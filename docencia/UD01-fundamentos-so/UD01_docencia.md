# UD01 — Fundamentos del sistema operativo (Docencia)

**Módulo:** Sistemas Operativos Monopuesto · 1º SMR
**RA cubierto:** RA1 — *Reconoce las características de los sistemas operativos analizando sus elementos y funciones* (15% de la nota del módulo)
**CE cubiertos:** a, b, c, d, e, f, g, h, i (los 9 de RA1)
**Duración orientativa:** 18-20 h · 4 semanas (a 5 h/semana)
**Prerrequisitos:** ninguno — es la primera unidad del curso.
**Con qué conecta después:** esta unidad no se evalúa de forma aislada. El sistema de archivos (epígrafe 4) y los permisos (epígrafe 5) se usan de forma constante desde RA5 (instalación y particionado de VMs) y son prerrequisito directo de RA4 (administración con `chmod`/`chown` y permisos NTFS). La arquitectura por capas (epígrafe 2) da el vocabulario —núcleo, shell, controladores— que se reutiliza al explicar GRUB/systemd en RA3 Linux y el arranque de Windows en RA3 Windows.

> Ver la ponderación interna de cada CE y su justificación en [1SMR-SOM-Propuesta_planificacion_y_ponderacion.md](../../criterios-evaluacion/1SMR-SOM-Propuesta_planificacion_y_ponderacion.md).

---

## Objetivos generales de la unidad

Al terminar UD01 el alumnado debe ser capaz de:

- Explicar qué es un sistema informático y situar el sistema operativo dentro de él, distinguiendo software de base y software de aplicación.
- Describir, sin necesidad de algoritmos, qué hace un sistema operativo y cómo se organiza por capas.
- Reconocer que un proceso no es lo mismo que un programa, y nombrar sus estados básicos.
- Moverse conceptualmente por la jerarquía de archivos de Windows y de Linux, y reconocer los atributos de archivos y directorios.
- Convertir entre binario, octal y decimal en la medida necesaria para interpretar permisos, y leer/escribir una notación de permisos tipo `rwx` / `755`.
- Calcular múltiplos del byte en el Sistema Internacional (kilo/mega/giga) y en la norma IEC 80000-13 (kibi/mebi/gibi), y explicar por qué un disco anunciado como "500 GB" se muestra como "~465 GB" al formatearlo.
- Explicar por qué existen los sistemas de archivos transaccionales (journaling) y qué problema resuelven.

**Idea fuerza de la unidad:** todo lo que se explica aquí es vocabulario y base conceptual que se va a usar constantemente a partir de RA5. Conviene decírselo explícitamente al alumnado desde la primera sesión — motiva mucho más "esto lo vas a necesitar dentro de tres semanas para instalar tu propia VM" que "esto entra en el examen".

---

## Orden de la unidad y por qué

La secuencia **no sigue el orden alfabético de los CE** (a, b, c...) sino su peso como prerrequisito de lo que viene después:

| # | Epígrafe | CE | Horas aprox. | Peso en RA1 |
|---|---|---|---|---|
| 1 | El sistema informático y el software | a | 2 h | 11% |
| 2 | Funciones y arquitectura del SO | c + d | 3 h | 22% |
| 3 | Procesos y sus estados | e | 1,5 h | 8% |
| 4 | Sistema de archivos: organización y atributos | f + g | 4 h | 25% |
| 5 | Binario/octal aplicado a permisos y unidades de medida | b + h | 5 h | 27% |
| 6 | Sistemas transaccionales | i | 1 h | 7% |
| — | Caso práctico integrador + resumen + repaso | todos | 2-3 h | — |

Los epígrafes 4 y 5 concentran más de la mitad del peso de la unidad porque son los que el alumnado va a usar de verdad en cuanto empiece a tocar máquinas virtuales. Los epígrafes 3 y 6 se quedan deliberadamente en un nivel conceptual ligero — no hay que alargarlos por "sensación de que falta contenido": su profundidad real llega en RA4.

---

## Epígrafe 1 — El sistema informático y el software (CE-a)

**Duración:** 2 h · **Peso:** 11%

### Guion de clase

1. **Arranque de la sesión (10 min):** pregunta abierta a la clase: "¿qué es un ordenador?". Dejar que respondan con lo que ya saben (probablemente hablarán de hardware: CPU, RAM, disco). Anotar en la pizarra sus respuestas sin corregir todavía.
2. **Concepto de sistema informático (20 min):** cerrar la idea de que un sistema informático es hardware + software + usuarios, y que los tres se necesitan mutuamente — el hardware sin software es inerte, el software sin hardware no se ejecuta, y ambos sin un usuario u otro sistema que los use no tienen propósito. Aquí es donde se corrige la idea inicial de "ordenador = hardware" que casi siempre sale en el punto 1.
3. **Software de base vs. software de aplicación (25 min):** explicar la diferencia con ejemplos que el alumnado reconozca (Windows/Linux, controladores de la tarjeta gráfica, antivirus → software de base; Word, un navegador, un videojuego → software de aplicación). Insistir en que el software de base existe para que el de aplicación pueda funcionar sin tener que hablar directamente con el hardware.
4. **Niveles del sistema informático (30 min):** presentar el modelo de capas (hardware → software de base → lenguajes/entornos → software de aplicación → usuario). Dibujarlo en la pizarra como pirámide o como capas concéntricas — funciona mejor visualmente que como lista.
5. **Lenguajes de programación, solo para situar el nivel (20 min):** explicar que existen lenguaje máquina, ensamblador y lenguajes de alto nivel, y **dónde encajan** en el modelo de capas (entre el software de base y el de aplicación). **No enseñar sintaxis ni hacer que programen nada** — el objetivo es que entiendan que "cuando alguien programa una aplicación, el resultado final baja varios niveles hasta convertirse en instrucciones que la CPU entiende", no que sepan programar.
6. **Cierre y actividad (15 min):** clasificación de software en imágenes/capturas de pantalla (ver práctica).

