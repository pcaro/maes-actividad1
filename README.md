# Actividad 1 · Evaluación de un proyecto de innovación docente

Presentación digital de la Actividad 1 de **Innovación docente e Iniciación a la Investigación Educativa** (MAES, especialidad Tecnología e Informática): evaluación del proyecto **Apps for Good** con el Decálogo de un Proyecto Innovador de Fundación Telefónica.

**Entrega:** 19 de octubre de 2026 · **Peso:** 5 de los 15 puntos de la evaluación continua.

## Contenido

El análisis y las fuentes viven en el repositorio de trabajo del máster, `pcaro/maes`, en `primero/innovacion-docente-investigacion-educativa/actividad-1/`:

- `trabajo/02-actividad-1.md` — análisis completo (características, descripción, los 10 indicadores del Decálogo, diana, reflexión y referencias APA 7).
- `trabajo/00-seleccion-proyecto.md` — informe de selección del proyecto y alternativas descartadas.
- `trabajo/01-apps-for-good-ficha-top100.txt` — ficha del proyecto en el Top 100 (2014, págs. 23-26).

Este repositorio contiene **solo la pieza visual**.

## Guion visual

Arco elegido, de los cinco planteados:

1. **La diana como columna vertebral.** La diana no es una diapositiva final: aparece al principio casi vacía y se enciende un eje por bloque del análisis, hasta formar el polígono completo. El cierre deja a la vista el hallazgo: nueve ejes altos y el de **evaluación hundido en 1**.
2. **El gráfico del vacío ("lo que el proyecto mide / lo que no mide").** Columna llena frente a columna vacía: encuestas de percepción y métricas de programa frente a la ausencia de rúbrica de aprendizaje e instrumentos de evaluación de competencias.
3. **Dos curvas que se cruzan.** Línea temporal 2010-2026: el alcance crece (17.000 estudiantes y 230 escuelas en 2013; 6.000 estudiantes de 196 centros en Cataluña en enero de 2014; 30.444 al año hoy) mientras los productos del propio programa desaparecen (los cursos anteriores dejaron de mantenerse en agosto de 2026). El eje de sostenibilidad en una sola imagen.

Como apoyo puntual, la **escalera de los cuatro niveles de prototipado** (de los *wireframes* a JavaScript con API, p. 25 de la ficha implícita). La idea de presentarlo como una *app* se reserva como guiño de portada, sin desarrollar.

## Estructura

```text
.
├── index.html   # la presentación, en un único fichero autocontenido
└── assets/      # diana, balanza y curvas en SVG
```

Sin paso de compilación ni dependencias: un HTML con el CSS y el SVG en línea, servido directamente por GitHub Pages. Se versiona tal cual se publica, sin `node_modules` ni CI de por medio.

## Publicación

GitHub Pages **no está habilitado todavía**: en el plan actual (Free), Pages no admite repositorios privados.

```bash
# cuando se decida publicar
gh repo edit pcaro/maes-actividad1 --visibility public --accept-visibility-change-consequences
gh api -X POST repos/pcaro/maes-actividad1/pages -f 'source[branch]=main' -f 'source[path]=/'
```

La URL quedará en `https://pcaro.github.io/maes-actividad1/`.

Nota: aun en planes de pago, la web publicada es siempre pública; un repositorio privado solo oculta el código fuente. Como la actividad exige un enlace público, el contenido será visible en cualquier caso.
