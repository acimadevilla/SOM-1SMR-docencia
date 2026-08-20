# Propuesta de planificación y ponderación

**Módulo:** Sistemas Operativos Monopuesto · CF Grado Medio Sistemas Microinformáticos y Redes
**Departamento de Informática · IES Medina Azahara**

Este documento recoge, para su discusión y aprobación por el departamento, la propuesta de secuenciación de bloques y la ponderación de Resultados de Aprendizaje (RA) y Criterios de Evaluación (CE) del módulo, adaptada al calendario de FP Dual del centro (inicio de la fase en empresa el 30 de abril).

> **Recordatorio:** la evaluación oficial de RA2 (instalación de sistemas operativos en máquina real) corresponde al tutor/a de empresa. Las actividades de instalación trabajadas en el aula dentro del bloque RA5 refuerzan esa competencia, sobre máquina virtual, pero no sustituyen ni duplican dicha evaluación.

---

## 1. Planificación por bloques

Secuencia acordada: RA1 → RA5 (con refuerzo de RA2) → RA3 Linux → RA3 Windows → RA4 Linux → RA4 Windows. El orden evita instalar los sistemas dos veces: RA5 deja las máquinas virtuales listas y funcionando antes de que RA3 y RA4 las necesiten.

| Orden | Bloque | Horas aprox. | Semanas aprox. |
|---|---|---|---|
| 1 | RA1 — Fundamentos simplificados | 18-20 h | 4 |
| 2 | RA5 — Virtualización + instalación profunda (refuerzo RA2) | 28-30 h | 6 |
| 3 | RA3 — Configuración Linux | 22-25 h | 5 |
| 4 | RA3 — Configuración Windows | 18-20 h | 4 |
| 5 | RA4 — Administración Linux | 25-28 h | 5-6 |
| 6 | RA4 — Administración Windows | 22-25 h | 4-5 |

*Total estimado: ~135-150 h en ~28-30 semanas, a completar antes del 30 de abril.*

---

## 2. Ponderación de Resultados de Aprendizaje (RA)

Ponderación actualmente vigente frente a la propuesta, pendiente de aprobación departamental:

| RA | % actual | % propuesto | Justificación |
|---|---|---|---|
| RA1 | 20% | **15%** | Teoría muy recortada, menos horas dedicadas. |
| RA2 | 15% | **10%** | Evaluación externa (empresa), menor trabajo de aula específico. |
| RA3 | 25% | **25%** | Se mantiene: núcleo práctico central. |
| RA4 | 25% | **30%** | Sube: más horas dedicadas y mayor relevancia profesional directa. |
| RA5 | 15% | **20%** | Sube: asume doble función (virtualización propia + refuerzo de RA2). |

> Pendiente de confirmar con el departamento: el mecanismo exacto de integración de la nota de RA2 (procedente del tutor/a de empresa) en la calificación final del módulo, según la normativa de FP Dual aplicable.

---

## 3. Ponderación de Criterios de Evaluación (CE) dentro de cada RA

Dentro de cada RA, todos sus criterios de evaluación (CE) tienen el mismo peso entre sí. El porcentaje de cada CE se calcula repartiendo a partes iguales el 100% del RA entre su número de criterios.

### RA1 (15%) — Reconoce las características de los sistemas operativos analizando sus elementos y funciones.

> A diferencia del resto de RA, los CE de RA1 no se reparten a partes iguales: se ponderan según lo determinantes que son como prerrequisito de los bloques prácticos posteriores (RA5, RA3, RA4). El sistema de archivos (CE-f) y los permisos (CE-h) se usan de forma constante desde el primer bloque práctico, por lo que suben de peso; procesos (CE-e) y sistemas transaccionales (CE-i) se quedan en un nivel conceptual que no condiciona directamente ninguna práctica posterior, por lo que bajan.

