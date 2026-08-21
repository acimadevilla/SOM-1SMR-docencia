# SOM-1SMR-docencia

Material docente del módulo **Sistemas Operativos Monopuesto (SOM)**, 1º SMR,
IES Medina Azahara.

Repositorio **privado**: contiene tanto el material de docencia (guiones de
clase para el profesor) como los apuntes del alumnado. Es la fuente de
verdad única del proyecto.

**¿Retomando el proyecto tras un tiempo?** Empieza por [ESTADO.md](ESTADO.md) — resume qué está hecho, qué falta y cuál es el siguiente paso.

Contexto completo del proyecto (objetivos, secuenciación, ponderación de RA,
enfoque pedagógico): [CONTEXTO.md](CONTEXTO.md).

## Estructura

```
├── criterios-evaluacion/   Documento oficial de criterios de evaluación y calificación
├── docencia/               Material para el profesor, por unidad didáctica (UD)
└── apuntes/                Material para el alumnado, por unidad didáctica (UD)
```

## Publicación de apuntes al repo del alumnado

El contenido de `apuntes/` se publica de forma manual y deliberada al repo
público [SOM-1SMR-alumnos](https://github.com/acimadevilla/SOM-1SMR-alumnos)
mediante `git subtree`. Nunca se automatiza ni se copia a mano.

Configuración inicial (una sola vez):

```bash
git remote add publico https://github.com/acimadevilla/SOM-1SMR-alumnos.git
```

Publicar el estado actual de los apuntes:

```bash
git subtree push --prefix=apuntes publico main
```

`docencia/` nunca se publica.
