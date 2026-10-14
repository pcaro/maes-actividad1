# Actividad 1 · Evaluación de un proyecto de innovación docente

Presentación digital de la Actividad 1 de **Innovación docente e Iniciación a la Investigación Educativa** (MAES, especialidad Tecnología e Informática): evaluación del proyecto **FIRST LEGO League** con el Decálogo de un Proyecto Innovador de Fundación Telefónica.

**Entrega:** 19 de octubre de 2026 · **Peso:** 5 de los 15 puntos de la evaluación continua.

## Contenido

El análisis y las fuentes viven en el repositorio de trabajo del máster, `pcaro/maes`, en `primero/innovacion-docente-investigacion-educativa/actividad-1/`:

- `trabajo/02-actividad-1.md` — análisis completo (características, descripción, los 10 indicadores del Decálogo, diana, reflexión y referencias APA 7).
- `trabajo/00-seleccion-proyecto.md` — informe de selección del proyecto y alternativas descartadas.

Este repositorio contiene **solo la pieza visual**.

## Guion visual

Arco elegido, de los cinco planteados:

1. **La diana como columna vertebral.** La diana no es una diapositiva final: aparece al principio casi vacía y se enciende un eje por bloque del análisis, hasta formar el polígono completo. El cierre deja a la vista el hallazgo: ocho ejes en 4, dos en 3 y el de **aprendizaje más allá del aula hundido en 2**.
2. **El gráfico del vacío ("sale del centro / no sale del aula").** Dos columnas enfrentadas: los torneos y el jurado sacan al alumnado del centro en lo geográfico, pero no en la naturaleza del aprendizaje —no hay contexto informal ni servicio real a la comunidad—.
3. **Sostenibilidad en tres cifras.** En lugar de una curva, tres tarjetas: 679.000 participantes en 110 países, 14.000 en España y Andorra, y una trayectoria desde 1998. El programa es muy sostenible; la barrera es de acceso (coste), no de continuidad.

Como apoyo puntual, los **tres pilares** (Proyecto de Innovación, Juego del Robot y Core Values). La idea de presentar el proyecto como un *robot* se reserva como guiño de portada, sin desarrollar.

## Estructura

```text
├── index.html                              # la presentación entera: HTML, CSS y la diana en SVG en línea
└── actividad-1-first-lego-league.pdf       # la misma presentación en PDF, una diapositiva por página
```

### El PDF

Se genera desde el propio HTML, sin herramientas externas, y la página tiene **exactamente las medidas del lienzo de diseño** (1240 x 698 px = 930 x 523,92 pt), de modo que el PDF es el diseño y no una reinterpretación: las columnas, la diana y los gráficos caen donde se revisaron.

Dos detalles que costaron encontrar y conviene no volver a pisar:

- Chrome **ignora el `@page { size }`** del CSS salvo que se le pase `preferCSSPageSize`. El comando `agent-browser pdf` no expone esa opción, así que la generación va por el protocolo DevTools (`Page.printToPDF` con `preferCSSPageSize` y `printBackground`). Sin eso, el PDF sale en carta apaisada, la maquetación se reflowa y la composición se rompe.
- En impresión, `.slide` no puede ser `position: static`: el pie de página es absoluto y se queda sin referencia, así que desaparece de todas las páginas. Se apilan con `position: relative` más `break-after`.

Sin paso de compilación ni dependencias: un HTML con el CSS y el SVG en línea, servido directamente por GitHub Pages. Se versiona tal cual se publica, sin `node_modules` ni CI de por medio.

### Ver en local

```bash
python3 -m http.server 8080   # y abrir http://localhost:8080
```

También funciona abriendo el fichero directamente (`file://`); el servidor solo hace falta para que la URL se parezca a la publicada. Se navega con las flechas izquierda y derecha, y el botón *exportar a PDF* usa el diálogo de impresión del navegador (una diapositiva por página, en apaisado).

## Publicación

**Publicada:** <https://pcaro.github.io/maes-actividad1/> → este es el enlace que pide la actividad.

Servida por GitHub Pages desde la rama `main`, en la raíz. El repositorio es público: en el plan Free, Pages no admite repositorios privados, y de todos modos la actividad exige un enlace público, así que un repositorio privado solo habría ocultado el código fuente.

Dos cosas que conviene saber de este despliegue:

- **El primer build falló** con `Page build failed` (duración cero) y el siguiente construyó sin problemas. El error no se reprodujo y no llegué a determinar la causa; se añadió `.nojekyll` como medida preventiva. Si alguna vez vuelve a fallar, se consulta con `gh api repos/pcaro/maes-actividad1/pages/builds/latest`.
- El PDF de la entrega se sirve también desde aquí: `actividad-1-first-lego-league.pdf`.