| CE | Criterio de evaluación | % del RA | Justificación |
|---|---|---|---|
| a) | Se han identificado y descrito los elementos funcionales de un sistema informático. | 11% | Base conceptual de toda la unidad. |
| b) | Se ha codificado y relacionado la información en los diferentes sistemas de representación. | 11% | Se enseña junto al CE-h: es su prerrequisito directo. |
| c) | Se han analizado las funciones del sistema operativo. | 11% | Conceptual, necesario para entender b/d/f. |
| d) | Se ha descrito la arquitectura del sistema operativo. | 11% | Da el vocabulario (núcleo, shell, drivers) usado en RA3. |
| e) | Se han identificado los procesos y sus estados. | 8% | Nivel conceptual; se retoma con herramientas reales en RA4. |
| f) | Se ha descrito la estructura y organización del sistema de archivos. | 16% | Prerrequisito directo y constante desde RA5 en adelante. |
| g) | Se han distinguido los atributos de un archivo y un directorio. | 9% | Descriptivo, va a rueda del CE-f. |
| h) | Se han reconocido los permisos de archivos y directorios. | 16% | Prerrequisito directo de RA4 (chmod/chown, NTFS). |
| i) | Se ha constatado la utilidad de los sistemas transaccionales y sus repercusiones al seleccionar un sistema de archivos. | 7% | El que menos condiciona la parte práctica posterior. |

### RA2 (10%) — Instala sistemas operativos, relacionando sus características con el hardware del equipo y el software de aplicación.

> Evaluación oficial a cargo del tutor/a de empresa (FP Dual). Las actividades correspondientes se trabajan en el bloque RA5, sobre máquina virtual, como refuerzo — no sustituyen la evaluación de empresa.

| CE | Criterio de evaluación | % del RA |
|---|---|---|
| a) | Se ha verificado la idoneidad del hardware. | 12,50% |
| b) | Se ha seleccionado el sistema operativo. | 12,50% |
| c) | Se ha elaborado un plan de instalación. | 12,50% |
| d) | Se han configurado parámetros básicos de la instalación. | 12,50% |
| e) | Se ha configurado un gestor de arranque. | 12,50% |
| f) | Se han descrito las incidencias de la instalación. | 12,50% |
| g) | Se han respetado las normas de utilización del software (licencias). | 12,50% |
| h) | Se ha actualizado el sistema operativo. | 12,50% |

### RA3 (25%) — Realiza tareas básicas de configuración de sistemas operativos, interpretando requerimientos y describiendo los procedimientos seguidos.

| CE | Criterio de evaluación | % del RA |
|---|---|---|
| a) | Se han realizado operaciones de arranque y parada del sistema y de uso de sesiones. | 11,11% |
| b) | Se han diferenciado los interfaces de usuario según sus propiedades. | 11,11% |
| c) | Se han aplicado preferencias en la configuración del entorno personal. | 11,11% |
| d) | Se han gestionado los sistemas de archivos específicos. | 11,11% |
| e) | Se han aplicado métodos para la recuperación del sistema operativo. | 11,11% |
| f) | Se ha realizado la configuración para la actualización del sistema operativo. | 11,11% |
| g) | Se han realizado operaciones de instalación/desinstalación de utilidades. | 11,11% |
| h) | Se han utilizado los asistentes de configuración del sistema (acceso a redes, dispositivos, entre otros). | 11,11% |
| i) | Se han ejecutado operaciones para la automatización de tareas del sistema. | 11,12% |

### RA4 (30%) — Realiza operaciones básicas de administración de sistemas operativos, interpretando requerimientos y optimizando el sistema para su uso.

| CE | Criterio de evaluación | % del RA |
|---|---|---|
| a) | Se han configurado perfiles de usuario y grupo. | 11,11% |
| b) | Se han utilizado herramientas gráficas para describir la organización de los archivos del sistema. | 11,11% |
| c) | Se ha actuado sobre los procesos del usuario en función de las necesidades puntuales. | 11,11% |
| d) | Se ha actuado sobre los servicios del sistema en función de las necesidades puntuales. | 11,11% |
| e) | Se han aplicado criterios para la optimización de la memoria disponible. | 11,11% |
| f) | Se ha analizado la actividad del sistema a partir de las trazas generadas por el propio sistema. | 11,11% |
| g) | Se ha optimizado el funcionamiento de los dispositivos de almacenamiento. | 11,11% |
| h) | Se han reconocido y configurado los recursos compartibles del sistema. | 11,11% |
| i) | Se ha interpretado la información de configuración del sistema operativo. | 11,12% |

### RA5 (20%) — Crea máquinas virtuales identificando su campo de aplicación e instalando software específico.

> Incorpora en aula, sobre máquina virtual, las actividades prácticas propias de RA2 (instalación, particionado, arranque, licencias, actualización) como refuerzo.