### Contexto para el profesorado (no necesariamente para el alumnado)

Este epígrafe sustituye al antiguo desglose de hardware por componentes, que ahora se cubre en el módulo de Montaje y Mantenimiento — **no hay que reintroducirlo aquí**, ni siquiera como repaso, salvo que surja de forma espontánea y sirva para anclar un concepto (por ejemplo, si alguien pregunta "¿y la BIOS/UEFI en qué nivel está?", es una buena pregunta y merece respuesta, pero no hay que planificar una sesión sobre firmware).

Sobre los niveles del lenguaje: si al alumnado le suena de algo será por otro módulo o por cultura general de gaming/tecnología. No hace falta profundizar en compiladores vs. intérpretes salvo que la pregunta salga sola — si sale, una explicación de una frase basta ("un compilador traduce todo el programa de una vez antes de ejecutarlo, un intérprete lo traduce línea a línea mientras se ejecuta").

### Errores conceptuales frecuentes

- **"El ordenador es el hardware, el software es un añadido."** Es la confusión más común en este punto del curso. Se corrige bien con la analogía de que el hardware sin sistema operativo es como un coche sin conductor ni gasolina: existe, pero no hace nada útil por sí solo.
- **Confundir sistema operativo con interfaz gráfica.** Algún alumno dirá "yo no tengo sistema operativo, tengo Windows" sin darse cuenta de que Windows *es* el sistema operativo. Aprovechar para introducir de pasada (sin desarrollarlo, eso es el epígrafe 2) que el SO incluye mucho más que lo que se ve en pantalla.
- **Pensar que "software de base" significa "software antiguo" o "software del sistema operativo únicamente".** Los controladores y ciertas utilidades (por ejemplo, un gestor de particiones) también son software de base aunque no formen parte del SO en sí.

### Preguntas frecuentes del alumnado

- *"¿El antivirus es software de base o de aplicación?"* — Depende de cómo se mire, pero para este curso: se considera software de base porque opera a bajo nivel y da soporte al resto del sistema, aunque el usuario lo perciba como una aplicación más. Es una buena pregunta para matizar que la frontera no siempre es nítida.
- *"¿Para qué necesito saber esto si solo quiero instalar un Windows?"* — Porque cuando en unas semanas se instale un sistema operativo de verdad (RA5), va a tener que decidir entre software libre y propietario, entender qué son los controladores que el instalador pide, y distinguir qué parte de lo que ve es el sistema operativo y qué parte son aplicaciones que se instalan encima.

### Actividad / práctica

**Enunciado (para el alumnado):** a partir de 10-12 capturas de pantalla o fotos (gestor de tareas de Windows, terminal de Linux, una placa base, una ventana de Word, el BIOS/UEFI, un smartphone, un router, un IDE de programación, una consola de videojuegos, una tarjeta gráfica, un instalador de un programa, un servicio en segundo plano), el alumnado debe clasificar cada elemento como: hardware / software de base / software de aplicación, y justificar brevemente cada respuesta en una frase.

**Solución orientativa y qué mirar al corregir:**
- No penalizar respuestas dudosas si la justificación es coherente (por ejemplo, un IDE de programación se puede defender como aplicación "para el programador" — lo importante es que sepan argumentarlo).
- Vigilar especialmente el caso del router/firmware y el antivirus: son los que más dudas generan y sirven para detectar si el concepto ha calado o se ha quedado en la superficie.
- Si un alumno clasifica el sistema operativo como "hardware", es señal de que el epígrafe no ha calado y conviene repasarlo individualmente antes de seguir.

### Curiosidades / para ampliar si sobra tiempo

- El término "software" lo acuñó el estadístico John Tukey en 1958, como contraposición a "hardware" (que ya se usaba para referirse a la ferretería/herramientas mucho antes de la informática).
- Ejemplo real de los niveles: cuando alguien escribe una app en Python, ese código pasa por un intérprete (CPython) que lo traduce a bytecode, que a su vez se ejecuta sobre una máquina virtual que finalmente genera instrucciones que la CPU entiende. Son varios niveles solo para ese ejemplo — sirve para que vean que el modelo de capas no es una simplificación artificial de clase, es como funciona de verdad.

---

## Epígrafe 2 — Funciones y arquitectura del sistema operativo (CE-c + CE-d)

**Duración:** 3 h · **Peso:** 22%

### Guion de clase

1. **Recordatorio y enganche (10 min):** retomar el modelo de capas del epígrafe 1 y preguntar: "¿qué hace exactamente esa capa de software de base que llamamos sistema operativo?".
2. **Las cuatro grandes funciones del SO (45 min):** gestión de procesos, gestión de memoria, gestión de archivos, gestión de entrada/salida. Para cada una: qué problema resuelve y un ejemplo cotidiano. **Sin algoritmos ni cálculos de particiones/paginación** — el objetivo es que sepan que el SO "reparte la CPU entre procesos", "organiza la RAM para que las aplicaciones no se pisen", "da acceso ordenado al disco" y "media entre las aplicaciones y los periféricos", no que sepan calcular cómo lo hace.
3. **Arquitectura por capas (45 min):** núcleo (kernel), controladores (drivers), shell, aplicaciones. Dibujar el esquema de capas concéntricas (núcleo en el centro, aplicaciones en el exterior) y relacionarlo explícitamente con el modelo de niveles del epígrafe 1 — es la misma idea aplicada específicamente al sistema operativo.
4. **Comparativa Windows/Linux a alto nivel (45 min):** sin entrar en tipos de kernel en profundidad (monolítico, microkernel, híbrido) salvo como nota breve, mostrar que ambos sistemas comparten esta misma arquitectura por capas aunque la implementen de forma distinta. Usar una tabla comparativa en pantalla (núcleo Linux vs. núcleo NT, shell bash/PowerShell vs. cmd, gestores de paquetes vs. instaladores .exe/.msi).
5. **Cierre (15 min):** repaso rápido oral, encadenando: "¿qué capa falla si no reconoce mi impresora?" (drivers), "¿qué capa uso cuando escribo comandos?" (shell), etc.

