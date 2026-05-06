# Introducción

## Resumen del proyecto

Este laboratorio fue desarrollado para practicar la implementación de un entorno Microsoft basado en Active Directory, con enfoque en administración de usuarios, equipos, políticas de grupo, acceso a recursos compartidos y seguridad de cuentas.

El objetivo no fue únicamente instalar servicios, sino comprender cómo se relacionan entre sí dentro de un dominio corporativo, cómo validarlos técnicamente y cómo resolver fallas comunes durante la implementación.

A lo largo del laboratorio se configuró un controlador de dominio en Windows Server, se integró un cliente Windows 11 al dominio, se aplicaron GPOs, se implementó un modelo de permisos con AGDLP, se automatizó el acceso a recursos compartidos mediante Drive Maps y se validaron políticas de seguridad como complejidad de contraseña y bloqueo de cuentas.

## Objetivo general

Implementar y validar un laboratorio funcional de Active Directory con servicios base de identidad, resolución de nombres, configuración centralizada y control de acceso, siguiendo una lógica cercana a un entorno empresarial.

## Objetivos específicos

- Instalar y configurar Windows Server como controlador de dominio.
- Implementar DNS interno para la resolución del dominio.
- Crear una estructura organizada de OUs, usuarios y grupos.
- Integrar un cliente Windows 11 al dominio.
- Aplicar restricciones y configuraciones mediante GPO.
- Diseñar permisos usando el modelo AGDLP.
- Configurar recursos compartidos y validar acceso por usuario.
- Mapear unidades de red por GPO según grupo de pertenencia.
- Aplicar políticas de contraseña y bloqueo de cuentas a nivel dominio.

## Alcance del laboratorio

El laboratorio cubre un flujo completo de administración base en un entorno Windows empresarial:

1. Configuración de DC y DNS.
2. Unión de cliente al dominio.
3. Validación de aplicación de GPO.
4. Implementación de permisos con grupos.
5. Publicación de carpetas compartidas.
6. Mapeo automático de unidades.
7. Configuración de políticas de seguridad de cuentas.

## Estructura documental

La documentación del laboratorio se dividió en los siguientes bloques:

- `01-DC-y-DNS.md`
- `02-Domain-Join-y-GPO.md`
- `03-AGDLP-y-Shares.md`
- `04-Drive-Maps.md`
- `05-Password-y-Lockout.md`

## Resultado esperado

Contar con un entorno funcional donde un usuario del dominio pueda autenticarse, recibir políticas, acceder únicamente a los recursos que le correspondan por grupo y quedar sujeto a reglas de seguridad definidas centralmente.