| CE | Criterio de evaluación | % del RA |
|---|---|---|
| a) | Se ha diferenciado entre máquina real y máquina virtual. | 14,29% |
| b) | Se han establecido las ventajas e inconvenientes de la utilización de máquinas virtuales. | 14,29% |
| c) | Se ha instalado el software libre y propietario para la creación de máquinas virtuales. | 14,29% |
| d) | Se han creado máquinas virtuales a partir de sistemas operativos libres y propietarios. | 14,29% |
| e) | Se han configurado máquinas virtuales. | 14,29% |
| f) | Se ha relacionado la máquina virtual con el sistema operativo anfitrión. | 14,29% |
| g) | Se han realizado pruebas de rendimiento del sistema. | 14,26% |

---

## 4. Estado y próximos pasos

- Aprobación departamental de la ponderación de RA propuesta.
- Confirmación del mecanismo de integración de la nota de RA2 (empresa) en la calificación final.
- Traslado de esta ponderación al documento oficial "Criterios de evaluación y calificación" una vez aprobada.

---

## 5. Mapa de contenidos por bloque, asociados a CE

Propuesta de contenidos para cada bloque de la planificación (apartado 1), con el detalle de qué se trabaja para cada criterio de evaluación. Es un primer nivel de zoom sobre el mapa del módulo: la programación detallada de cada unidad didáctica (secuencia de clases, actividades, prácticas) se desarrollará más adelante, unidad a unidad.

> En RA4 no existe un CE específico de "permisos": he asociado los contenidos de permisos avanzados (chmod/chown en Linux, NTFS con herencia en Windows) al CE-b, por ser el más cercano (organización avanzada de archivos). Si el departamento prefiere asociarlos a otro criterio, se ajusta sin problema.

### Bloque 1 — RA1: Fundamentos simplificados

Secuencia interna de la unidad (UD01), reagrupada por peso como prerrequisito de los bloques prácticos posteriores, no por orden alfabético de CE: el sistema de archivos y los permisos, que se usan de forma constante desde RA5 en adelante, se sitúan como núcleo de la unidad; procesos y sistemas transaccionales, que no condicionan directamente ninguna práctica posterior, quedan como bloques breves de nivel conceptual.

| CE | Contenidos propuestos |
|---|---|
| 1. (a) | El sistema informático y el software: hardware, software, usuarios y su relación; software de base frente a software de aplicación; niveles del sistema informático (hardware → software de base → lenguajes/entornos → software de aplicación → usuario); lenguajes de programación: concepto general y ubicación en el modelo de niveles (máquina, ensamblador, alto nivel), sin sintaxis ni programación real. |
| 2. (c+d) | Funciones y arquitectura del sistema operativo: gestión de procesos, memoria, archivos y entrada/salida (sin algoritmos), organizadas según la arquitectura por capas (núcleo, controladores, shell, aplicaciones); comparación Windows/Linux a alto nivel. |
| 3. (e) | Procesos y sus estados: concepto, sin planificadores ni algoritmos — se retoma con herramientas reales (ps/top, Administrador de tareas) en RA4. |
| 4. (f+g) | Sistema de archivos: organización y atributos. Estructura y jerarquía, rutas, atributos de archivo y directorio en Windows y Linux. |
| 5. (b+h) | Binario/octal aplicado a permisos y unidades de medida de la información: representación binaria y octal enlazada directamente con permisos de archivos y directorios (introducción; se profundiza en el bloque 5-6, RA4); múltiplos del byte según el Sistema Internacional (kilo/mega/giga, base 10) y según la norma IEC 80000-13 (kibi/mebi/gibi, base 2), y cálculo entre ambos — con el caso real de por qué un disco de 500 GB se muestra como ~465 GB al formatearlo. |
| 6. (i) | Sistemas transaccionales: cierre breve — concepto y journaling en ext4/NTFS, y su relevancia al elegir un sistema de archivos. |

*Actividades transversales: identificación de componentes de software en imágenes, calculadora binario-octal aplicada a permisos, exploración de la jerarquía de archivos, clasificación software de base vs. aplicación.*

### Bloque 2 — RA5 (+ refuerzo RA2): Virtualización e instalación

