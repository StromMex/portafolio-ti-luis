# Lab 02.4 - Drive Maps por GPO

## Objetivo

Configurar unidades de red mapeadas mediante **Group Policy Preferences (Drive Maps)** para que los usuarios reciban automáticamente el recurso compartido correspondiente según su pertenencia a grupos de seguridad.

## Herramientas usadas

- Windows Server 2025
- Group Policy Management
- Group Policy Management Editor
- Active Directory
- Group Policy Preferences
- Item-level targeting
- Recursos compartidos SMB
- Cliente Windows 11 unido al dominio
- PowerShell
- Explorador de archivos

## Actividades realizadas

1. Se creó y configuró una GPO orientada al mapeo automático de unidades de red.
2. Dentro de la GPO se agregaron elementos en:
   - `User Configuration`
   - `Preferences`
   - `Windows Settings`
   - `Drive Maps`
3. Se configuró la unidad **S:** para el recurso `\\SRV-DC01\Soporte`.
4. Se configuró la unidad **U:** para el recurso `\\SRV-DC01\Usuarios`.
5. Se configuró la unidad **I:** para el recurso `\\SRV-DC01\IT-Admins`.
6. En cada unidad se aplicó **Item-level targeting** basado en grupos de seguridad:
   - `CORP\GG-Soporte`
   - `CORP\GG-Usuarios`
   - `CORP\GG-IT-Admins`
7. Se actualizó la política en el cliente con `gpupdate /force`.
8. Se validó en **This PC** la aparición de las unidades mapeadas según la pertenencia del usuario.
9. Se comprobó que el acceso entregado coincidiera con el recurso esperado para cada grupo.

## Validaciones realizadas

### Configuración de Drive Maps

Se comprobó que cada unidad quedara correctamente configurada con la acción **Update**, una ruta UNC válida y una letra de unidad asignada:

- **S:** → `\\SRV-DC01\Soporte`
- **U:** → `\\SRV-DC01\Usuarios`
- **I:** → `\\SRV-DC01\IT-Admins`

### Targeting por grupo

Se validó que cada unidad no se aplicara a todos los usuarios, sino únicamente a quienes pertenecieran al grupo correspondiente.

Esto se configuró mediante **Item-level targeting**, usando la condición:

- *the user is a member of the security group...*

### Aplicación de políticas

Se ejecutó `gpupdate /force` en el cliente para forzar la actualización de directivas y comprobar la entrega inmediata de los mapeos.

### Verificación visual en cliente

Se revisó en **This PC** que las unidades aparecieran como **Network locations**, confirmando que la GPO se aplicó correctamente.

## Conceptos aprendidos

### Drive Maps

Los **Drive Maps** permiten publicar recursos compartidos como letras de unidad visibles para el usuario, facilitando el acceso a carpetas de red sin necesidad de escribir manualmente rutas UNC.

### Group Policy Preferences

Las **Preferences** dentro de una GPO permiten automatizar configuraciones prácticas del entorno, como:

- unidades mapeadas
- accesos directos
- variables de entorno
- archivos y carpetas

### Item-level targeting

El **targeting** permite aplicar configuraciones solo cuando se cumple una condición específica.

En este laboratorio se utilizó la pertenencia a grupos de seguridad, lo que vuelve el mapeo más dinámico y administrable.

### Relación con AGDLP

El mapeo automático funciona mejor cuando los permisos ya fueron diseñados con grupos.

Así, la GPO entrega la unidad y los permisos sobre el recurso determinan qué puede hacer realmente el usuario.

## Resultado del laboratorio

Se implementó correctamente el mapeo automático de unidades de red mediante GPO.

Cada recurso compartido quedó asociado a una letra específica y a un grupo de seguridad determinado.

La validación en el cliente confirmó que las políticas se aplicaron correctamente y que las unidades se mostraron en el explorador según el contexto del usuario.

## Evidencias

- `lab02-01-drive-map-soporte-targeting`
- `lab02-02-drive-map-soporte-properties`
- `lab02-03-drive-map-usuarios-targeting`
- `lab02-04-drive-map-usuarios-properties`
- `lab02-05-drive-map-it-admins-targeting`
- `lab02-06-drive-map-it-admins-properties`
- `lab02-07-drive-maps-list`
- `lab02-08-gpupdate-force-client`
- `lab02-09-client-drive-i-it-admins`
- `lab02-10-client-drive-s-soporte`
- `lab02-11-client-drive-u-usuarios`