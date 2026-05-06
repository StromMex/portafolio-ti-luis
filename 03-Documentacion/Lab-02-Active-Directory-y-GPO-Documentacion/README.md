# Lab-02-Active-Directory-y-GPO

## Descripción general

Este laboratorio integra la construcción y validación de un entorno Windows Server con Active Directory, DNS, Group Policy, modelo de permisos AGDLP, recursos compartidos y mapeo de unidades por GPO.

El objetivo fue simular tareas reales de administración de identidad, acceso y seguridad dentro de un dominio corporativo, documentando cada bloque técnico con evidencias y resultados verificables.

## Estructura del laboratorio

Este laboratorio se documentó en los siguientes archivos:

- `00-Introduccion.md`
- `01-DC-y-DNS.md`
- `02-Domain-Join-y-GPO.md`
- `03-AGDLP-y-Shares.md`
- `04-Drive-Maps.md`
- `05-Password-y-Lockout.md`

## Módulos trabajados

### 1. DC y DNS
Se validó la configuración base del controlador de dominio y la resolución DNS interna del entorno.

### 2. Unión al dominio y validación de GPO
Se integró un cliente Windows 11 al dominio y se verificó la aplicación de políticas de grupo.

### 3. AGDLP y recursos compartidos
Se implementó una estructura de permisos basada en grupos para controlar acceso a carpetas compartidas.

### 4. Drive Maps por GPO
Se automatizó la entrega de unidades de red según pertenencia a grupos de seguridad.

### 5. Políticas de contraseña y bloqueo de cuentas
Se configuraron políticas de seguridad a nivel dominio y se validó el bloqueo y desbloqueo de cuentas.

## Tecnologías y herramientas utilizadas

- Oracle VirtualBox
- Windows Server 2025
- Windows 11 Enterprise Evaluation
- Active Directory Domain Services
- DNS
- Group Policy Management
- Active Directory Users and Computers
- SMB / Shared Folders
- PowerShell

## Habilidades practicadas

- Configuración de controlador de dominio
- Resolución DNS interna
- Unión de equipos al dominio
- Aplicación y validación de GPO
- Diseño de permisos con AGDLP
- Publicación de recursos compartidos
- Mapeo de unidades por GPO
- Administración de políticas de contraseña
- Bloqueo y desbloqueo de cuentas con PowerShell
- Documentación técnica con evidencias

## Resultado general

Se construyó y validó un laboratorio funcional de Active Directory orientado a escenarios reales de administración de usuarios, equipos, permisos y seguridad.

Cada módulo fue probado con evidencias visuales y validaciones técnicas, permitiendo demostrar no solo la configuración, sino también el comportamiento esperado del entorno.

## Evidencias

Las evidencias de cada bloque se encuentran organizadas en la carpeta:

- `Capturas/01-DC-y-DNS`
- `Capturas/02-Domain-Join-y-GPO`
- `Capturas/03-AGDLP-y-Shares`
- `Capturas/04-Drive-Maps`
- `Capturas/05-Password-y-Lockout`

## Conclusión

Este laboratorio permitió consolidar una base práctica en administración de entornos Windows empresariales, integrando identidad, acceso, automatización y seguridad en un mismo escenario.