### Contexto para el profesorado

Sobre el kernel: merece la pena mencionar, aunque sea en una frase, que Linux usa un núcleo monolítico (aunque modular, con módulos que se cargan y descargan en caliente) y que Windows NT usa un núcleo híbrido. No hace falta desarrollarlo como contenido evaluable — es cultura técnica que ayuda a que la comparativa Windows/Linux no quede plana, y probablemente surgirá si algún alumno ha oído hablar de microkernels o de proyectos como GNU Hurd.

Es un buen momento para sembrar, sin desarrollarlo, que "el sistema operativo reparte la CPU entre procesos" es una función que en RA1 se queda en lo conceptual, pero que en RA4 van a ver herramientas reales (`top`, Administrador de tareas) que muestran ese reparto en vivo. Decirlo explícitamente ayuda a que no sientan que "esto no vale para nada práctico".

### Errores conceptuales frecuentes

- **Creer que el kernel es "todo el sistema operativo".** Es habitual que, tras ver el esquema de capas, algunos entiendan que el núcleo y el sistema operativo son sinónimos. Conviene remarcar que el SO es el conjunto de todas las capas de software de base, y el núcleo es solo la más interna (la que habla directamente con el hardware).
- **Pensar que los drivers los "hace" el sistema operativo.** Muchos alumnos no saben que los controladores suelen venir del fabricante del hardware, no del sistema operativo, y que el SO simplemente define cómo debe comunicarse un driver con él.
- **Confundir shell con sistema operativo.** Sobre todo entre quienes ya han visto una terminal antes: piensan que "bash es Linux" o "PowerShell es Windows". Es el momento de dejar claro que el shell es solo una capa más, intercambiable (se puede usar zsh en vez de bash, o cmd en vez de PowerShell) sin cambiar de sistema operativo.

### Preguntas frecuentes del alumnado

- *"¿Por qué Windows no deja tocar el núcleo y Linux sí?"* — Ambos protegen el núcleo del acceso directo de las aplicaciones de usuario (por seguridad y estabilidad), pero Linux, al ser de código abierto, permite inspeccionar y modificar el propio código fuente del núcleo, cosa que con Windows no es posible salvo con herramientas y permisos muy específicos que quedan fuera del alcance de este módulo.
- *"¿Se puede tener varios núcleos en un mismo ordenador?"* — Aquí conviene distinguir "núcleo del sistema operativo" (kernel) de "núcleo de la CPU" (core), que es una confusión de vocabulario muy habitual a esta edad por el marketing de procesadores ("procesador de 8 núcleos"). Merece una aclaración explícita aunque no esté prevista en el guion, porque si no se aclara arrastra el malentendido durante el resto del curso.

### Actividad / práctica

**Enunciado:** tabla comparativa Windows/Linux a completar por parejas, con columnas: elemento (núcleo, shell, gestor de paquetes/instaladores, drivers) y una fila para "qué hace" y otra para "ejemplo en Windows"/"ejemplo en Linux". Después, puesta en común oral.

**Solución orientativa:**

| Elemento | Qué hace | Windows | Linux |
|---|---|---|---|
| Núcleo | Gestiona hardware, procesos, memoria a bajo nivel | Núcleo NT (híbrido) | Núcleo Linux (monolítico modular) |
| Shell | Interfaz de línea de comandos | CMD / PowerShell | bash / zsh |
| Gestión de software | Instalación y actualización de programas | Instaladores .exe/.msi, Microsoft Store, winget | Gestores de paquetes (APT, DNF) |
| Controladores | Comunican el SO con dispositivos concretos | Suministrados por el fabricante, instalados vía Windows Update o manualmente | Suministrados por el fabricante o integrados en el propio núcleo |

**Qué mirar al corregir:** el error más informativo es que confundan "shell" con "sistema operativo" en la columna de "qué hace" — es la señal más clara de que el epígrafe necesita repaso antes de seguir a RA3, donde esta distinción es constante.

### Curiosidades

- El núcleo Linux se originó en 1991 como proyecto personal de Linus Torvalds, entonces estudiante, y hoy es uno de los proyectos de software colaborativo más grandes del mundo — sigue creciendo y aceptando contribuciones de miles de desarrolladores.
- Windows NT (la base de todos los Windows modernos, desde XP hasta 11) no viene de MS-DOS, como mucha gente cree: se diseñó desde cero en los 90, con influencia directa de VMS, otro sistema operativo anterior en el que trabajó parte del mismo equipo de ingenieros.

---

## Epígrafe 3 — Procesos y sus estados (CE-e)

**Duración:** 1,5 h · **Peso:** 8%

### Guion de clase

