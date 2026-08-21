# CONTEXTO.md — Proyecto docente SOM · 1º/2º SMR
> Este documento resume todo lo acordado en las sesiones de diseño del módulo
> Sistemas Operativos Monopuesto, para que cualquier instancia de Claude
> (incluida Claude Code) tenga el contexto completo sin necesidad de repetir
> la conversación original.
---
## 1. Datos del proyecto
- **Centro:** IES Medina Azahara
- **Ciclo:** CF Grado Medio - Sistemas Microinformáticos y Redes (SMR)
- **Módulo:** Sistemas Operativos Monopuesto (SOM)
- **Modalidad:** FP Dual formal, inicio de fase en empresa: **30 de abril**
- **Horas del módulo:** 5 horas/semana lectivas
- **Total estimado hasta el 30 de abril:** ~135-150h en ~28-30 semanas reales
  (calendario ajustado, sin margen relevante para imprevistos)
- **Identidad institucional:** logo IES Medina Azahara, paleta azul oscuro y
  magenta, fuente News Gothic MT, cabecera/pie con numeración de página
  (logo disponible en sesiones previas en `/home/claude/logo_ies.jpg`)
---
## 2. Rol y enfoque pedagógico general
Claude debe actuar simultáneamente como:
- Experto en sistemas operativos (Windows y GNU/Linux)
- Administrador de sistemas con experiencia práctica real
- Experto en hardware/software de sistemas microinformáticos
- Experto en docencia de FP en España (especialmente SMR)
- Experto en diseño de materiales didácticos
**Principio fundamental:** no se busca que el alumnado memorice cómo hacer
algo, sino que entienda qué está haciendo, por qué, qué puede salir mal y
cómo solucionarlo. Menos memorización mecánica → más comprensión. Menos
recetas → más razonamiento. Menos teoría aislada → más aplicación práctica.
**Progresión pedagógica preferida:**
Concepto → ejemplo → demostración → práctica guiada → práctica autónoma →
problema → diagnóstico → solución.
**Estilo de redacción:** libro de texto moderno de FP — claro, explicativo,
fluido, con párrafos completos (no solo listas y definiciones). Explicar
siempre el "por qué" de las cosas, no solo el "cómo". Español de España.
Términos técnicos explicados la primera vez que aparecen (incluyendo su
forma en inglés cuando sea el término habitual del sector, ej. "Controlador
(driver)").
**No dar la razón por defecto:** Claude debe ser crítico y avisar de errores
técnicos, tecnologías obsoletas, prácticas poco seguras, decisiones
pedagógicas mejorables o secuenciación mejorable, antes de generar material
basado en ellas.
**Nivel del alumnado:** SMR, Grado Medio. No presuponer conocimientos
avanzados. Explicar siempre hardware, procesos, permisos, redes, IP,
BIOS/UEFI, virtualización, terminal, etc. la primera vez que se usan como
base de algo posterior.
---
## 3. Reorientación del enfoque (curso actual)
El módulo se reorienta hacia un enfoque marcadamente práctico. Se reduce
deliberadamente la profundidad teórica en los siguientes puntos, salvo que
un CE lo exija explícitamente:
- No incluir algoritmos de planificación de procesos (FIFO, RR, SJF...).
  Si acaso, mencionar de forma breve qué usan los sistemas actuales
  (Completely Fair Scheduler / vruntime en Linux; Planificador de Prioridad
  Dinámica y Thread Director en CPUs híbridas de Windows 11) sin entrar en
  el algoritmo en detalle.
- No incluir gestión de memoria con cálculos de particiones fijas/variables,
  paginación o segmentación. Sí ideas generales de cómo gestionan memoria
  los sistemas actuales (Linux/Ubuntu y Windows 11: paginación por demanda).
- No incluir algoritmos de planificación de disco.
- Limitar la conversión de sistemas numéricos a lo estrictamente necesario
  para comprender permisos (binario/octal) u otros usos prácticos concretos.
Motivo: el enfoque de libros como "Sistemas Operativos Monopuesto" de
somebooks.es se considera excesivamente denso y algo obsoleto para el
perfil de técnico medio SMR, cuyas destrezas deben priorizar lo práctico.
---
## 4. Tratamiento de RA2 y RA5
El centro trabaja en modalidad **FP Dual formal**, con inicio de la fase en
empresa el **30 de abril**. Oficialmente, **RA2** (instalación de sistemas
operativos en máquina real) **se evalúa en la empresa**, mediante el
instrumento/informe que aporte el tutor de empresa correspondiente.
La experiencia de cursos anteriores (incluso en Dual formal) muestra que no
todo el alumnado realiza en la empresa tareas específicas de instalación.
Por ello, en la programación de aula, **el bloque de RA5** (creación de
máquinas virtuales) **incorpora también las actividades prácticas de
instalación propias de RA2**: planificación de la instalación, selección de
sistema operativo, particionado, gestores de arranque (incluyendo dual
boot), resolución de incidencias de instalación, licencias y actualización
post-instalación. Esto se hace **sobre máquina virtual, no sobre hardware
real**, con el objetivo de que el alumnado llegue competente en instalación
antes de incorporarse a la empresa el 30 de abril.
Debe quedar siempre claro en cualquier material o documento generado que:
- La calificación oficial de RA2 procede de la empresa, no del aula.
- Las actividades de instalación dentro de RA5 refuerzan esa competencia
  pero no sustituyen ni duplican la evaluación oficial de RA2.
- El CE de RA5 relativo a pruebas de rendimiento del sistema (g) se cubre
  con benchmarks sencillos (tiempo de arranque, velocidad de disco
  asignado, comparativa de recursos VM vs. anfitrión), **sin anticipar**
  contenido de monitorización de procesos/servicios propio de RA4.
**Pendiente de confirmar con el departamento:** el mecanismo exacto de
integración de la nota de RA2 (procedente del tutor de empresa) en la
calificación final del módulo, según la normativa de FP Dual aplicable.
---
## 5. Secuenciación del curso
Orden acordado: **RA1 → RA5 → RA3 (Linux) → RA3 (Windows) → RA4 (Linux) →
RA4 (Windows)**
Razón del orden: RA1 sienta el vocabulario base; RA5 justo después permite
instalar y dejar funcionando las VMs (con el refuerzo de RA2 incluido)
**antes** de necesitarlas para RA3 y RA4, evitando una doble instalación.
RA3 y RA4 no pueden trabajarse sin sistemas ya instalados.
| Orden | Bloque | Horas aprox. | Semanas aprox. |
|---|---|---|---|
| 1 | RA1 — Fundamentos simplificados | 18-20h | 4 |
| 2 | RA5 — Virtualización + instalación profunda (refuerzo RA2) | 28-30h | 6 |
| 3 | RA3 — Configuración Linux | 22-25h | 5 |
| 4 | RA3 — Configuración Windows | 18-20h | 4 |
| 5 | RA4 — Administración Linux | 25-28h | 5-6 |
| 6 | RA4 — Administración Windows | 22-25h | 4-5 |
Todo esto debe completarse antes del 30 de abril. RA2 se evalúa después,
ya en la empresa.
---
## 6. Ponderación de Resultados de Aprendizaje
**Actual (documento oficial vigente):** RA1: 20% | RA2: 15% | RA3: 25% |
RA4: 25% | RA5: 15%
**Propuesta (pendiente de aprobación por el departamento):**
| RA | % actual | % propuesto | Justificación |
|---|---|---|---|
| RA1 | 20% | **15%** | Teoría muy recortada, menos horas dedicadas |
| RA2 | 15% | **10%** | Evaluación externa (empresa), menor trabajo de aula específico |
| RA3 | 25% | **25%** | Se mantiene: núcleo práctico central |
| RA4 | 25% | **30%** | Sube: más horas dedicadas y mayor relevancia profesional directa |
| RA5 | 15% | **20%** | Sube: asume doble función (virtualización propia + refuerzo de RA2) |
Pendiente de confirmar con el departamento: mecanismo exacto de integración
de la nota de RA2 (procedente del tutor de empresa) en la calificación
final del módulo.
---
## 7. Mapa de contenidos por bloque (con asociación a CE)
### Bloque 1 — RA1: Fundamentos simplificados
CE cubiertos: a, b, c, d, e, f, g, h, i (todos)
- **CE-a (actualizado):** NO incluir desglose de hardware (se cubre en el
  módulo de Montaje y Mantenimiento). Incluir en su lugar:
  - Concepto de sistema informático (hardware, software, usuarios, y cómo
    se relacionan entre sí)
  - Software de base (SO, drivers, utilidades) vs. software de aplicación
  - Niveles del sistema informático (modelo de capas: hardware → software
    de base → lenguajes/entornos → software de aplicación → usuario)
  - Lenguajes de programación: concepto general y su ubicación en el
    modelo de niveles (máquina, ensamblador, alto nivel), sin sintaxis ni
    programación real
  - **Ojo:** debe quedar ligero, es solo para situar dónde encaja el SO en
    la pila completa, no para que el alumno programe
- CE-b: representación de la información, solo lo necesario para permisos
  (binario/octal)
- CE-c: funciones del SO (gestión de procesos, memoria, archivos, E/S) sin
  algoritmos — se apoya en CE-a pero con foco solo en la pieza "SO"
- CE-d: arquitectura del SO por capas (núcleo, drivers, shell,
  aplicaciones), comparando Windows/Linux a alto nivel
- CE-e: procesos y sus estados (concepto, sin planificadores)
- CE-f: estructura y organización del sistema de archivos (jerarquía, rutas)
- CE-g: atributos de archivo/directorio (Windows y Linux)
- CE-h: permisos de archivos y directorios (introducción; se profundiza en
  RA4)
- CE-i: sistemas transaccionales (concepto, journaling ext4/NTFS)
Prácticas: identificar componentes/software en imágenes, calculadora
binario-octal aplicada a permisos, exploración de jerarquía de archivos,
clasificación SO vs. hardware.
### Bloque 2 — RA5 (+ refuerzo RA2): Virtualización e instalación
RA5 CE cubiertos: a-g (todos). RA2 CE reforzados (no evaluados oficialmente
aquí): a-h (todos).
- RA5-a: máquina real vs. virtual, tipos de hipervisor
- RA5-b: ventajas/inconvenientes de virtualizar
- RA5-c: instalación de software de virtualización (libre/propietario)
- RA2-a: verificación de idoneidad de hardware (VT-x/AMD-V, RAM, disco)
- RA2-b: selección de SO según caso de uso
- RA2-c + RA5-d: plan de instalación (particionado, disco, red de la VM)
- RA2-d: parámetros básicos de instalación
- RA2-e: gestor de arranque, incluyendo dual boot
- RA2-f: incidencias típicas de instalación
- RA2-g: licencias (libre vs. propietario)
- RA2-h: actualización post-instalación
- RA5-e: configuración de la VM (recursos, snapshots, red)
- RA5-f: relación VM - anfitrión (carpetas compartidas, red NAT/bridge)
- RA5-g: pruebas de rendimiento básicas (arranque, disco, VM vs. anfitrión)
- Ampliación no evaluable: introducción a Docker (diferencia VM vs.
  contenedor)
Nota obligatoria en el material: cada actividad debe indicar si su origen
curricular es RA5 o si además refuerza RA2, dejando constancia de que la
evaluación oficial de RA2 llega por la empresa.
### Bloque 3 — RA3 Linux: Configuración
CE a-i aplicados a Linux: arranque/GRUB/systemd, sesiones, CLI vs. entorno
gráfico, personalización, ext4/fstab, recuperación (modo rescate, GRUB),
actualización (APT/DNF), paquetes .deb/.rpm, asistentes de red/dispositivos,
automatización básica (cron/at, scripts sin bucles complejos).
### Bloque 4 — RA3 Windows: Configuración
CE a-i aplicados a Windows: arranque/opciones avanzadas, sesiones locales,
Configuración vs. Panel de control, PowerShell vs. CMD, personalización,
Administrador de discos/NTFS, WinRE/Restaurar sistema, Windows Update,
instaladores/Store/winget, asistentes, Programador de tareas/PowerShell
básico.
### Bloque 5 — RA4 Linux: Administración
CE a-i aplicados a Linux: usuarios/grupos (useradd, /etc/passwd),
permisos (chmod/chown), procesos (ps/top/kill/nice), servicios
(systemctl/journal), memoria (free/swap), logs (/var/log, journalctl),
almacenamiento (df/du), Samba/NFS básico, archivos de configuración en /etc.
### Bloque 6 — RA4 Windows: Administración
CE a-i aplicados a Windows: usuarios/grupos locales (lusrmgr.msc), permisos
NTFS con herencia, Administrador de tareas, servicios (services.msc),
rendimiento, Visor de eventos, discos/TRIM/liberador de espacio, recursos
compartidos en red (NTFS + permisos de red), msinfo32/registro básico.
### Cobertura de CE — control
Todos los CE de RA1, RA2 (reforzado), RA3 (×2 pistas), RA4 (×2 pistas) y
RA5 quedan cubiertos. Único punto abierto: mecanismo administrativo de
integración de la nota de RA2 (empresa) — no es un problema de contenidos.
---
## 8. Formato de materiales por unidad
Para cada unidad didáctica (UD) se generan **dos materiales diferenciados**:
| | Docencia (para el profesor) | Apuntes (para el alumnado) |
|---|---|---|
| Profundidad | Mayor: contexto histórico/técnico, matices, preguntas frecuentes del alumnado y cómo resolverlas, errores conceptuales habituales en clase | La necesaria para cubrir los CE, sin extras |
| Estructura | Guion de clase: orden de explicación, demos en vivo, tiempos orientativos, puntos donde suele atascarse el alumnado | Estructura orientativa de unidad (concepto → funcionamiento → práctica → casos → resumen) |
| Prácticas | Con solución completa y notas de qué buscar al corregir | Enunciado limpio + casos prácticos ya resueltos como referencia (no todos, para dejar trabajo autónomo real) |
| Extras | Curiosidades, enlaces a documentación oficial, ideas de preguntas de examen | Solo lo decidido para la unidad final |
**Estructura orientativa de unidad** (adaptable, no mecánica):
Introducción → ¿Por qué necesitamos esto? → Conceptos fundamentales →
Funcionamiento → Aplicación práctica → Práctica guiada → Práctica autónoma
→ Caso práctico/problema → Errores frecuentes → Buenas prácticas →
Actualidad (solo si aporta valor) → Resumen → Actividades → Prácticas →
Relación con RA y CE (tabla de correspondencia).
---
## 9. Estructura de carpetas y estrategia de publicación (dos repos)
**Decisión clave:** la parte de **docencia** (material del profesor) no debe
ser pública para el alumnado. La parte de **apuntes** sí debe serlo. Esto
implica trabajar con **dos repositorios**:
- **Repo privado** (`SOM-1SMR-privado`) — fuente de verdad única, contiene
  todo (docencia + apuntes). Es donde se trabaja el día a día.
- **Repo público** (`SOM-1SMR-alumnos`) — contiene solo el contenido de
  `apuntes/`, se publica de forma consciente y puntual (no automática),
  mediante `git subtree push`.
Se descartan la copia manual (duplica trabajo, riesgo de desincronización)
y la publicación automática vía GitHub Actions (riesgo de publicar algo
sensible por error de carpeta en un commit). Se opta por `git subtree`:
mantiene una sola fuente de verdad, pero publicar sigue siendo un paso
manual y deliberado.
**Estructura del repo privado** (con `apuntes/` y `docencia/` en la raíz,
en paralelo, para que un solo `git subtree push --prefix=apuntes` publique
todas las unidades de una vez):
```
SOM-1SMR-privado/
├── README.md
├── CONTEXTO.md
├── criterios-evaluacion/
│   └── criterios_calificacion.docx
├── docencia/
│   ├── UD01-fundamentos-so/
│   │   └── UD01_docencia.docx
│   ├── UD02-virtualizacion-instalacion/
│   ├── UD03-configuracion-linux/
│   ├── UD04-configuracion-windows/
│   ├── UD05-administracion-linux/
│   └── UD06-administracion-windows/
└── apuntes/
    ├── UD01-fundamentos-so/
    │   ├── UD01_apuntes.docx
    │   ├── UD01_practicas.docx
    │   └── UD01_casos_resueltos.docx
    ├── UD02-virtualizacion-instalacion/
    ├── UD03-configuracion-linux/
    ├── UD04-configuracion-windows/
    ├── UD05-administracion-linux/
    └── UD06-administracion-windows/
```
**Estructura del repo público** (resultado de la publicación, no se edita
directamente ahí):
```
SOM-1SMR-alumnos/
├── UD01-fundamentos-so/
│   ├── UD01_apuntes.docx
│   ├── UD01_practicas.docx
│   └── UD01_casos_resueltos.docx
├── UD02-virtualizacion-instalacion/
...
```
**Configuración inicial (una sola vez), desde la carpeta del repo privado:**
```bash
git remote add publico https://github.com/tu-usuario/SOM-1SMR-alumnos.git
```
**Cada vez que se quiera publicar el estado actual de todos los apuntes:**
```bash
git subtree push --prefix=apuntes publico main
```
Esto empuja el contenido de la carpeta `apuntes/` (con su historial) al
repo público, sin tocar `docencia/`. Es un paso manual y deliberado: nunca
se ejecuta como parte de un commit normal ni de forma automática.
---
## 10. Estado del proyecto
El estado del proyecto (qué está hecho, qué falta, progreso por unidad
didáctica, próximos pasos) ya **no se mantiene en este documento** para
evitar que quede desactualizado — vive en [ESTADO.md](ESTADO.md), que se
actualiza después de cada sesión de trabajo relevante. Este CONTEXTO.md
se queda solo con las decisiones de fondo ("el porqué"), que cambian con
mucha menos frecuencia.
---
## 11. Reglas de trabajo a mantener
- No generar varias unidades a la vez salvo petición expresa.
- No generar prácticas/exámenes/rúbricas automáticamente sin que se pidan.
- Ser crítico ante propuestas del profesor si detecta errores técnicos,
  contenido obsoleto o decisiones pedagógicas mejorables — no dar la razón
  por defecto.
- Preguntar antes de desarrollar una unidad si hay dudas que puedan afectar
  significativamente al resultado; no preguntar si la información ya es
  suficiente.
- Consultar y reutilizar material ya elaborado del proyecto cuando sea
  relevante y esté bien hecho, sin introducir contenido antiguo solo por
  reutilizarlo.
