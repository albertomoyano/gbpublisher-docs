# gbpublisher — Documentación

Repositorio del sitio de documentación oficial de [gbpublisher](https://github.com/albertomoyano/gbpublisher),
publicado en <https://albertomoyano.github.io/gbpublisher-docs/>.

La documentación cubre el marco conceptual de la publicación académica moderna,
la metodología editorial estructurada y el uso de la herramienta, con especial
atención al contexto de las revistas científicas latinoamericanas y el modelo de
acceso abierto diamante.

---

## Tecnología

El sitio está construido con [Hugo](https://gohugo.io/) usando el tema
[Docsy](https://www.docsy.dev/), y se publica automáticamente en GitHub Pages.

| Componente       | Detalle                                    |
|------------------|--------------------------------------------|
| Hugo             | extended (requerido para SCSS)             |
| Tema             | Docsy (Hugo module)                        |
| Búsqueda         | Lunr.js (offline, sin servicios externos)  |
| Idiomas          | Español (principal), English, Português    |
| Feed RSS         | generado automáticamente por Hugo          |

---

## Estructura del contenido

```
content/
├── es/          # Español (idioma principal)
├── en/          # English
└── pt/          # Português
```

Cada árbol de idioma replica la misma estructura de secciones:

```
docs/
├── nivel-1-marco/          # Marco conceptual de la publicación académica
├── nivel-2-metodologia/    # Metodología editorial estructurada
└── nivel-3-herramienta/    # Uso de gbpublisher
```

---

## Requisitos para ejecutar localmente

- [Hugo extended](https://gohugo.io/installation/) (versión reciente)
- [Go](https://go.dev/dl/) (requerido para Hugo modules)
- [Node.js](https://nodejs.org/) con npm (requerido por Docsy para PostCSS)

```bash
# Instalar dependencias de Node (solo la primera vez)
npm install

# Iniciar servidor local con recarga automática
hugo server
```

El sitio queda disponible en `http://localhost:1313/gbpublisher-docs/`.

---

## Contribuir a la documentación

Las contribuciones al contenido son bienvenidas. El proceso es el estándar de GitHub:

1. hacer fork de este repositorio
2. crear una rama descriptiva (`fix/typo-capitulo-2`, `add/seccion-redalyc`, etc.)
3. realizar los cambios en los archivos `.md` correspondientes
4. abrir un Pull Request con una descripción clara del cambio propuesto

También podés usar el botón **"Editar esta página"** que aparece al pie de cada
página del sitio — te lleva directamente al archivo fuente en GitHub.

Para reportar errores, imprecisiones o sugerir contenido nuevo, abrí un
[issue](https://github.com/albertomoyano/gbpublisher-docs/issues).

### Acuerdo de contribución

Al enviar un Pull Request a este repositorio, el contribuyente acepta que su
aporte queda licenciado bajo los mismos términos que el proyecto
([CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.es)).

---

## Licencia

El contenido de esta documentación está publicado bajo licencia
[Creative Commons Atribución-CompartirIgual 4.0 Internacional (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/deed.es).

Esto significa que podés reutilizar y adaptar el contenido siempre que se
atribuya la autoría y se mantenga la misma licencia en los trabajos derivados.

> La licencia del contenido de este repositorio (CC BY-SA 4.0) es independiente
> de la licencia del software gbpublisher (BSL 1.1 con transición a GPL-3.0).

---

## Repositorio principal

El código fuente de gbpublisher se encuentra en un repositorio separado:
<https://github.com/albertomoyano/gbpublisher>

---

**Copyright © 2025–2026 Alberto Moyano — Estudio 2A**
