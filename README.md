# Seguridad de Redes — Comercial El Triunfo S.A. de C.V.

## Contexto general

Proyecto universitario de la asignatura **Seguridad de Redes — SDR901 G01T** de la **Universidad Don Bosco**.

El caso corresponde a la empresa ficticia **Comercial El Triunfo S.A. de C.V.**

El proyecto se desarrolló en tres fases:

1. Descubrimiento
2. Diseño
3. Construcción / Implementación

La fase actual es la **Actividad 3 — Construcción**, que necesita corregirse porque la implementación anterior fue guiada de forma incompleta y no cumplió correctamente con todos los requisitos de la actividad.

---

# Caso de la empresa

La empresa posee aproximadamente 100 usuarios distribuidos así:

- Dirección General: 3
- Recursos Humanos: 5
- Contabilidad: 8
- Compras: 10
- Ventas: 35
- Bodega: 20
- Informática: 4
- Atención al Cliente: 15

La infraestructura original incluía:

- 1 Windows Server
- 1 Ubuntu/Linux Server
- red LAN
- router empresarial
- switch principal
- base de datos
- sitio web institucional
- acceso a Internet

Problemas identificados originalmente:

- ausencia de Active Directory;
- administración descentralizada de usuarios;
- permisos administrados manualmente;
- sitio web únicamente mediante HTTP;
- ausencia de infraestructura de certificados;
- configuraciones potencialmente inseguras;
- falta de documentación técnica;
- ausencia de revisiones periódicas de seguridad.

---

# Actividad 1 — Descubrimiento

Esta actividad ya fue terminada.

Se trabajó:

- identificación de activos;
- descripción de infraestructura;
- diagnóstico;
- vulnerabilidades;
- amenazas;
- impacto;
- confidencialidad, integridad y disponibilidad;
- priorización de riesgos;
- recomendaciones;
- diagramas;
- conclusiones.

Documento previo:

```text
SDR - Actividad 1 Descubrimiento - QR230082.pdf
```

No es la prioridad actual.

---

# Actividad 2 — Diseño

También está terminada.

La arquitectura diseñada utilizó únicamente dos servidores.

## Windows Server

Planeado para:

- Active Directory Domain Services
- DNS
- administración centralizada
- OU
- grupos de seguridad
- permisos
- infraestructura de certificados como parte del diseño

## Ubuntu Server

Planeado para:

- Apache
- sitio web institucional
- preparación para HTTPS

Dominio diseñado:

```text
corp.eltriunfo.test
```

Servidor Windows:

```text
SRV-DC01
```

Servidor Ubuntu:

```text
SRV-WEB01
```

Documento previo:

```text
SDR - Actividad 2 Diseño - QR230082.pdf
```

---

# Actividad 3 — Construcción

La actividad exige implementar la solución utilizando únicamente:

- una máquina virtual Windows Server;
- una máquina virtual Ubuntu Server.

## Windows Server debe incluir

- Active Directory Domain Services;
- DNS;
- dominio corporativo;
- OU correspondientes a las áreas de la empresa;
- 3 usuarios por OU;
- grupos de seguridad;
- permisos según la estructura propuesta.

## Ubuntu debe incluir

- Apache;
- sitio web institucional representativo;
- acceso mediante HTTP desde Windows Server.

## La defensa debe permitir demostrar

- funcionamiento de ambos servidores;
- comunicación entre las máquinas;
- resolución DNS;
- acceso HTTP;
- estructura completa de Active Directory;
- OU;
- usuarios;
- grupos;
- servicios operativos.

## Requisito crítico

La actividad requiere **Windows Server en entorno gráfico**.

La implementación final debe utilizar:

```text
Windows Server con Desktop Experience
```

No utilizar Windows Server Core para la entrega final.

---

# ERRORES DE LA ASISTENCIA ANTERIOR

Esta sección debe leerse antes de continuar el proyecto porque documenta decisiones incorrectas que no deben repetirse.

## Error 1 — Se recomendó Windows Server Core

La asistencia anterior recomendó utilizar **Windows Server Core** para ahorrar memoria RAM y reducir consumo de recursos.

Eso fue un error.

Aunque Server Core técnicamente permite ejecutar:

- AD DS;
- DNS;
- usuarios;
- OU;
- grupos;
- recursos compartidos;

la actividad requería **entorno gráfico**.

Durante la defensa se observó que otros estudiantes utilizaban:

- Server Manager;
- Active Directory Users and Computers;
- DNS Manager;
- árbol visual del dominio;
- OU gráficas;
- usuarios y grupos visibles;
- navegador web.

La implementación Core era funcional técnicamente, pero **no cumplía correctamente con la forma requerida de implementación y defensa**.

### Regla

No volver a recomendar:

```text
Windows Server Core
```

La corrección debe hacerse con:

```text
Windows Server Desktop Experience
```

---

## Error 2 — Se priorizó ahorro de recursos sobre la consigna

La asistencia priorizó:

- bajo consumo de RAM;
- PowerShell;
- CLI;
- reutilización de una VM Core;
- implementación mínima;

cuando debía priorizar:

```text
REQUISITO LITERAL
+
FUNCIONALIDAD
+
ENTORNO GRÁFICO
+
EVIDENCIA VISUAL
+
DEFENSA
```

El usuario había advertido explícitamente que se trataba de una actividad evaluada y que necesitaba evitar errores similares ocurridos anteriormente en otra asignatura de Servidores.

Esto no se tomó suficientemente en cuenta.

---

## Error 3 — No se detectó a tiempo el requisito gráfico

La asistencia tuvo acceso a las instrucciones de la actividad y aun así permitió continuar con Server Core.

Debió detener la implementación y señalar:

```text
La actividad requiere entorno gráfico.
Server Core no debe utilizarse.
```

No lo hizo.

Como consecuencia se invirtió tiempo en configurar una VM que después resultó inadecuada para la defensa.

---

## Error 4 — Se intentó justificar Server Core después

Cuando apareció el problema, la asistencia intentó defender la implementación argumentando que:

- Server Core sigue siendo Windows Server;
- AD DS funcionaba;
- DNS funcionaba;
- PowerShell podía demostrar la estructura.

Eso no resolvía el problema.

Si la consigna exige entorno gráfico, que una implementación sea técnicamente válida no significa que cumpla la actividad.

### Regla

Cuando exista conflicto entre:

```text
"técnicamente posible"
```

y:

```text
"requisito literal de la actividad"
```

seguir el requisito literal.

---

## Error 5 — Se confundió funcionamiento con evidencia adecuada

La infraestructura se validó con comandos como:

```powershell
Get-ADOrganizationalUnit
Get-ADUser
Get-ADGroup
Resolve-DnsName
Invoke-WebRequest
```

Estos comandos son útiles.

Pero no sustituyen las herramientas gráficas cuando el docente espera ver:

- Active Directory Users and Computers;
- DNS Manager;
- Server Manager;
- navegador;
- estructura visual del dominio.

La versión corregida debe ofrecer:

- funcionamiento real;
- validación por comandos cuando sea útil;
- evidencia gráfica.

---

## Error 6 — Se repitió un patrón similar al de otra materia

El usuario ya había tenido problemas anteriormente en una asignatura de Servidores debido a implementaciones incompletas.

Había advertido explícitamente que no quería volver a pasar por eso.

La asistencia debía haber sido particularmente cuidadosa en:

- leer literalmente la consigna;
- confirmar requisitos;
- pensar en la defensa;
- no asumir que una solución mínima bastaba.

No lo hizo.

---

## Error 7 — Se complicó innecesariamente el traslado a Codex

Al intentar mover este proyecto a Codex Cloud, la asistencia dio varias indicaciones incorrectas o innecesarias:

- asumir que el usuario utilizaba una app de escritorio;
- recomendar abrir una carpeta local;
- insistir con `Choose remote`;
- enviar al usuario repetidamente a Settings;
- no comprender inicialmente que el usuario no podía enviar nada desde la pantalla Remote;
- sugerir flujos de Remote que no correspondían;
- sugerir repositorios sin explicar inmediatamente que las máquinas virtuales de VirtualBox no pueden trasladarse de esa forma.

### Situación real

El usuario:

- utiliza navegador;
- no quiere instalar la app de escritorio;
- está configurando Codex Cloud;
- utilizará GitHub únicamente como workspace/contexto;
- mantendrá las VMs localmente en VirtualBox.

Codex Cloud no debe asumir acceso directo a las máquinas virtuales.

---

# Infraestructura actual

A pesar del problema con Server Core, se consiguió una infraestructura funcional que debe utilizarse como referencia para reconstruir correctamente la versión gráfica.

---

# Red VirtualBox

Nombre de la NAT Network:

```text
ELTRIUNFO
```

Red:

```text
10.10.10.0/24
```

Gateway:

```text
10.10.10.1
```

---

