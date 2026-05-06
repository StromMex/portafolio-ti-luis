# Lab 02.3 - AGDLP y recursos compartidos

## Objetivo

Implementar una estructura de permisos basada en el modelo **AGDLP** para administrar acceso a carpetas compartidas de forma ordenada, escalable y alineada a buenas prácticas de Active Directory.

## Herramientas usadas

- Windows Server 2025
- Active Directory Users and Computers
- Carpetas compartidas SMB
- Pestañas **Sharing** y **Security**
- Cliente Windows 11 unido al dominio
- PowerShell
- Explorador de archivos

## Actividades realizadas

1. Se revisó la estructura de grupos dentro de la OU `02-Groups`.
2. Se validó la existencia de grupos globales:
   - `GG-IT-Admins`
   - `GG-Soporte`
   - `GG-Usuarios`
3. Se validó la existencia de grupos de dominio local:
   - `DL-IT-Admins-FC`
   - `DL-Soporte-RW`
   - `DL-Usuarios-R`
4. Se confirmó la membresía de grupos bajo el modelo AGDLP:
   - `GG-IT-Admins` dentro de `DL-IT-Admins-FC`
   - `GG-Soporte` dentro de `DL-Soporte-RW`
   - `GG-Usuarios` dentro de `DL-Usuarios-R`
5. Se revisaron las carpetas compartidas creadas en el servidor:
   - `\\SRV-DC01\Soporte`
   - `\\SRV-DC01\Usuarios`
   - `\\SRV-DC01\IT-Admins`
6. Se validaron los permisos de recurso compartido:
   - **Soporte** con permisos de **Change / Read**
   - **Usuarios** con permisos de **Read**
   - **IT-Admins** con permisos de **Full Control**
7. Se validaron los permisos NTFS sobre las carpetas locales:
   - `C:\Shares\Soporte`
   - `C:\Shares\Usuarios`
   - `C:\Shares\IT-Admins`
8. Se realizaron pruebas desde el cliente para comprobar acceso permitido y acceso denegado según el grupo del usuario.
9. Se verificó que un usuario con permisos adecuados pudiera:
   - crear carpeta en **Soporte**
   - leer contenido en **Soporte**
   - crear archivo en **IT-Admins**
10. Se verificó que un usuario sin permisos suficientes no pudiera acceder al recurso **Usuarios**.

## Validaciones realizadas

### Estructura AGDLP

Se comprobó que la lógica aplicada fuera:

**Accounts → Global Groups → Domain Local Groups → Permissions**

Esto permite asignar permisos a recursos de manera centralizada, evitando dar permisos directos a usuarios individuales.

### Recursos compartidos

Se validó que cada carpeta tuviera su ruta compartida correctamente publicada:

- `\\SRV-DC01\Soporte`
- `\\SRV-DC01\Usuarios`
- `\\SRV-DC01\IT-Admins`

### Permisos por recurso

- **Soporte**: lectura y escritura
- **Usuarios**: solo lectura
- **IT-Admins**: control total

### Pruebas funcionales en cliente

Se comprobó en el cliente que:

- el acceso a **Usuarios** fuera denegado cuando el usuario no tenía permisos suficientes
- el acceso a **Soporte** permitiera crear carpetas y leer archivos
- el acceso a **IT-Admins** permitiera crear archivos cuando el usuario pertenecía al grupo correspondiente

## Conceptos aprendidos

### AGDLP

El modelo **AGDLP** ayuda a organizar permisos en Active Directory de una forma más limpia y administrable:

- **A** = Accounts
- **G** = Global Groups
- **DL** = Domain Local Groups
- **P** = Permissions

### Diferencia entre Share Permissions y NTFS

Los permisos de recurso compartido controlan el acceso por red al recurso SMB.  
Los permisos **NTFS** controlan lo que realmente se puede hacer dentro de la carpeta a nivel del sistema de archivos.

Para que un acceso funcione correctamente, ambos tipos de permisos deben estar alineados.

### Administración escalable

Usar grupos en vez de permisos directos a usuarios facilita:

- altas y bajas de personal
- cambios de puesto
- auditoría de acceso
- administración más ordenada del entorno

## Resultado del laboratorio

Se implementó correctamente una estructura de acceso basada en **AGDLP** para recursos compartidos en el servidor.  
Se validó que los grupos globales alimentaran a los grupos de dominio local y que los permisos aplicados sobre los recursos coincidieran con el nivel de acceso esperado.

Las pruebas desde el cliente confirmaron tanto escenarios de acceso permitido como escenarios de acceso denegado, demostrando que la configuración de grupos, shares y permisos NTFS quedó funcional.

## Evidencias

- `lab02-01-groups-list`
- `lab02-02-dl-it-admins-membership`
- `lab02-03-dl-soporte-membership`
- `lab02-04-dl-usuarios-membership`
- `lab02-05-share-soporte-path`
- `lab02-06-share-usuarios-path`
- `lab02-07-share-it-admins-path`
- `lab02-08-share-permissions-soporte`
- `lab02-09-share-permissions-usuarios`
- `lab02-10-share-permissions-it-admins`
- `lab02-11-ntfs-soporte`
- `lab02-12-ntfs-usuarios`
- `lab02-13-ntfs-it-admins`
- `lab02-14-client-file-created-it-admins`
- `lab02-15-client-access-denied-usuarios`
- `lab02-16-client-folder-created-soporte`
- `lab02-17-client-read-soporte-file`
- `lab02-18-client-create-file-soporte`