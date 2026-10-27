# Seguridad de Redes - Proyecto Comercial El Triunfo

## Contexto

Proyecto universitario de la asignatura **Seguridad de Redes - SDR901 G01T** de la **Universidad Don Bosco**.

Caso: empresa ficticia **Comercial El Triunfo S.A. de C.V.**

El proyecto se divide en:

1. Descubrimiento
2. Diseño
3. Construcción / Implementación

La fase actual es la **Actividad 3 - Construcción**, que necesita corrección porque la implementación anterior fue guiada de forma incompleta.

---

# IMPORTANTE: ERRORES PREVIOS QUE NO DEBEN REPETIRSE

La asistencia anterior cometió varios errores que afectaron directamente la preparación de la actividad y de la defensa.

## Error 1 - Se eligió Windows Server Core cuando la actividad requería entorno gráfico

Este fue el error principal.

La actividad requería **Windows Server en entorno gráfico**, pero se recomendó utilizar:

```text
Windows Server Core
```

La decisión se tomó principalmente para ahorrar RAM y recursos de la computadora.

Esto fue incorrecto para el contexto académico.

Aunque Server Core técnicamente permite instalar:

- Active Directory Domain Services
- DNS
- usuarios
- OU
- grupos
- recursos compartidos

la actividad y la defensa requerían poder mostrar visualmente herramientas como:

- Server Manager
- Active Directory Users and Computers
- DNS Manager
- estructura gráfica del dominio
- OU
- usuarios
- grupos
- propiedades
- navegador web

Durante la defensa se observó que otros estudiantes estaban mostrando precisamente estas herramientas gráficas.

### Consecuencia

La infraestructura funcionaba técnicamente, pero quedó **incompleta respecto a la consigna evaluada** y mucho más difícil de demostrar.

### Regla para Codex

**NO recomendar Server Core.**

La solución corregida debe utilizar:

```text
Windows Server con Desktop Experience
```

---

## Error 2 - Se priorizó "lo mínimo técnicamente funcional" sobre la rúbrica

La asistencia anterior priorizó:

- bajo consumo de RAM;
- PowerShell;
- CLI;
- reutilización de una VM Core;
- mínimo consumo de recursos;

en vez de priorizar:

```text
REQUISITO LITERAL
+
FORMA DE EVALUACIÓN
+
DEMOSTRACIÓN VISUAL
+
FUNCIONALIDAD
```

Esto es especialmente importante porque el usuario había advertido que:

- era una actividad evaluada;
- debía defenderse en vivo;
- no quería repetir problemas ocurridos anteriormente en otra materia de Servidores.

### Regla para Codex

Antes de recomendar una arquitectura o instalación:

1. revisar literalmente los requisitos;
2. identificar cómo se evaluará;
3. identificar qué deberá mostrarse en pantalla;
4. solo después optimizar recursos.

---

## Error 3 - Se intentó justificar Server Core después de detectar el problema

Cuando apareció el problema durante la defensa, la asistencia anterior siguió intentando justificar Server Core diciendo que:

- técnicamente seguía siendo Windows Server;
- AD DS funcionaba;
- DNS funcionaba;
- PowerShell podía demostrar la configuración.

Eso no resolvía el problema porque el requisito era **entorno gráfico**.

### Regla para Codex

Si existe una diferencia entre:

```text
"técnicamente posible"
```

y:

```text
"lo que exige literalmente la actividad"
```

se debe cumplir lo segundo.

---

## Error 4 - Se confundió una implementación funcional con una implementación adecuada para defensa

Se construyeron pruebas mediante comandos como:

```powershell
Get-ADUser
Get-ADGroup
Get-ADOrganizationalUnit
Resolve-DnsName
Invoke-WebRequest
```

Estas pruebas sirven técnicamente, pero no sustituyen una implementación gráfica cuando la evaluación espera ver:

- AD Users and Computers
- DNS Manager
- Server Manager
- navegador
- estructura del dominio visualmente

### Regla para Codex

La solución corregida debe incluir **ambas cosas**:

- funcionamiento real;
- evidencia gráfica clara.

---

## Error 5 - No se detectó a tiempo el requisito gráfico al revisar las instrucciones

La asistencia tuvo acceso a las instrucciones de la Actividad 3 y aun así no detuvo la implementación Core.

Debió decir desde el principio:

```text
"Esta actividad requiere entorno gráfico.
No debemos utilizar Server Core."
```

No lo hizo.

### Consecuencia

Se invirtió tiempo en:

- clonar una VM Core;
- eliminar un dominio anterior;
- renombrarla;
- crear un dominio nuevo;
- configurar red;
- crear OU;
- crear usuarios;
- crear grupos;
- crear permisos;
- configurar DNS;

sobre una base que luego resultó inadecuada para la entrega.

---

## Error 6 - Se complicó innecesariamente la migración hacia Codex

Posteriormente, al intentar trasladar el proyecto a Codex Cloud, la asistencia también dio varias indicaciones incorrectas o poco útiles.

Entre ellas:

- asumir que existía una app de escritorio;
- recomendar "Open folder" cuando el usuario estaba usando únicamente navegador;
- insistir con `Choose remote`;
- mandar al usuario a Settings repetidamente;
- no comprender inicialmente que Codex no permitía enviar nada porque no había entorno configurado;
- sugerir rutas relacionadas con Remote que no correspondían;
- sugerir repositorios sin aclarar primero que las VMs de VirtualBox no pueden subirse ni ejecutarse de esa manera.

### Situación correcta

El usuario:

- NO quiere instalar la app de escritorio;
- utiliza Codex desde navegador;
- está creando un **Codex Cloud Environment**;
- necesita un repositorio únicamente como workspace/contexto;
- las máquinas virtuales permanecen localmente en VirtualBox.

### Regla para Codex

No asumir acceso directo a las VMs.

Codex Cloud debe:

- leer contexto;
- mantener scripts;
- preparar comandos;
- revisar documentación;
- ayudar a reconstruir la configuración;

pero el usuario ejecutará las acciones dentro de VirtualBox localmente.

---

# Objetivo actual

Corregir la Actividad 3 para que cumpla literalmente con la consigna y pueda defenderse correctamente.

La infraestructura debe tener únicamente:

- 1 Windows Server
- 1 Ubuntu Server

## Requisito crítico

Windows Server debe utilizar:

```text
Desktop Experience / entorno gráfico
```

No utilizar Server Core para la entrega final.

---

# Arquitectura esperada

## Windows Server

Configuración deseada:

```text
Hostname: SRV-DC01
IP: 10.10.10.10/24
Gateway: 10.10.10.1
DNS: 10.10.10.10
Domain: corp.eltriunfo.test
NetBIOS: ELTRIUNFO
```

Servicios:

- Active Directory Domain Services
- DNS
- dominio corporativo
- Unidades Organizativas
- usuarios
- grupos de seguridad
- permisos
- recurso compartido

Debe poder administrarse y mostrarse gráficamente mediante:

- Server Manager
- Active Directory Users and Computers
- DNS Manager
- herramientas gráficas de administración correspondientes

---

# Ubuntu Server

Configuración utilizada:

```text
Hostname: SRV-WEB01
IP: 10.10.10.3/24
Gateway: 10.10.10.1
```

Servicios:

- Apache
- sitio institucional
- HTTP

El sitio debe abrirse desde Windows mediante:

```text
http://www.corp.eltriunfo.test
```

---

# Red VirtualBox

NAT Network:

```text
Nombre: ELTRIUNFO
Red: 10.10.10.0/24
Gateway: 10.10.10.1
```

Servidores:

```text
Windows Server: 10.10.10.10
Ubuntu Server:  10.10.10.3
```

Ambas máquinas deben comunicarse.

---

# Active Directory

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

Se requieren:

```text
3 usuarios por OU departamental
```

Total:

```text
24 usuarios
```

Usuarios utilizados anteriormente:

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

# Grupos

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

Grupo Domain Local creado como ejemplo:

```text
DL_CONTABILIDAD_RW
```

Modelo:

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
Recurso compartido Contabilidad
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

Permisos usados:

```text
ELTRIUNFO\Domain Admins
    → Full Access

ELTRIUNFO\DL_CONTABILIDAD_RW
    → Change Access
```

---

# DNS

Zona:

```text
corp.eltriunfo.test
```

Registro:

```text
www
```

Debe producir:

```text
www.corp.eltriunfo.test
        ↓
10.10.10.3
```

La IP `10.10.10.3` corresponde al Ubuntu Server con Apache.

---

# Zona inversa

Red:

```text
10.10.10.0/24
```

Zona inversa:

```text
10.10.10.in-addr.arpa
```

PTR posibles:

```text
10.10.10.3
→ www.corp.eltriunfo.test

10.10.10.10
→ SRV-DC01.corp.eltriunfo.test
```

IMPORTANTE:

No asumir que la zona inversa quedó implementada correctamente en la versión anterior.

Verificar antes.

---

# Ubuntu / Apache

Apache estaba funcionando en la implementación anterior.

Comando:

```bash
sudo service apache2 status
```

Resultado observado:

```text
active (running)
```

Archivo:

```text
/var/www/html/index.html
```

Contenido anterior mínimo:

```text
Comercial El Triunfo S.A. de C.V.
```

El sitio debería mejorarse para que sea un sitio institucional sencillo pero presentable.

Puede contener:

- nombre de empresa;
- descripción;
- productos/servicios;
- contacto;
- CSS básico.

No necesita ser complejo.

---

# Validaciones

## Windows → Ubuntu

```powershell
ping 10.10.10.3
```

Funcionó anteriormente.

## Ubuntu → Windows

```bash
ping -c 4 10.10.10.10
```

Funcionó anteriormente.

---

# Resolución DNS

Desde Windows:

```powershell
Resolve-DnsName www.corp.eltriunfo.test
```

Debe devolver:

```text
10.10.10.3
```

---

# HTTP

Desde Windows:

```powershell
Invoke-WebRequest http://www.corp.eltriunfo.test -UseBasicParsing
```

Anteriormente devolvió:

```text
StatusCode: 200
```

La versión corregida debe además abrirlo visualmente en un navegador:

```text
http://www.corp.eltriunfo.test
```

Debe mostrar la página realmente alojada en Ubuntu.

---

# Script utilizado anteriormente para crear AD

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

Este script puede reutilizarse en la nueva VM gráfica, pero debe revisarse antes de ejecutarse para evitar duplicados o conflictos.

---

# Estado de la VM anterior

Existe una implementación anterior basada en:

```text
Windows Server Core
```

con:

```text
Hostname: SRV-DC01
IP: 10.10.10.10
Dominio: corp.eltriunfo.test
```

Esta VM NO debe destruirse inmediatamente.

Debe mantenerse como respaldo mientras se construye la versión correcta.

IMPORTANTE:

No encender simultáneamente dos servidores con:

```text
misma IP
mismo hostname
misma identidad de DC
```

sin una estrategia correcta.

---

# Estrategia preferida

Crear o reutilizar una VM de:

```text
Windows Server Desktop Experience
```

y reconstruir de manera limpia:

1. configuración de red;
2. hostname;
3. AD DS;
4. DNS;
5. dominio;
6. OU;
7. usuarios;
8. grupos;
9. permisos;
10. recurso compartido;
11. registro DNS para Ubuntu;
12. zona inversa si es necesaria;
13. pruebas de conectividad;
14. prueba HTTP desde navegador.

La VM Core anterior debe permanecer apagada cuando la nueva utilice la misma IP/hostname.

---

# Qué debe mostrarse durante la defensa

La defensa corregida debería mostrar:

1. Ambas VMs en VirtualBox.
2. Windows Server con escritorio gráfico.
3. Server Manager.
4. AD DS instalado.
5. Active Directory Users and Computers.
6. `corp.eltriunfo.test`.
7. OU `Usuarios`.
8. Las ocho OU departamentales.
9. Tres usuarios dentro de una OU.
10. Grupos globales.
11. Grupo Domain Local.
12. Membresías.
13. DNS Manager.
14. Forward Lookup Zones.
15. `corp.eltriunfo.test`.
16. Registro A `www`.
17. Zona inversa si corresponde.
18. Dirección IP de Windows.
19. Dirección IP de Ubuntu.
20. Ping entre máquinas.
21. Apache activo en Ubuntu.
22. Navegador de Windows.
23. `http://www.corp.eltriunfo.test`.
24. Página alojada en Ubuntu.

---

# Elementos que NO deben darse por implementados

No asumir que existen actualmente:

- AD CS
- HTTPS
- certificados TLS
- firewall configurado
- VLAN
- IDS/IPS
- alta disponibilidad
- backup
- GPO avanzadas

Estos elementos pueden haber aparecido durante el diseño, pero no todos forman parte de la implementación actual.

Verificar la consigna literal antes de agregarlos.

---

# Restricción de recursos

La computadora del usuario tiene recursos limitados.

Eso debe tomarse en cuenta, pero **NO puede utilizarse para eliminar requisitos de la actividad**.

Optimizar mediante:

- RAM razonable;
- apagar VM Core anterior;
- mantener únicamente dos VMs activas;
- cerrar aplicaciones innecesarias;
- usar snapshots;
- evitar servicios no solicitados.

No solucionar el problema sustituyendo Desktop Experience por Core.

---

# Instrucciones específicas para Codex

Al continuar este proyecto:

1. Leer este README completo antes de proponer cambios.
2. No recomendar Windows Server Core.
3. Priorizar la consigna literal.
4. Priorizar evidencia gráfica para la defensa.
5. No destruir la VM anterior.
6. Evitar conflictos de IP y hostname.
7. Indicar pasos GUI exactos.
8. Proporcionar comandos cuando ayuden a automatizar.
9. Verificar el resultado después de cada fase.
10. No agregar tecnologías que la actividad no pide.
11. No asumir acceso directo a VirtualBox.
12. Recordar que Codex está ejecutándose en Cloud.
13. El usuario ejecutará localmente los pasos de VirtualBox.
14. Los scripts del repositorio sirven como soporte y automatización.
15. Si una instrucción académica contradice una optimización técnica, **seguir la instrucción académica**.

---

# Resultado final deseado

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
```

Con:

```text
AD DS
DNS
OU
24 usuarios
8 grupos globales
grupo Domain Local
permisos
recurso compartido
GUI
```

## Ubuntu

```text
Hostname:
SRV-WEB01

IP:
10.10.10.3/24

Servicio:
Apache
```

## Resultado DNS/HTTP

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

## Criterio final

La implementación no se considera terminada únicamente porque los comandos funcionen.

Debe cumplir simultáneamente:

```text
REQUISITO LITERAL
+
SERVICIOS FUNCIONALES
+
ENTORNO GRÁFICO
+
EVIDENCIA VISUAL
+
DEFENSA CLARA
```
