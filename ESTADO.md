# ESTADO.md — Punto de partida rápido

> Léelo primero cada vez que retomes el proyecto. Este archivo se actualiza
> después de cada sesión de trabajo relevante — si algo no aparece aquí, no
> se ha comiteado todavía. Los "por qué" de las decisiones están en
> [CONTEXTO.md](CONTEXTO.md); esto es solo el "dónde estamos" y el
> "qué toca ahora".

**Última actualización:** 2026-08-20

---

## En una frase

Terminado el diseño global del módulo (bloques, ponderación, mapa de contenidos) y un primer borrador completo de la **docencia de UD01**; falta que lo revises, generar sus **apuntes**, y luego seguir con UD02.

## Qué hacer ahora mismo

- [ ] Revisar `docencia/UD01-fundamentos-so/UD01_docencia.md` (6 epígrafes + caso práctico + resumen) y confirmar que se da por cerrada.
- [ ] Generar los **apuntes** de UD01 a partir de esa docencia ya validada.
- [ ] Decidir si actualizamos primero el documento oficial de "Criterios de evaluación y calificación" con la ponderación nueva, o seguimos con UD02 y lo dejamos para más adelante.

---

## Progreso por unidad didáctica

| UD | Bloque | Docencia | Apuntes | Prácticas | Estado |
|---|---|---|---|---|---|
| UD01 | RA1 — Fundamentos simplificados | ✅ borrador completo (v1) | ⬜ no iniciado | ⬜ no iniciado | En curso |
| UD02 | RA5 (+refuerzo RA2) — Virtualización e instalación | ⬜ | ⬜ | ⬜ | Pendiente |
| UD03 | RA3 Linux — Configuración | ⬜ | ⬜ | ⬜ | Pendiente |
| UD04 | RA3 Windows — Configuración | ⬜ | ⬜ | ⬜ | Pendiente |
| UD05 | RA4 Linux — Administración | ⬜ | ⬜ | ⬜ | Pendiente |
| UD06 | RA4 Windows — Administración | ⬜ | ⬜ | ⬜ | Pendiente |

*(Regla del proyecto: nunca se desarrolla más de una unidad a la vez salvo que lo pidas expresamente.)*

## Otros documentos del proyecto

| Documento | Estado |
|---|---|
| [`criterios-evaluacion/1SMR-SOM-Propuesta_planificacion_y_ponderacion`](criterios-evaluacion/) (docx + md) | ✅ hecho — planificación por bloques, ponderación de RA y CE, mapa de contenidos por bloque |
| Documento oficial "Criterios de evaluación y calificación" (con la ponderación nueva) | ⬜ no actualizado todavía |
| `CONTEXTO.md` | ✅ vivo, se actualiza si cambian decisiones de fondo |
| `CLAUDE.md` (creado por ti, fuera de git por ahora) | ⬜ pendiente decidir si se integra en el repo o se fusiona con `CONTEXTO.md` |

---

## Decisiones pendientes / abiertas

- Aprobación departamental de la ponderación de RA propuesta (15/10/25/30/20).
- Mecanismo exacto de integración de la nota de RA2 (tutor de empresa) en la calificación final del módulo.
- Qué hacer con `CLAUDE.md`: por ahora se deja fuera del repositorio a petición tuya.

---

## Historial de hitos

- **2026-08-19** — Estructura inicial del repo (`docencia/`, `apuntes/`, `criterios-evaluacion/`), remotos `origin` (privado) y `publico` configurados, primer commit.
- **2026-08-19** — Propuesta de planificación y ponderación: bloques, ponderación de RA, mapa de contenidos por bloque asociado a CE (docx + md).
- **2026-08-19/20** — Reajuste de la ponderación de CE dentro de RA1 (ya no igualitaria: sube sistema de archivos y permisos, baja procesos y transaccionales) y reordenación del Bloque 1 en 6 epígrafes por prerrequisito práctico, no por orden alfabético de CE.
- **2026-08-20** — UD01 Docencia: primer borrador completo (6 epígrafes, caso práctico integrador, resumen, tabla RA/CE, ideas de examen). Ampliado después con unidades de medida de la información (SI vs. IEC 80000-13, caso del disco de 500GB→465GB) y con la ubicación de la interfaz gráfica y los tipos de núcleo (monolítico/microkernel/híbrido) en el epígrafe 2.

---

## Siguiente paso natural

1. Revisar y cerrar la docencia de UD01.
2. Generar los apuntes de UD01 (versión para alumnado).
3. Empezar UD02 — RA5 (+ refuerzo RA2): Virtualización e instalación.
