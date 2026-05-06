# Lab 02.5 - Políticas de contraseña y bloqueo de cuentas

## Objetivo

Configurar y validar políticas de seguridad de cuentas a nivel dominio en Active Directory, incluyendo complejidad de contraseña, longitud mínima, historial de contraseñas y bloqueo temporal por intentos fallidos de inicio de sesión.

## Herramientas usadas

- Windows Server 2025
- Active Directory
- Group Policy Management
- Group Policy Management Editor
- Default Domain Policy
- PowerShell
- Cliente Windows 11 unido al dominio
- Active Directory Users and Computers

## Actividades realizadas

1. Se revisó la política de dominio predeterminada aplicada a la seguridad de cuentas.
2. Se configuraron los parámetros de **Password Policy** dentro de:
   - `Computer Configuration`
   - `Policies`
   - `Windows Settings`
   - `Security Settings`
   - `Account Policies`
   - `Password Policy`
3. Se definió el historial de contraseñas en **5 passwords remembered**.
4. Se configuró la expiración máxima de contraseña en **30 días**.
5. Se configuró la antigüedad mínima de contraseña en **1 día**.
6. Se estableció una longitud mínima de contraseña de **10 caracteres**.
7. Se habilitó el requisito de complejidad de contraseña.
8. Se dejó deshabilitado el almacenamiento de contraseñas con cifrado reversible.
9. Se configuraron los parámetros de **Account Lockout Policy**:
   - bloqueo después de **3 intentos fallidos**
   - duración del bloqueo de **15 minutos**
   - reinicio del contador después de **15 minutos**
10. Se forzó la actualización de políticas con `gpupdate /force`.
11. Se validó la política efectiva con `Get-ADDefaultDomainPasswordPolicy`.
12. Se probó el cambio de contraseña con una contraseña no válida y luego con una válida.
13. Se provocó el bloqueo de una cuenta por intentos fallidos.
14. Se verificó el estado de bloqueo con `Get-ADUser`.
15. Se desbloqueó manualmente la cuenta con `Unlock-ADAccount`.
16. Se confirmó que la cuenta quedó nuevamente habilitada para autenticación.

## Validaciones realizadas

### Validación de Password Policy

Se comprobó que la política de contraseñas quedara configurada con los siguientes parámetros efectivos:

- **ComplexityEnabled:** `True`
- **MinPasswordLength:** `10`
- **PasswordHistoryCount:** `5`
- **MaxPasswordAge:** `30 días`
- **MinPasswordAge:** `1 día`
- **ReversibleEncryptionEnabled:** `False`

### Validación de Account Lockout Policy

Se comprobó que la política de bloqueo de cuenta quedara configurada con estos valores:

- **LockoutThreshold:** `3`
- **LockoutDuration:** `15 minutos`
- **LockoutObservationWindow:** `15 minutos`

### Validación funcional de contraseña

Se realizó una prueba de cambio de contraseña con un valor que no cumplía la política, obteniendo un mensaje de error por complejidad o longitud.

Después se realizó una segunda prueba con una contraseña válida y el cambio se completó correctamente.

### Validación funcional de bloqueo

Se provocó el bloqueo de la cuenta mediante intentos fallidos de autenticación en el cliente.

Posteriormente se verificó en PowerShell que el atributo **LockedOut** estuviera en `True`.

### Validación de desbloqueo administrativo

Se ejecutó `Unlock-ADAccount` sobre el usuario de prueba y después se confirmó que **LockedOut** cambiara a `False`.

## Conceptos aprendidos

### Password Policy

La **Password Policy** define los requisitos mínimos que deben cumplir las contraseñas en el dominio, ayudando a reducir el uso de credenciales débiles o repetidas.

### Complejidad de contraseña

La complejidad obliga a que las contraseñas combinen distintos tipos de caracteres y evita patrones simples o predecibles.

### Historial de contraseñas

El historial impide reutilizar inmediatamente contraseñas anteriores, fortaleciendo la rotación de credenciales.

### Account Lockout Policy

La política de bloqueo protege las cuentas contra ataques de fuerza bruta al deshabilitar temporalmente el inicio de sesión después de varios intentos fallidos.

### Validación con PowerShell

PowerShell permitió comprobar de forma objetiva la política efectiva del dominio y el estado real de la cuenta bloqueada.

## Resultado del laboratorio

Se implementaron correctamente políticas de contraseña y bloqueo de cuentas a nivel dominio.

Las validaciones demostraron que el dominio ya exige contraseñas más seguras, bloquea temporalmente cuentas tras varios intentos fallidos y permite al administrador verificar y revertir el bloqueo de manera controlada.

## Evidencias

- `lab02-01-password-policy-history`
- `lab02-02-password-policy-max-age`
- `lab02-03-password-policy-min-age`
- `lab02-04-password-policy-min-length`
- `lab02-05-password-policy-complexity`
- `lab02-06-password-policy-reversible-encryption`
- `lab02-07-password-policy-summary`
- `lab02-08-lockout-threshold`
- `lab02-09-lockout-duration`
- `lab02-10-lockout-reset-counter`
- `lab02-11-lockout-policy-summary`
- `lab02-12-gpupdate-force-domain-policy`
- `lab02-13-get-addefaultdomainpasswordpolicy`
- `lab02-14-password-change-failed-policy`
- `lab02-15-password-change-success`
- `lab02-16-client-account-locked-out`
- `lab02-17-get-aduser-lockedout-true`
- `lab02-18-unlock-adaccount-lockedout-false`