1. **Diferenciar programa y proceso (25 min):** un programa es código almacenado (un archivo en disco); un proceso es ese programa en ejecución, con recursos asignados (memoria, tiempo de CPU). Ejemplo claro: puedo tener un solo archivo `chrome.exe` (un programa) y sin embargo varios procesos de Chrome ejecutándose a la vez (una pestaña, una extensión, el proceso principal...).
2. **Estados básicos de un proceso (30 min):** nuevo, listo, en ejecución, bloqueado, terminado. Explicar cada transición con un ejemplo (un proceso que espera datos del disco pasa a "bloqueado"; cuando el disco responde, vuelve a "listo").
3. **Qué NO se ve aquí, y por qué (10 min):** decir explícitamente que no se van a estudiar algoritmos de planificación (quién decide qué proceso se ejecuta cuándo). Mencionar solo el nombre de lo que usan los sistemas actuales (CFS/vruntime en Linux, Thread Director en CPUs híbridas de Windows 11) sin entrar en cómo funcionan — es una frase, no un contenido a desarrollar.
4. **Cierre con anticipo de RA4 (10 min):** mostrar en pantalla, sin profundizar, el Administrador de tareas de Windows o `top` en Linux, señalando que eso es "un proceso real en uno de los estados que acabamos de ver" — crea expectativa para RA4 sin adelantar contenido de esa unidad.

### Contexto para el profesorado

Este es uno de los dos epígrafes deliberadamente breves de la unidad (junto con el 6). No hay que alargarlo con contenido de planificación "porque parece que falta algo" — es una decisión curricular explícita de este curso, justificada porque el uso práctico real de este conocimiento llega con herramientas de verdad en RA4, no aquí.

### Errores conceptuales frecuentes

- **Confundir programa y proceso**, usando ambos términos como sinónimos. Es el error más importante de corregir en este epígrafe porque arrastra confusión hasta RA4.
- **Pensar que un proceso "bloqueado" está "colgado" o "roto".** Bloqueado es un estado normal y temporal (esperando un recurso), no un fallo.

### Preguntas frecuentes del alumnado

- *"¿Cuántos procesos hay ejecutándose a la vez en mi ordenador?"* — Buena pregunta para mostrar en pantalla (Administrador de tareas / `ps aux`) que son varias decenas o cientos, muchos más de los que el usuario percibe, y que la mayoría son del propio sistema operativo, no aplicaciones abiertas por el usuario.

### Actividad / práctica

**Enunciado:** dado un escenario breve por escrito ("abres tu navegador, escribes una URL y pulsas Enter; el navegador pide datos a Internet y espera la respuesta; la respuesta llega y la página se renderiza en pantalla"), el alumnado debe identificar en qué estado está el proceso del navegador en cada momento de la secuencia.

**Solución:** nuevo (al abrir el navegador) → listo/ejecución (mientras procesa la URL) → bloqueado (esperando la respuesta de Internet) → listo/ejecución (al recibir los datos y renderizar).

**Qué mirar al corregir:** que distingan bien el momento de "bloqueado" — es el punto donde más se equivocan, a menudo diciendo "terminado" o "en ejecución" cuando en realidad el proceso está esperando un recurso externo.

---

## Epígrafe 4 — Sistema de archivos: organización y atributos (CE-f + CE-g)

**Duración:** 4 h · **Peso:** 25%

### Guion de clase