# Windows Server actual

La implementación anterior utiliza Server Core.

Hostname:

```text
SRV-DC01
```

IP:

```text
10.10.10.10/24
```

Gateway:

```text
10.10.10.1
```

DNS:

```text
10.10.10.10
```

Dominio:

```text
corp.eltriunfo.test
```

NetBIOS:

```text
ELTRIUNFO
```

Actualmente funcionaban:

- AD DS;
- DNS;
- dominio;
- OU;
- usuarios;
- grupos;
- permisos;
- recurso compartido;
- resolución DNS hacia Ubuntu;
- comunicación con Ubuntu.

Esta VM debe mantenerse como respaldo mientras se construye la versión gráfica.

---

# Ubuntu Server

Hostname:

```text
SRV-WEB01
```

IP utilizada durante las pruebas:

```text
10.10.10.3/24
```

Gateway:

```text
10.10.10.1
```

Sistema utilizado:

```text
Ubuntu Server 16.04.7 LTS
```

Usuario administrativo recuperado:

```text
gabrieladmin
```

Apache:

```text
Apache/2.4.18
```

Estado comprobado:

```text
active (running)
```

Sitio:

```text
/var/www/html/index.html
```

Contenido mínimo utilizado inicialmente:

```text
Comercial El Triunfo S.A. de C.V.
```

Se comprobó localmente:

```bash
wget http://localhost
```

Respuesta:

```text
200 OK
```

---

# Comunicación entre máquinas

Windows hacia Ubuntu:

```powershell
ping 10.10.10.3
```

Funcionó.

Ubuntu hacia Windows:

```bash
ping -c 4 10.10.10.10
```

Funcionó.

---

# Estructura de Active Directory

Dominio:

```text
corp.eltriunfo.test
```

Estructura:

```text
corp.eltriunfo.test
├── OU=Usuarios
│   ├── DireccionGeneral
│   ├── RecursosHumanos
│   ├── Contabilidad
│   ├── Compras
│   ├── Ventas
│   ├── Bodega
│   ├── Informatica
│   └── AtencionCliente
├── OU=Equipos
├── OU=Servidores
└── OU=Grupos
```

---

# Usuarios

Se crearon tres usuarios por OU departamental.

Total:

```text
24 usuarios
```

Convención utilizada:

```text
dg.usuario1
dg.usuario2
dg.usuario3

rrhh.usuario1
rrhh.usuario2
rrhh.usuario3

cont.usuario1
cont.usuario2
cont.usuario3

comp.usuario1
comp.usuario2
comp.usuario3

vent.usuario1
vent.usuario2
vent.usuario3

bod.usuario1
bod.usuario2
bod.usuario3

info.usuario1
info.usuario2
info.usuario3

atc.usuario1
atc.usuario2
atc.usuario3
```

---

# Grupos de seguridad

Grupos globales:

```text
GG_DG_USUARIOS
GG_RRHH_USUARIOS
GG_CONT_USUARIOS
GG_COMP_USUARIOS
GG_VENT_USUARIOS
GG_BOD_USUARIOS
GG_INFO_USUARIOS
GG_ATC_USUARIOS
```

Grupo Domain Local utilizado como ejemplo:

```text
DL_CONTABILIDAD_RW
```

Modelo de permisos:

```text
Usuario
   ↓
Grupo global departamental
   ↓
Grupo Domain Local
   ↓
Permiso sobre recurso
```

Ejemplo:

```text
Usuarios de Contabilidad
        ↓
GG_CONT_USUARIOS
        ↓
DL_CONTABILIDAD_RW
        ↓
Recurso Contabilidad
```

---

# Recurso compartido

Ruta:

```text
C:\Recursos\Contabilidad
```

Share:

```text
Contabilidad
```

Permisos utilizados:

```text
ELTRIUNFO\Domain Admins
→ Full Access

ELTRIUNFO\DL_CONTABILIDAD_RW
→ Change Access
```

Comando utilizado:

```powershell
New-SmbShare `
-Name "Contabilidad" `
-Path "C:\Recursos\Contabilidad" `
-FullAccess "ELTRIUNFO\Domain Admins" `
-ChangeAccess "ELTRIUNFO\DL_CONTABILIDAD_RW"
```

Relación:

```powershell
Add-ADGroupMember `
-Identity "DL_CONTABILIDAD_RW" `
-Members "GG_CONT_USUARIOS"
```

---

# DNS

Zona:

```text
corp.eltriunfo.test
```

Registro A:

```text
www
```

Resolución deseada:

```text
www.corp.eltriunfo.test
→
10.10.10.3
```

La IP `10.10.10.3` pertenece al servidor Ubuntu que ejecuta Apache.

Comando utilizado:

```powershell
Add-DnsServerResourceRecordA `
-Name "www" `
-ZoneName "corp.eltriunfo.test" `
-IPv4Address "10.10.10.3"
```

Validación:

```powershell
Resolve-DnsName www.corp.eltriunfo.test
```

Resultado obtenido:

```text
www.corp.eltriunfo.test
A
10.10.10.3
```

---

# Zona inversa

Para:

```text
10.10.10.0/24
```

la zona inversa sería:

```text
10.10.10.in-addr.arpa
```

Comando propuesto:

```powershell
Add-DnsServerPrimaryZone `
-NetworkId "10.10.10.0/24" `
-ReplicationScope "Domain"
```

PTR Ubuntu:

```powershell
Add-DnsServerResourceRecordPtr `
-Name "3" `
-ZoneName "10.10.10.in-addr.arpa" `
-PtrDomainName "www.corp.eltriunfo.test"
```

PTR Windows:

```powershell
Add-DnsServerResourceRecordPtr `
-Name "10" `
-ZoneName "10.10.10.in-addr.arpa" `
-PtrDomainName "SRV-DC01.corp.eltriunfo.test"
```

IMPORTANTE:

No asumir que la zona inversa quedó finalmente implementada.

Debe verificarse.

---

# Validación HTTP

Desde Windows se utilizó:

```powershell
Invoke-WebRequest http://www.corp.eltriunfo.test -UseBasicParsing
```

Resultado obtenido:

```text
StatusCode        : 200
StatusDescription : OK
Content           : Comercial El Triunfo S.A. de C.V.
```

Esto validó:

```text
Windows
   ↓
DNS
   ↓
www.corp.eltriunfo.test
   ↓
10.10.10.3
   ↓
Ubuntu
   ↓
Apache
   ↓
HTTP 200
```

La nueva implementación debe además demostrar esto mediante navegador gráfico.

---

# Script anterior para crear OU, usuarios y grupos

```powershell
Import-Module ActiveDirectory

$baseDN = "DC=corp,DC=eltriunfo,DC=test"

New-ADOrganizationalUnit -Name "Usuarios" -Path $baseDN -ProtectedFromAccidentalDeletion $false
New-ADOrganizationalUnit -Name "Equipos" -Path $baseDN -ProtectedFromAccidentalDeletion $false
New-ADOrganizationalUnit -Name "Servidores" -Path $baseDN -ProtectedFromAccidentalDeletion $false
New-ADOrganizationalUnit -Name "Grupos" -Path $baseDN -ProtectedFromAccidentalDeletion $false

$usuariosOU = "OU=Usuarios,$baseDN"
$gruposOU = "OU=Grupos,$baseDN"

$areas = @(
 @{OU="DireccionGeneral"; Grupo="GG_DG_USUARIOS"; Prefijo="dg"},
 @{OU="RecursosHumanos"; Grupo="GG_RRHH_USUARIOS"; Prefijo="rrhh"},
 @{OU="Contabilidad"; Grupo="GG_CONT_USUARIOS"; Prefijo="cont"},
 @{OU="Compras"; Grupo="GG_COMP_USUARIOS"; Prefijo="comp"},
 @{OU="Ventas"; Grupo="GG_VENT_USUARIOS"; Prefijo="vent"},
 @{OU="Bodega"; Grupo="GG_BOD_USUARIOS"; Prefijo="bod"},
 @{OU="Informatica"; Grupo="GG_INFO_USUARIOS"; Prefijo="info"},
 @{OU="AtencionCliente"; Grupo="GG_ATC_USUARIOS"; Prefijo="atc"}
)

$password = Read-Host "Contraseña para los usuarios de prueba" -AsSecureString

