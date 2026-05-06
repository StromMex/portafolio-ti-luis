# Lab 02.2 - Unión al dominio y validación de GPO

## Objetivo

Integrar un equipo Windows 11 al dominio `corp.luis.test`, validar conectividad contra el controlador de dominio y comprobar la aplicación de políticas de grupo sobre el cliente.

## Herramientas usadas

- Oracle VirtualBox
- Windows 11 Enterprise Evaluation
- Active Directory Users and Computers
- Group Policy Management
- Windows PowerShell

## Actividades realizadas

1. Se instaló Windows 11 Enterprise Evaluation en una máquina virtual cliente.
2. Se configuró el nombre del equipo como `CLT-W11-01`.
3. Se validó la conectividad de red hacia el controlador de dominio.
4. Se comprobó la resolución DNS del dominio y del servidor.
5. Se unió el cliente al dominio `corp.luis.test`.
6. Se reinició el equipo para completar la unión al dominio.
7. Se validó la aparición del equipo dentro de Active Directory.
8. Se aplicaron políticas de grupo sobre la estación de trabajo.
9. Se forzó la actualización de directivas con `gpupdate /force`.
10. Se probaron restricciones aplicadas al usuario en el cliente.

## Configuración aplicada

- **Cliente:** `CLT-W11-01`
- **Dominio:** `corp.luis.test`
- **IP del cliente:** `192.168.56.20`
- **DNS configurado:** `192.168.56.10`
- **OU objetivo:** `04-Workstations`

## Comandos utilizados

- `hostname`
- `ipconfig /all`
- `ping 192.168.56.10`
- `nslookup corp.luis.test`
- `nslookup srv-dc01.corp.luis.test`
- `gpupdate /force`

## Validaciones realizadas

1. El cliente respondió correctamente con el nombre `CLT-W11-01`.
2. La configuración IP mostró la dirección `192.168.56.20`.
3. El cliente tuvo conectividad correcta con `SRV-DC01`.
4. El dominio `corp.luis.test` resolvió correctamente.
5. El nombre `srv-dc01.corp.luis.test` resolvió hacia `192.168.56.10`.
6. El mensaje de bienvenida al dominio confirmó la unión satisfactoria.
7. El equipo apareció dentro de Active Directory en la OU correspondiente.
8. `gpupdate /force` ejecutó correctamente la actualización de políticas.
9. Las restricciones configuradas por GPO se reflejaron en el cliente.

## Conceptos aprendidos

### Unión al dominio
Unir un equipo al dominio permite que sea administrado centralmente, reciba políticas y autentique usuarios del entorno corporativo.

### Dependencia de DNS
Antes de unir un equipo al dominio, el cliente debe poder resolver correctamente el dominio y el controlador de dominio usando DNS interno.

### Group Policy
Las GPO permiten aplicar configuraciones y restricciones de manera centralizada sobre usuarios y equipos, evitando configuraciones manuales individuales.

### Validación posterior a la unión
No basta con unir el equipo al dominio; también es necesario validar que aparezca en AD, que resuelva correctamente y que reciba políticas.

## Resultado del laboratorio

El equipo `CLT-W11-01` fue unido correctamente al dominio `corp.luis.test`, logró comunicarse con el controlador de dominio y recibió políticas de grupo aplicadas desde el entorno centralizado.

## Evidencias

- `lab02-01-win11-installation-progress`
- `lab02-02-win11-disk-selection`
- `lab02-03-client-desktop-ready`
- `lab02-04-hostname-and-ping-client`
- `lab02-05-client-ping-and-nslookup`
- `lab02-06-pre-domain-join-window`
- `lab02-07-domain-join-success`
- `lab02-08-clt-w11-01-in-aduc`
- `lab02-09-gpupdate-force-client`
- `lab02-10-restriction-message`
- `lab02-11-ipconfig-client`