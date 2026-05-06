# Lab 02.1 - Controlador de dominio y DNS

## Objetivo

Implementar un controlador de dominio funcional en Windows Server y validar la resolución de nombres interna del dominio `corp.luis.test`.

## Herramientas usadas

- Oracle VirtualBox
- Windows Server 2025 Standard Evaluation
- Active Directory Domain Services
- DNS Manager
- Windows PowerShell

## Actividades realizadas

1. Se instaló Windows Server como base del laboratorio.
2. Se configuró el nombre del servidor como `SRV-DC01`.
3. Se validó el contexto administrativo del equipo.
4. Se configuró la red del servidor con IP fija.
5. Se promovió el servidor como controlador de dominio del bosque.
6. Se creó el dominio `corp.luis.test`.
7. Se validó la zona DNS desde DNS Manager.
8. Se comprobó la resolución del dominio y del controlador de dominio desde PowerShell.

## Configuración aplicada

- **Servidor:** `SRV-DC01`
- **Dominio:** `corp.luis.test`
- **IP del servidor:** `192.168.56.10`
- **DNS principal:** `127.0.0.1` / `::1`
- **Rol principal:** Controlador de dominio y servidor DNS

## Comandos utilizados

- `hostname`
- `whoami`
- `ipconfig /all`
- `nslookup corp.luis.test`
- `nslookup srv-dc01.corp.luis.test`

## Validaciones realizadas

1. El servidor respondió correctamente con el nombre `SRV-DC01`.
2. La sesión administrativa se validó como `corp\administrator`.
3. La configuración IP mostró la dirección `192.168.56.10`.
4. El dominio `corp.luis.test` resolvió correctamente en DNS.
5. El registro `srv-dc01.corp.luis.test` resolvió correctamente hacia `192.168.56.10`.
6. La zona DNS quedó visible desde DNS Manager con sus registros correspondientes.

## Conceptos aprendidos

### Active Directory Domain Services
AD DS permite administrar identidades, usuarios, equipos, grupos y políticas dentro de un dominio.

### DNS en Active Directory
DNS es un componente crítico para Active Directory, porque los clientes dependen de la resolución de nombres para localizar el controlador de dominio y autenticarse.

### Controlador de dominio
Un Domain Controller centraliza la autenticación, la administración de objetos del dominio y la aplicación de políticas.

### Importancia de IP fija
Un controlador de dominio no debe trabajar con IP cambiante, porque eso puede afectar autenticación, resolución DNS y comunicación con los clientes.

## Resultado del laboratorio

Se implementó correctamente el controlador de dominio `SRV-DC01`, se creó el dominio `corp.luis.test` y se validó que la resolución DNS interna funcionara correctamente para el dominio y el propio servidor.

## Evidencias

- `lab02-01-hostname-srv-dc01.png`
- `lab02-02-whoami-corp-administrator.png`
- `lab02-03-ipconfig-srv-dc01.png`
- `lab02-04-dns-manager-corp-luis-test.png`
- `lab02-05-nslookup-corp-luis-test.png`
- `lab02-06-nslookup-srv-dc01-corp-luis-test.png`