1. **Por qué necesitamos un sistema de archivos (15 min):** plantear la pregunta "si guardo un archivo, ¿dónde está exactamente?" para introducir que el sistema de archivos es la estructura que organiza y localiza la información en el almacenamiento — sin él, el disco sería un espacio de bytes sin ningún orden.
2. **Jerarquía de directorios: Windows (35 min):** unidades con letra (C:\, D:\...), estructura de carpetas típica (`Usuarios`, `Archivos de programa`, `Windows`), rutas absolutas y relativas, separador `\`.
3. **Jerarquía de directorios: Linux (45 min):** raíz única `/`, sin letras de unidad — los discos se "montan" dentro del árbol de directorios. Recorrido de los directorios principales (`/home`, `/etc`, `/var`, `/bin`, `/usr`...) con qué contiene cada uno, en pizarra o en una VM ya preparada si se dispone de una para demostración. Separador `/`.
4. **Comparativa directa y el punto que más falla: sensibilidad a mayúsculas (30 min):** Windows no distingue mayúsculas de minúsculas en nombres de archivo (`Documento.txt` y `documento.txt` son el mismo archivo); Linux sí (son dos archivos distintos). **Este es, con diferencia, el error práctico más habitual cuando el alumnado empiece a trabajar con Linux en RA3** — merece tiempo y algún ejemplo en vivo si hay acceso a una terminal.
5. **Atributos de archivos y directorios (45 min):** en Windows (solo lectura, oculto, sistema, archivo listo para archivar) y en Linux (oculto mediante el punto inicial `.archivo`, y una introducción de que existen otros atributos gestionables con `chattr` sin entrar en detalle). Mostrar en pantalla cómo se ven en el explorador de Windows y con `ls -la` en Linux.
6. **Cierre (10 min):** actividad de exploración guiada.

### Contexto para el profesorado

Esta es una de las dos sesiones "pesadas" de la unidad y conviene tratarla así en tiempo — no comprimirla. La sensibilidad a mayúsculas de Linux es, según la experiencia de cursos anteriores, la causa más frecuente de "el comando no funciona" en las primeras prácticas de RA3, y se corrige mucho mejor si se planta aquí, con calma, que sobre la marcha en mitad de una práctica de terminal.

Sobre el montaje de discos en Linux: no hace falta profundizar en `/etc/fstab` ni en el proceso de montaje en sí (eso es RA3), basta con que entiendan la idea de que "un disco o partición nueva aparece como una carpeta más dentro del árbol, no como una letra nueva".

### Errores conceptuales frecuentes

- **Pensar que en Linux "no hay discos con letra" porque "todo es una carpeta".** Hay que aclarar que sí hay discos y particiones distintas, simplemente no se representan con una letra sino que se integran en el árbol único mediante puntos de montaje.
- **Olvidar la sensibilidad a mayúsculas de Linux** — no es tanto un error conceptual como una costumbre que hay que crear activamente, porque toda la experiencia previa del alumnado con Windows la contradice.
- **Confundir "oculto" con "protegido" o "seguro".** Un archivo oculto en Windows o Linux no está protegido de ningún modo especial, solo no se muestra por defecto — es buen momento para desmontar la falsa sensación de seguridad que da ocultar un archivo.

### Preguntas frecuentes del alumnado

- *"¿Por qué Linux no usa letras como C: o D:?"* — Herencia del diseño de Unix: un único árbol de directorios simplifica la forma de referirse a cualquier archivo del sistema, sin importar en qué disco físico esté realmente guardado.
- *"¿Si cambio de mayúsculas el nombre de una carpeta en Linux, se rompe algo?"* — No en sí misma, pero cualquier script, acceso directo o programa que la referencie con el nombre anterior dejará de encontrarla — es un buen gancho para explicar por qué en entornos profesionales se evita cambiar nombres de carpetas del sistema.

### Actividad / práctica

**Enunciado (parte 1, sin equipo, con dibujo/esquema):** dado un fragmento de árbol de directorios de Linux, el alumnado debe escribir la ruta absoluta y una ruta relativa posible a un archivo concreto marcado en el esquema.

**Enunciado (parte 2, con equipo o capturas):** identificar, en una serie de nombres de archivo, cuáles corresponden al mismo archivo en Windows y cuáles serían archivos distintos en Linux (ejemplo: `Informe.docx` / `informe.docx` / `INFORME.docx`).

**Solución orientativa:** en Windows, los tres nombres del ejemplo son el mismo archivo; en Linux, son tres archivos distintos.

**Qué mirar al corregir:** en la parte 1, el fallo más habitual es escribir la ruta relativa mal calculada respecto al directorio de partida indicado en el enunciado — conviene repasarlo con quien falle esto, porque es exactamente lo que van a necesitar para moverse por terminal en RA3. En la parte 2, cualquier alumno que diga que los tres nombres son "el mismo archivo" en Linux necesita repaso directo de este punto antes de continuar.

### Curiosidades

- El árbol de directorios de Linux sigue en gran medida el *Filesystem Hierarchy Standard* (FHS), un estándar público que explica por qué `/etc` guarda configuración, `/var` guarda datos que cambian (logs, colas...) y `/usr` guarda programas — mencionarlo de pasada ayuda a que no parezca una convención arbitraria.

---

## Epígrafe 5 — Binario/octal aplicado a permisos y unidades de medida (CE-b + CE-h)

**Duración:** 5 h · **Peso:** 27%

### Guion de clase

1. **Por qué el ordenador usa binario (15 min):** un transistor tiene dos estados (encendido/apagado), y esa es la razón física de fondo, no una elección arbitraria. Conectar con lo ya visto: esto es representación de la información, no aritmética por aritmética.
2. **Sistema binario: conversión básica (40 min):** de decimal a binario y de binario a decimal, con números pequeños (0-255, un byte). No hay que llegar a operaciones aritméticas en binario (sumas, restas) — el objetivo es leer y convertir, no calcular con binario.
3. **Unidades de medida de la información: SI frente a IEC 80000-13 (30 min):** el byte como unidad base, y sus múltiplos según dos normas distintas: el Sistema Internacional (kilo, mega, giga... en base 10, potencias de 1000) y la norma **IEC 80000-13** —heredera de la antigua IEC 60027-2— que define los prefijos binarios (kibi, mebi, gibi... en base 2, potencias de 1024) precisamente para no confundir ambos sistemas. Cálculo de conversión entre ambos con un par de ejemplos numéricos sencillos.
4. **El caso real: por qué un disco de 500 GB se queda en ~465 GB (20 min):** ver más abajo el desarrollo completo del ejemplo. Es el momento de conectar la teoría de múltiplos con algo que el alumnado va a comprobar por sí mismo en cuanto empiece a particionar discos en RA5.
5. **Sistema octal y por qué nos interesa aquí (30 min):** convertir binario a octal agrupando en bloques de 3 bits, y explicar **la razón real de que se use octal para permisos**: un permiso rwx son exactamente 3 bits (activado/desactivado cada uno), así que un dígito octal representa exactamente un conjunto de permisos completo. Esto es el "por qué" que conecta ambos contenidos y por eso se enseñan juntos.
6. **Permisos de archivos y directorios: introducción (60 min):** en Linux, los tres conjuntos de permisos (propietario, grupo, otros) y los tres tipos (lectura, escritura, ejecución), su representación simbólica (`rwxr-xr--`) y numérica (`754`). Mostrar con `ls -la` en una VM o captura. Introducir brevemente que Windows también tiene permisos (NTFS) pero con un modelo distinto (listas de control de acceso, ACL) que se verá en profundidad en RA4 — aquí solo se menciona que existen y que son más granulares.
7. **De binario a permiso real: ejercicio guiado en la pizarra (40 min):** coger un número octal (por ejemplo, 640) y descomponerlo en binario, y de ahí a qué puede hacer cada conjunto de usuarios. Hacerlo al revés también: dado un `rw-r-----`, obtener el octal.
8. **Cierre (5 min):** enlazar con RA4 y con RA5: "esto que acabáis de aprender sobre permisos es lo que vais a usar con `chmod`; lo de los múltiplos del byte es lo que os va a explicar por qué el disco que le asignéis a una VM nunca coincide exactamente con el número que hayáis escrito".

### El caso real: el disco de 500 GB que se queda en ~465 GB

Este es el ejemplo que conviene desarrollar despacio en la pizarra, porque resume por qué hacen falta las dos normas:

- Los **fabricantes de discos** anuncian la capacidad en el Sistema Internacional, en base 10: un disco "de 500 GB" tiene exactamente 500 × 10⁹ = 500.000.000.000 bytes. Esto no es un truco de marketing malintencionado — es una convención de la industria del almacenamiento, coherente con el resto de unidades del SI (igual que 1 km son 1000 m, no 1024).
- Los **sistemas operativos**, en cambio, calculan y muestran la capacidad en base 2, contando en potencias de 1024 — pero durante décadas la han etiquetado, por error histórico, con el mismo nombre "GB" que corresponde al SI. Lo que realmente se está mostrando es GiB (gibibytes), no GB.
- Al convertir esos 500.000.000.000 bytes a GiB: 500.000.000.000 ÷ 1024³ = 500.000.000.000 ÷ 1.073.741.824 ≈ **465,7 GiB**, que el sistema operativo etiqueta (mal, pero es lo habitual) como "465 GB".

No se ha perdido ningún dato ni el fabricante ha "engañado": son exactamente los mismos bytes, contados con dos reglas distintas para agruparlos. Merece la pena remarcar que sistemas operativos más recientes (algunas versiones de macOS, por ejemplo) ya muestran GB en base 10 de verdad, coincidiendo con el fabricante — lo cual, irónicamente, genera la confusión inversa cuando el alumnado compara capturas de pantalla de sistemas distintos.

### Contexto para el profesorado

Este es el epígrafe con más peso de toda la unidad, y con razón: es el único contenido de RA1 que se va a usar de forma **literal y directa** en RA4 (no solo como base conceptual), y el bloque de múltiplos del byte es el que más "aja, ahora lo entiendo" suele generar, porque es una confusión que casi todo el alumnado ha vivido sin saber por qué ocurría.

La clave pedagógica de este epígrafe es que **CE-b y CE-h no son dos temas distintos que coinciden en la misma sesión**: son la misma idea, ligada desde el principio. Enseñar binario/octal como aritmética abstracta y solo semanas después (en RA4) aplicarlo a permisos es la razón principal por la que, en cursos anteriores, buena parte del alumnado llegaba a RA4 sin recordar cómo convertir a octal. Al enseñarlo junto con su aplicación inmediata, la conversión deja de ser "matemáticas sin sentido" y pasa a ser "la herramienta que necesito para leer `chmod 755`". Lo mismo aplica a los múltiplos del byte: no es una curiosidad aislada, es la explicación de algo que van a ver con sus propios ojos en RA5.

No hace falta enseñar hexadecimal en este punto — no es necesario para permisos y añadiría carga sin beneficio práctico en esta unidad. Tampoco hace falta memorizar la norma IEC 80000-13 por su nombre ni su histórico (viene de la antigua IEC 60027-2, de 1998-2005) — basta con que sepan que existe una norma internacional específica para los prefijos binarios y por qué hizo falta crearla.

### Errores conceptuales frecuentes

- **Intentar memorizar la tabla de conversión en vez de entender el mecanismo.** Es el error más costoso a medio plazo: memorizar "755 = rwxr-xr-x" sin saber por qué hace que cualquier combinación no memorizada (por ejemplo 640) los deje bloqueados. Insistir siempre en el método (binario → agrupar en 3 → octal), no en la memorización de casos.
- **Olvidar que hay tres conjuntos de permisos, no uno.** Es habitual que, al principio, piensen en "los permisos del archivo" en genérico, sin distinguir propietario/grupo/otros.
- **Confundir permiso de ejecución con "se puede abrir".** En un directorio, el permiso de ejecución significa "se puede *entrar* en él" (acceder a su contenido), no "ejecutarlo" como si fuera un programa — es una fuente de confusión constante y merece una aclaración explícita.
- **Pensar que GB y GiB son "casi lo mismo, da igual".** La diferencia es pequeña en porcentaje a escala de kilobyte (un 2,4%) pero crece con cada múltiplo (un 7% en giga, casi un 10% en tera) — suficiente para generar confusión real al planificar el tamaño de discos y particiones en RA5.

### Preguntas frecuentes del alumnado

- *"¿Por qué no se usa hexadecimal si también agrupa bits?"* — Buena pregunta técnica: hexadecimal agrupa de 4 en 4 bits, y un permiso son exactamente 3 bits, así que no encaja limpiamente; octal, al agrupar de 3 en 3, representa un conjunto de permisos completo en un solo dígito.
- *"¿Y en Windows también hay algo como 755?"* — No exactamente: NTFS usa permisos más granulares y no se resumen con la misma notación numérica. La equivalencia conceptual (quién puede leer/escribir/ejecutar) sí existe, pero el mecanismo es diferente y se verá en RA4 Windows.
- *"¿Entonces me han estafado al venderme un disco de 500 GB?"* — No: son exactamente los bytes que se anuncian, contados en base 10 tal y como marca el SI. Lo que ocurre es que el sistema operativo los muestra contados en base 2 (GiB) pero etiquetados como si fueran GB — es un problema de etiquetado heredado históricamente, no de cantidad real de bytes.
- *"¿Y con la RAM pasa lo mismo?"* — Al revés: la memoria RAM se fabrica físicamente en potencias de 2 (por su propio diseño en circuitos), así que ahí no hay discrepancia entre lo que anuncia el fabricante y lo que muestra el sistema — es una buena pregunta para remarcar que el problema del disco es una cuestión de convención de medida, no un fenómeno universal de todo el hardware.

### Actividad / práctica

**Enunciado (parte 1):** tabla de conversión decimal-binario-octal a completar con 8-10 valores entre 0 y 7 (para los dígitos octales individuales) y luego 3-4 valores de un byte completo (0-255).

**Enunciado (parte 2 — múltiplos del byte):** dada la capacidad anunciada de tres discos distintos (1 TB, 256 GB, 500 GB), calcular cuántos GiB/TiB mostrará aproximadamente el sistema operativo al formatearlos, mostrando el cálculo (no solo el resultado).

**Enunciado (parte 3 — permisos):** dados 5 permisos en notación simbólica (`rwxr-xr-x`, `rw-rw-r--`, `rwx------`, `r--r--r--`, `rwxrwxrwx`), obtener su notación octal. Y a la inversa, dados 5 valores octales (750, 644, 600, 777, 640), obtener la notación simbólica y explicar en una frase qué puede hacer cada tipo de usuario.

**Solución (parte 2):** 1 TB = 1×10¹² bytes ÷ 1024⁴ ≈ 0,909 TiB (~909 GiB); 256 GB = 256×10⁹ bytes ÷ 1024³ ≈ 238,4 GiB; 500 GB ≈ 465,7 GiB (el mismo cálculo desarrollado en el guion).

**Solución (parte 3):** `rwxr-xr-x` → 755; `rw-rw-r--` → 664; `rwx------` → 700; `r--r--r--` → 444; `rwxrwxrwx` → 777.

**Qué mirar al corregir:** en la parte 2, el fallo más habitual es dividir por 1000³/1000⁴ en vez de 1024³/1024⁴ — es exactamente el error que confirma que no han entendido la diferencia entre ambas normas, no un simple fallo de cálculo. En la parte 3, el fallo más revelador es cuando el resultado final es correcto pero el alumno no puede explicar el paso intermedio (la conversión a binario) — indica que ha memorizado un patrón en vez de entender el mecanismo, y es precisamente el tipo de error que se manifestará en RA4 en cuanto aparezca un valor no memorizado.

### Curiosidades

- El modelo de permisos `rwx` de propietario/grupo/otros viene directamente de Unix, de los años 70, y se ha mantenido prácticamente intacto en Linux y macOS (que también deriva de Unix) durante más de cincuenta años — pocas piezas de diseño de software han demostrado tanta durabilidad.
- Los prefijos binarios (kibi, mebi, gibi...) los propuso formalmente la Comisión Electrotécnica Internacional en 1998 —precisamente para resolver esta ambigüedad de una vez—, pero más de veinticinco años después la mayoría de sistemas operativos y fabricantes de software todavía no los usan en su interfaz, y siguen mostrando "GB" cuando en realidad calculan en GiB.

---

## Epígrafe 6 — Sistemas transaccionales (CE-i)

**Duración:** 1 h · **Peso:** 7%

### Guion de clase

1. **El problema que resuelven (20 min):** plantear el escenario "se va la luz mientras el ordenador está escribiendo un archivo grande — ¿qué pasa?". Sin journaling, el sistema de archivos puede quedar en un estado inconsistente (corrupción). Con journaling, el sistema registra la operación antes de ejecutarla, de forma que puede completarla o deshacerla limpiamente al reiniciar.
2. **Journaling en ext4 y NTFS (25 min):** mencionar que ambos sistemas de archivos modernos (el de Linux y el de Windows) usan journaling, cada uno con su implementación, y que esta es una de las razones por las que los sistemas operativos actuales rara vez "se rompen" tras un corte de luz, a diferencia de sistemas de archivos más antiguos (FAT32, por ejemplo, no tiene journaling).
3. **Cierre y enlace con la elección de sistema de archivos (15 min):** enlazar con que, en RA5, al crear una máquina virtual, van a tener que elegir sistema de archivos — este contenido es el motivo técnico por el que casi siempre se recomienda ext4 en Linux y NTFS en Windows, y no alternativas sin journaling.

### Contexto para el profesorado

Epígrafe deliberadamente corto — es el contenido de la unidad con menos relación directa con las prácticas posteriores, y no hay que forzar más profundidad de la que da de sí en una hora. Es buen candidato para una demo puramente conceptual (sin VM), incluso con una analogía no informática (una lista de la compra tachada a medida que se compra cada cosa, de forma que si se interrumpe la compra se sabe exactamente qué falta, en vez de tener que revisar todo el carrito desde cero).

### Errores conceptuales frecuentes

- **Pensar que journaling "hace copias de seguridad".** No es una copia de seguridad ni protege contra pérdida de datos por borrado o fallo de disco — solo protege la consistencia del sistema de archivos ante interrupciones durante una escritura.

### Preguntas frecuentes del alumnado

- *"¿Entonces si tengo journaling nunca voy a perder datos?"* — No: journaling protege la estructura del sistema de archivos, no el contenido de un archivo en concreto que se estuviera escribiendo en el momento exacto del corte. Es un buen momento para recalcar que journaling no sustituye a hacer copias de seguridad.

### Actividad / práctica

**Enunciado:** pregunta corta de reflexión escrita: "explica con tus palabras qué diferencia hay entre que un sistema de archivos tenga journaling y que se hagan copias de seguridad periódicas, y por qué hacen falta las dos cosas".

**Qué mirar al corregir:** que no reduzcan la respuesta a "journaling es una copia de seguridad" — es el error central a detectar aquí.

---

## Cierre de la unidad

### Caso práctico integrador

**Duración orientativa:** 1,5-2 h.

**Enunciado (para el alumnado):** un compañero de prácticas en la empresa os cuenta que ha copiado una carpeta de un proyecto desde un Linux a un pendrive con Windows, y al volver a copiarla a un Linux distinto los permisos "ya no eran los mismos" y algunos scripts que antes eran ejecutables ya no lo son. Se pide, con lo visto en la unidad:

1. Explicar qué sistema de archivos maneja permisos Unix de forma nativa y cuál no, y por qué eso puede explicar la pérdida de permisos al pasar por un pendrive formateado en un sistema de archivos sin ese soporte (por ejemplo, exFAT o FAT32).
2. Explicar en términos de binario/octal qué significa que un script "deje de ser ejecutable" (qué bit ha cambiado).
3. Relacionar el caso con la arquitectura por capas: ¿en qué capa se decide qué permisos tiene un archivo?
4. Explicar qué habría pasado si, en vez de copiar por un pendrive, se hubiera transferido por red directamente entre los dos Linux (para introducir, sin desarrollarlo, que el problema es específico de pasar por un sistema de archivos que no soporta el modelo de permisos Unix, no del hecho de copiar en sí).

**Solución orientativa para el profesorado:**
1. ext4 (y otros sistemas de archivos nativos de Linux) guardan permisos Unix reales; NTFS los emula parcialmente; exFAT/FAT32 no tienen ningún concepto de permisos Unix, así que al copiar a través de ellos se pierde esa información y se sustituye por permisos por defecto.
2. El bit de ejecución (`x`) del propietario (u otros conjuntos, según el caso) ha pasado de `1` a `0` — en términos octales, el dígito correspondiente ha bajado en una unidad impar (por ejemplo, de 7 a 6, o de 5 a 4).
3. En la capa del sistema operativo, concretamente en la gestión del sistema de archivos (una de las funciones vistas en el epígrafe 2) — los permisos no son una propiedad "del archivo" en abstracto, son metadatos que gestiona el sistema de archivos.
4. Al transferir directamente entre dos sistemas Linux con sistemas de archivos compatibles con permisos Unix (por ejemplo, por red con `scp`/`rsync`), los permisos sí se conservarían, porque no hay un sistema de archivos intermedio incompatible de por medio.

**Qué mirar al corregir:** este caso está pensado para detectar si el alumnado conecta los distintos epígrafes entre sí, no solo si recuerda cada uno por separado. La pregunta 3 es la más discriminante: quien no relacione permisos con "gestión de archivos" como función del SO probablemente ha estudiado los epígrafes de forma aislada.

### Resumen de la unidad (para repasar antes del examen)

- Un sistema informático es hardware + software + usuarios; el software se divide en software de base (SO, drivers, utilidades) y software de aplicación.
- El sistema operativo se organiza por capas: núcleo, controladores, shell, aplicaciones — y cumple cuatro grandes funciones: gestión de procesos, memoria, archivos y entrada/salida.
- Un proceso es un programa en ejecución, con estados (nuevo, listo, ejecución, bloqueado, terminado) — sin entrar en cómo decide el SO cuál ejecutar.
- Windows y Linux organizan sus archivos de forma distinta (letras de unidad frente a árbol único), y Linux distingue mayúsculas de minúsculas en los nombres.
- La conversión binario-octal existe, en el contexto de esta unidad, para poder leer y escribir permisos: cada dígito octal representa un conjunto completo de permisos `rwx`.
- Los permisos definen qué puede hacer el propietario, el grupo y el resto de usuarios sobre un archivo o directorio.
- El byte tiene múltiplos según dos normas distintas: el SI (kilo/mega/giga, base 10, los que anuncia el fabricante) y la IEC 80000-13 (kibi/mebi/gibi, base 2, los que suele calcular y mal-etiquetar el sistema operativo como "GB") — de ahí que un disco de 500 GB se muestre como ~465 GB.
- El journaling protege la consistencia del sistema de archivos ante interrupciones, pero no sustituye a las copias de seguridad.

### Tabla de correspondencia RA/CE

| CE | Dónde se trabaja | Instrumento de evaluación sugerido |
|---|---|---|
| a) | Epígrafe 1 | Actividad de clasificación + examen |
| b) | Epígrafe 5 | Ejercicios de conversión + examen |
| c) | Epígrafe 2 | Tabla comparativa + examen |
| d) | Epígrafe 2 | Tabla comparativa + examen |
| e) | Epígrafe 3 | Actividad de estados + examen |
| f) | Epígrafe 4 | Actividad de rutas + examen |
| g) | Epígrafe 4 | Actividad de atributos + examen |
| h) | Epígrafe 5 | Ejercicios de permisos + examen |
| i) | Epígrafe 6 | Pregunta de reflexión + examen |

### Ideas para preguntas de examen

- Clasificación de elementos de software (tipo test o respuesta corta), similar a la actividad del epígrafe 1.
- Pregunta de desarrollo corto: "explica la diferencia entre núcleo y shell, con un ejemplo de cada uno en Windows y en Linux".
- Verdadero/falso sobre estados de procesos, incluyendo algún distractor que confunda "bloqueado" con "terminado".
- Ejercicio de conversión decimal-binario-octal y de notación de permisos (simbólica ↔ numérica), del mismo estilo que la práctica del epígrafe 5 pero con valores distintos.
- Ejercicio de cálculo de múltiplos del byte (SI ↔ IEC 80000-13) con la capacidad de un disco distinto al usado en clase, pidiendo que se muestre el cálculo, no solo el resultado.
- Pregunta de caso corto (versión reducida del caso práctico integrador) para comprobar si conectan permisos con sistemas de archivos y con la arquitectura por capas.
- Pregunta de reflexión breve sobre journaling, evitando que se pueda responder solo con la palabra "copia de seguridad".