foreach ($area in $areas) {

    $ouPath = "OU=$($area.OU),$usuariosOU"

    New-ADOrganizationalUnit `
        -Name $area.OU `
        -Path $usuariosOU `
        -ProtectedFromAccidentalDeletion $false

    New-ADGroup `
        -Name $area.Grupo `
        -SamAccountName $area.Grupo `
        -GroupCategory Security `
        -GroupScope Global `
        -Path $gruposOU

    for ($i=1; $i -le 3; $i++) {

        $usuario="$($area.Prefijo).usuario$i"

        New-ADUser `
            -Name $usuario `
            -SamAccountName $usuario `
            -UserPrincipalName "$usuario@corp.eltriunfo.test" `
            -Path $ouPath `
            -AccountPassword $password `
            -Enabled $true `
            -ChangePasswordAtLogon $false

        Add-ADGroupMember `
            -Identity $area.Grupo `
            -Members $usuario
    }
}
```

Este script puede reutilizarse en la nueva VM con Desktop Experience.

Antes de ejecutarlo:

- verificar que el dominio esté correctamente creado;
- verificar que las OU no existan;
- evitar duplicados;
- mantener apagada la VM Core si comparte IP, hostname o dominio.

---

# Comandos de validación utilizados

## OU

```powershell
Get-ADOrganizationalUnit -Filter * |
Select-Object Name, DistinguishedName |
Format-Table -AutoSize
```

## OU departamentales

```powershell
Get-ADOrganizationalUnit `
-SearchBase "OU=Usuarios,DC=corp,DC=eltriunfo,DC=test" `
-SearchScope OneLevel `
-Filter * |
Select-Object Name
```

## Usuarios

```powershell
Get-ADUser -Filter * |
Select-Object SamAccountName
```

## Usuarios de una OU

```powershell
Get-ADUser `
-SearchBase "OU=Ventas,OU=Usuarios,DC=corp,DC=eltriunfo,DC=test" `
-Filter * |
Select-Object SamAccountName
```

## Grupos

```powershell
Get-ADGroup -Filter * |
Select-Object Name, GroupScope
```

## Grupos creados

```powershell
Get-ADGroup `
-Filter 'Name -like "GG_*" -or Name -like "DL_*"' |
Select-Object Name, GroupScope |
Format-Table -AutoSize
```

## Miembros

```powershell
Get-ADGroupMember "GG_CONT_USUARIOS"
```

## Permiso

```powershell
Get-ADGroupMember "DL_CONTABILIDAD_RW"
```

## DNS

```powershell
Get-DnsServerZone
```

## Registros

```powershell
Get-DnsServerResourceRecord `
-ZoneName "corp.eltriunfo.test"
```

## Resolución

```powershell
Resolve-DnsName www.corp.eltriunfo.test
```

---

# Sitio web

El sitio actual es demasiado básico para una defensa final.

Actualmente solo muestra:

```text
Comercial El Triunfo S.A. de C.V.
```

Debe mejorarse para que sea un sitio institucional sencillo.

Puede contener:

- nombre de empresa;
- descripción breve;
- productos o servicios;
- contacto ficticio;
- diseño CSS básico.

No necesita ser complejo.

Debe seguir alojándose en:

```text
/var/www/html/index.html
```

y funcionar mediante:

```text
http://www.corp.eltriunfo.test
```

---

# Estrategia de corrección recomendada

No destruir inmediatamente la implementación Core.

Debe utilizarse como respaldo.

La estrategia preferida es crear o reutilizar una VM con:

```text
Windows Server Desktop Experience
```

y reconstruir de manera limpia:

1. configuración de red;
2. hostname;
3. instalación de AD DS;
4. instalación/configuración DNS;
5. creación del dominio;
6. OU;
7. usuarios;
8. grupos;
9. permisos;
10. recurso compartido;
11. registro DNS `www`;
12. zona inversa si corresponde;
13. conectividad con Ubuntu;
14. acceso HTTP;
15. validación visual mediante navegador.

---

# Precaución con la VM Core anterior

La VM anterior utiliza:

```text
Hostname: SRV-DC01
IP: 10.10.10.10
Domain: corp.eltriunfo.test
```

Si la nueva VM va a utilizar los mismos datos:

**NO encender ambas simultáneamente.**

Evitar conflictos de:

- IP;
- hostname;
- identidad de servidor;
- dominio;
- DNS.

Mantener la VM Core apagada mientras la nueva utiliza esa identidad.

---

# Qué debe mostrarse en la defensa

La versión corregida debe permitir mostrar claramente:

1. VirtualBox con las dos VMs.
2. Windows Server con escritorio gráfico.
3. Server Manager.
4. AD DS instalado.
5. Active Directory Users and Computers.
6. Dominio `corp.eltriunfo.test`.
7. OU `Usuarios`.
8. Las ocho OU departamentales.
9. Tres usuarios dentro de una OU.
10. Grupos globales.
11. Grupo `DL_CONTABILIDAD_RW`.
12. Membresías.
13. Recurso compartido.
14. DNS Manager.
15. Forward Lookup Zones.
16. Zona `corp.eltriunfo.test`.
17. Registro A `www`.
18. Zona inversa si la actividad lo requiere.
19. IP de Windows.
20. IP de Ubuntu.
21. Ping entre ambas máquinas.
22. Apache activo en Ubuntu.
23. Navegador en Windows.
24. `http://www.corp.eltriunfo.test`.
25. Página realmente servida desde Ubuntu.

---

# Elementos que NO deben asumirse implementados

No afirmar que existen sin verificarlos:

- Active Directory Certificate Services;
- HTTPS;
- certificados TLS;
- firewall;
- VLAN;
- IDS/IPS;
- alta disponibilidad;
- backup;
- GPO avanzadas.

Algunos aparecieron durante la fase de Diseño, pero no necesariamente forman parte de la implementación mínima completada.

Antes de agregar algo, revisar literalmente la consigna.

---

# Restricciones del equipo

La computadora tiene recursos limitados.

Anteriormente pudo manejar aproximadamente:

```text
Server Core: 768 MB RAM
Windows 10: 2048 MB RAM
```

La nueva solución debe optimizar recursos, pero nunca eliminar requisitos académicos.

Preferir:

- únicamente dos VMs activas;
- VM Core anterior apagada;
- cerrar aplicaciones innecesarias;
- asignación razonable de RAM;
- snapshots antes de cambios importantes;
- evitar servicios no solicitados.

No resolver la limitación usando Server Core otra vez.

---

# Codex Cloud

Este repositorio se utilizará como contexto/workspace para Codex Cloud.

Codex Cloud NO tiene acceso directo a:

- VirtualBox local;
- las VMs;
- el escritorio del usuario.

Por tanto Codex debe:

- leer este README;
- preparar scripts;
- revisar configuraciones;
- proporcionar pasos GUI exactos;
- ayudar a diagnosticar errores;
- mantener contexto;
- revisar documentación;
- generar archivos cuando sea útil.

El usuario ejecutará las acciones localmente dentro de VirtualBox.

No pedir subir archivos `.vdi`, `.vbox` o máquinas virtuales completas a GitHub.

---

# Instrucciones obligatorias para Codex

Antes de hacer cualquier cambio:

1. Leer completamente este README.
2. Revisar literalmente el requisito que se está intentando cumplir.
3. No recomendar Windows Server Core.
4. Priorizar Desktop Experience.
5. Priorizar evidencia visual.
6. No destruir la VM anterior.
7. Evitar conflictos de IP.
8. Evitar conflictos de hostname.
9. No asumir acceso a VirtualBox.
10. Dar instrucciones GUI exactas cuando correspondan.
11. Dar comandos reproducibles cuando sean útiles.
12. Verificar resultados antes de continuar.
13. No inventar componentes.
14. No asumir que algo quedó configurado solo porque fue discutido.
15. Diferenciar claramente entre:
   - implementado;
   - propuesto;
   - pendiente.
16. Si una optimización técnica contradice la consigna académica, seguir la consigna.
17. Pensar siempre en cómo se defenderá la implementación frente al docente.

---

# Estado final deseado

## Windows Server

```text
Windows Server Desktop Experience

Hostname:
SRV-DC01

IP:
10.10.10.10/24

Gateway:
10.10.10.1

DNS:
10.10.10.10

Domain:
corp.eltriunfo.test

NetBIOS:
ELTRIUNFO
```

Servicios:

```text
AD DS
DNS
OU
24 usuarios
8 grupos globales
grupo Domain Local
permisos
recurso compartido
GUI funcional
```

---

## Ubuntu Server

```text
Hostname:
SRV-WEB01

IP:
10.10.10.3/24

Gateway:
10.10.10.1

Servicio:
Apache
```

---

## Resolución web

```text
www.corp.eltriunfo.test
        ↓
10.10.10.3
        ↓
Ubuntu
        ↓
Apache
        ↓
Sitio institucional
```

---

# Criterio final de cumplimiento

La actividad no debe considerarse terminada simplemente porque los comandos funcionen.

Debe cumplir simultáneamente:

```text
REQUISITO LITERAL
+
SERVICIOS FUNCIONALES
+
WINDOWS SERVER GRÁFICO
+
EVIDENCIA VISUAL
+
COMUNICACIÓN ENTRE LAS VMs
+
DNS FUNCIONAL
+
HTTP FUNCIONAL
+
DEFENSA CLARA
```