| CE | Contenidos propuestos |
|---|---|
| RA5-a) | Máquina real frente a máquina virtual; tipos de hipervisor (tipo 1 y tipo 2). |
| RA5-b) | Ventajas e inconvenientes de virtualizar. |
| RA5-c) | Instalación de software de virtualización, libre y propietario. |
| RA2-a) | Verificación de idoneidad del hardware (VT-x/AMD-V, RAM, disco). |
| RA2-b) | Selección del sistema operativo según caso de uso. |
| RA2-c) + RA5-d) | Plan de instalación (particionado, disco, red de la VM) y creación de máquinas virtuales a partir de sistemas operativos libres y propietarios. |
| RA2-d) | Parámetros básicos de la instalación. |
| RA2-e) | Gestor de arranque, incluyendo dual boot. |
| RA2-f) | Incidencias típicas de la instalación. |
| RA2-g) | Licencias: software libre frente a propietario. |
| RA2-h) | Actualización post-instalación. |
| RA5-e) | Configuración de la VM: recursos, snapshots, red. |
| RA5-f) | Relación VM-anfitrión: carpetas compartidas, red NAT/bridge. |
| RA5-g) | Pruebas de rendimiento básicas: arranque, disco, VM frente a anfitrión. |

*Ampliación no evaluable: introducción a Docker (diferencia entre máquina virtual y contenedor).*

### Bloque 3 — RA3 Linux: Configuración

| CE | Contenidos propuestos |
|---|---|
| a) | Operaciones de arranque y parada del sistema, y uso de sesiones: proceso de arranque (GRUB, systemd), gestión de sesiones. |
| b) | Interfaces de usuario: línea de comandos frente a entorno gráfico. |
| c) | Preferencias en la configuración del entorno personal: personalización del escritorio. |
| d) | Sistemas de archivos específicos: ext4, fstab. |
| e) | Recuperación del sistema operativo: modo rescate, reparación de GRUB. |
| f) | Configuración para la actualización del sistema operativo: APT/DNF. |
| g) | Instalación/desinstalación de utilidades: paquetes .deb/.rpm. |
| h) | Asistentes de configuración del sistema: acceso a redes, dispositivos. |
| i) | Automatización de tareas del sistema: cron/at, scripts básicos sin bucles complejos. |

### Bloque 4 — RA3 Windows: Configuración

| CE | Contenidos propuestos |
|---|---|
| a) | Operaciones de arranque y parada del sistema, y uso de sesiones: opciones avanzadas de arranque, sesiones locales. |
| b) | Interfaces de usuario: Configuración frente a Panel de control, PowerShell frente a CMD. |
| c) | Preferencias en la configuración del entorno personal: personalización. |
| d) | Sistemas de archivos específicos: Administrador de discos, NTFS. |
| e) | Recuperación del sistema operativo: WinRE, Restaurar sistema. |
| f) | Configuración para la actualización del sistema operativo: Windows Update. |
| g) | Instalación/desinstalación de utilidades: instaladores, Microsoft Store, winget. |
| h) | Asistentes de configuración del sistema: acceso a redes, dispositivos. |
| i) | Automatización de tareas del sistema: Programador de tareas, PowerShell básico. |

### Bloque 5 — RA4 Linux: Administración

| CE | Contenidos propuestos |
|---|---|
| a) | Perfiles de usuario y grupo: useradd, /etc/passwd, gestión de grupos. |
| b) | Herramientas gráficas y organización avanzada de archivos: gestores de archivos gráficos, permisos avanzados (chmod, chown). |
| c) | Procesos del usuario: ps, top, kill, nice. |
| d) | Servicios del sistema: systemctl, journal. |
| e) | Optimización de la memoria disponible: free, swap. |
| f) | Actividad del sistema a partir de trazas: /var/log, journalctl. |
| g) | Optimización de dispositivos de almacenamiento: df, du. |
| h) | Recursos compartibles del sistema: Samba/NFS básico. |
| i) | Información de configuración del sistema: archivos de configuración en /etc. |

### Bloque 6 — RA4 Windows: Administración

| CE | Contenidos propuestos |
|---|---|
| a) | Perfiles de usuario y grupo: lusrmgr.msc. |
| b) | Herramientas gráficas y organización avanzada de archivos: Explorador de archivos, permisos NTFS con herencia. |
| c) | Procesos del usuario: Administrador de tareas. |
| d) | Servicios del sistema: services.msc. |
| e) | Optimización de la memoria disponible: Administrador de tareas, Monitor de recursos. |
| f) | Actividad del sistema a partir de trazas: Visor de eventos. |
| g) | Optimización de dispositivos de almacenamiento: TRIM, Liberador de espacio en disco. |
| h) | Recursos compartibles del sistema: recursos compartidos en red (permisos NTFS + permisos de red). |
| i) | Información de configuración del sistema: msinfo32, registro básico. |
