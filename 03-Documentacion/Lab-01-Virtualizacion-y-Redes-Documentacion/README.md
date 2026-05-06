# Lab 01 - Virtualización y fundamentos de red

## Objetivo
Entender la base de virtualización en VirtualBox y diferenciar los tipos de red NAT, Adaptador puente y Host-only, además de identificar la red real y la red virtual desde Windows.

## Herramientas usadas
- VirtualBox
- Windows 11
- Símbolo del sistema (CMD)

## Actividades realizadas
1. Se creó una carpeta local para almacenar máquinas virtuales fuera de OneDrive.
2. Se configuró la carpeta predeterminada de VirtualBox para guardar VMs en una ruta local.
3. Se revisó la red Host-only de VirtualBox.
4. Se creó una máquina virtual de prueba llamada `VM-Prueba-Red`.
5. Se revisaron los modos de red:
   - NAT
   - Adaptador puente
   - Adaptador sólo anfitrión
6. Se ejecutaron comandos de red en Windows:
   - `hostname`
   - `ipconfig`
   - `ipconfig /all`
   - `ping 8.8.8.8`
   - `ping google.com`
   - `nslookup google.com`
7. Se revisaron los adaptadores de red desde `ncpa.cpl`.

## Conceptos aprendidos

### NAT
La máquina virtual usa la conexión de mi equipo real para salir a internet.

### Adaptador puente
La máquina virtual se comporta como otra computadora dentro de la misma red real.

### Host-only
Es una red privada entre mi equipo real y las máquinas virtuales.

## Datos identificados en mi equipo

### Red real
- Adaptador: Wi-Fi
- IP: 192.168.100.127
- Gateway: 192.168.100.1

### Red virtual
- Adaptador: VirtualBox Host-Only Ethernet Adapter
- IP: 192.168.56.1

## Diferencia entre ping por IP y por nombre
- `ping 8.8.8.8` valida conectividad por IP.
- `ping google.com` valida conectividad por nombre y también depende de DNS.

## Conclusión
En este laboratorio entendí cómo separar la red real de mi equipo y la red virtual del entorno de laboratorio. También aprendí a identificar IP, gateway, DNS y los modos de red más importantes de VirtualBox.

## Evidencias
Las capturas de este laboratorio se encuentran en la carpeta `Capturas`.
## Evidencias destacadas
- Configuración de carpeta local para VMs fuera de OneDrive.
- Identificación del adaptador Host-Only de VirtualBox.
- Creación de la máquina virtual `VM-Prueba-Red`.
- Comparación de modos de red: NAT, Adaptador puente y Host-only.
- Validación de red en Windows con `hostname`, `ipconfig`, `ipconfig /all`, `ping` y `nslookup`.
- Identificación de la red real Wi-Fi y la red virtual Host-Only.

## Lecciones aprendidas
- VirtualBox permite crear laboratorios sin afectar directamente el sistema operativo principal.
- NAT, Bridge y Host-only tienen usos distintos según el tipo de prueba o laboratorio.
- La red real y la red virtual deben identificarse correctamente para evitar confusiones.
- `ping` por IP y `ping` por nombre no validan exactamente lo mismo.
- `nslookup` ayuda a comprobar resolución DNS.
- La documentación técnica y las evidencias hacen que un laboratorio tenga valor para portafolio.
