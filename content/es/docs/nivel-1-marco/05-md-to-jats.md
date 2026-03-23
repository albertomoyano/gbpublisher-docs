---
title: "Markdown como protocolo de entrada en la cadena editorial científica"
weight: 5
description: >
  La publicación científica contemporánea exige que los artículos estén disponibles en formatos estructurados y legibles por máquinas, siendo el estándar JATS (Journal Article Tag Suite, NISO Z39.96) el esquema XML dominante en los sistemas de indexación internacionales. Sin embargo, la producción directa de XML-JATS presenta barreras técnicas significativas para los equipos editoriales. Este artículo analiza por qué Markdown constituye el protocolo de entrada óptimo en una cadena editorial orientada a la producción de JATS canónico, examinando sus fundamentos históricos, su estado de adopción actual, su complementariedad semántica con JATS, su dimensión pragmática en contextos editoriales reales y su proyección futura en el ecosistema de la comunicación científica.
---

## 1. Introducción: el problema de la fragmentación en los flujos editoriales científicos

La publicación científica atraviesa una paradoja estructural de consecuencias prácticas significativas: mientras los sistemas de indexación internacional convergen hacia el XML estructurado como formato canónico de representación y circulación de artículos, los autores continúan produciendo sus manuscritos en procesadores de texto de propósito general —principalmente Microsoft Word— cuya arquitectura interna es fundamentalmente incompatible con el paradigma del marcado semántico [1,2].

Esta brecha entre el formato de producción y el formato de circulación genera lo que puede denominarse "fragmentación editorial": cada revista debe mantener cadenas de conversión paralelas, a menudo manuales o semimanuales, para transformar los manuscritos recibidos en los formatos exigidos por los distintos sistemas de indexación. En el contexto latinoamericano, esto significa que una misma revista puede necesitar producir variantes para SciELO Publishing Schema (SPS), para las especificaciones de Redalyc, para [JATS4R](https://jats4r.niso.org/) y, eventualmente, para PubMed Central, cada una con sus propias particularidades de implementación, aunque todas deriven del estándar JATS [3,4].

El costo de esta fragmentación recae desproporcionadamente sobre las revistas del modelo de acceso abierto diamante —aquellas que no cobran ni a lectores ni a autores—, que carecen de los recursos financieros de las grandes editoriales comerciales para sostener equipos técnicos especializados en marcado XML [5]. En América Latina, donde este modelo diamante es predominante y estructuralmente vinculado a instituciones universitarias y organismos públicos de ciencia, el problema adquiere dimensiones críticas [6].

La solución canónica a este problema, tal como ha sido propuesta por diversas iniciativas de infraestructura editorial abierta, consiste en adoptar un archivo maestro en XML-JATS a partir del cual se deriven automáticamente las variantes específicas de cada plataforma. Sin embargo, esta solución desplaza el problema sin resolverlo: sigue siendo necesario determinar desde qué formato se produce ese archivo maestro, y ese es precisamente el problema que este artículo aborda.

### JATS como estándar convergente de la comunicación científica

El estándar JATS (Journal Article Tag Suite), formalizado como [NISO Z39.96](https://www.niso.org/standards-committees/jats), es hoy el esquema XML dominante para la representación de artículos científicos en los sistemas de indexación y archivo de mayor alcance mundial [7]. Su adopción por parte de PubMed Central (PMC) en el contexto del National Center for Biotechnology Information (NCBI) de los Estados Unidos, y su posterior incorporación como base de los esquemas editoriales de SciELO y Redalyc en América Latina, le han conferido un papel de facto de infraestructura de la comunicación científica internacional [3,8].

JATS proviene del NLM DTD (National Library of Medicine Document Type Definition), desarrollado originalmente a comienzos de los años 2000 para el archivo digital de artículos biomédicos en PubMed Central. Su diseño original reflejaba las prioridades del dominio biomédico: estructura rígida, semántica precisa, trazabilidad de elementos (autores, afiliaciones, financiamiento, referencias) y compatibilidad con los flujos de datos de MEDLINE [7,9].

La transición de NLM DTD a JATS implicó una generalización del esquema hacia dominios disciplinares más amplios —ciencias sociales, humanidades, educación— sin abandonar la filosofía de marcado semántico exhaustivo. El resultado es un estándar suficientemente expresivo para representar la complejidad estructural de cualquier artículo científico, pero también suficientemente complejo como para exigir, en su implementación directa, conocimientos especializados de XML que la mayoría de los equipos editoriales no poseen [2,10].

Este es el núcleo de la tensión que fundamenta la pregunta de investigación del presente artículo: ¿cuál es el lenguaje de marcado más adecuado como protocolo de entrada para producir JATS [canónico](https://dle.rae.es/can%C3%B3nico) de manera eficiente, accesible y sostenible?

### La búsqueda de un protocolo de entrada adecuado

La pregunta por el protocolo de entrada óptimo hacia JATS ha recibido distintas respuestas en la literatura y en la práctica editorial. Las principales alternativas documentadas incluyen:

**a) Producción directa en XML-JATS.** Es el enfoque adoptado formalmente por sistemas como SciELO en sus etapas de producción profesional. Requiere marcadores XML especializados y herramientas como el SciELO PC Programs o editores XML como [Oxygen](https://www.oxygenxml.com/). Su principal desventaja es el alto costo de implementación y la pronunciada curva de aprendizaje, que la hace inviable para equipos pequeños [3].

**b) Conversión desde Microsoft Word mediante plantillas.** Es el flujo más extendido en la práctica, pero produce XML de calidad variable y frecuentemente requiere revisión manual intensiva. Los metadatos estructurales (afiliaciones, fondos de financiamiento, declaraciones de conflicto de interés) rara vez se capturan correctamente en este flujo [2,11].

**c) [LaTeX](https://www.latex-project.org/) como formato intermedio.** Adoptado en disciplinas matemáticas y físicas, presenta ventajas en la representación de fórmulas y notación científica, pero su curva de aprendizaje es elevada y su uso en ciencias sociales, humanidades y ciencias de la salud clínica es marginal. Herramientas como latex2jats existen pero tienen soporte limitado [12].

**d) Markdown como protocolo de entrada.** Es la alternativa relativamente más reciente en términos de adopción sistemática en flujos editoriales científicos, cuenta con un ecosistema de herramientas maduro —centrado en [Pandoc](https://pandoc.org/)— y una creciente base de evidencia empírica sobre su eficacia [13,14].

Este artículo sostiene que la cuarta alternativa —Markdown como protocolo de entrada— es la óptima para el objetivo de producción de JATS canónico en el contexto de revistas con recursos limitados, y articula los fundamentos de esta tesis a lo largo de las secciones siguientes.

### Justificación y relevancia para el contexto latinoamericano

La relevancia de esta discusión para el ecosistema editorial latinoamericano trasciende lo meramente técnico. América Latina ha construido, a lo largo de tres décadas, una infraestructura de acceso abierto sin precedentes a escala global: SciELO, fundada en 1997 por FAPESP y BIREME, y Redalyc, fundada en 2003 por la Universidad Autónoma del Estado de México, representan colectivamente miles de revistas y millones de artículos disponibles sin barreras de acceso [6,15].

Esta infraestructura, sin embargo, funciona bajo una tensión permanente: los equipos editoriales que la sostienen son en su mayoría pequeños, con recursos técnicos y financieros limitados, y las exigencias de marcado estructurado de los sistemas de indexación se incrementan continuamente. El requerimiento de XML-JATS no es una opción técnica entre otras: es una condición de visibilidad e impacto en la ciencia global [3,6].

En este contexto, la elección del protocolo de entrada hacia JATS no es una decisión técnica menor; es una decisión estratégica que puede determinar la sostenibilidad del modelo editorial diamante a mediano y largo plazo. Un protocolo de entrada que sea simultáneamente accesible para autores sin formación técnica especializada, capaz de preservar la semántica estructural requerida por JATS y compatible con flujos de trabajo colaborativos y control de versiones, representa una ventaja competitiva decisiva para las revistas latinoamericanas [5,14].

### Pregunta de investigación y objetivos

La pregunta central que articula este artículo es: **¿Por qué Markdown constituye el protocolo de entrada óptimo para la producción de JATS canónico en el contexto de la publicación científica de acceso abierto, particularmente en América Latina?**

Los objetivos específicos son:

1. Reconstruir la genealogía histórica de Markdown en relación con los principios que fundamentan el diseño de JATS.
2. Describir el estado del arte de las herramientas y flujos de trabajo basados en Markdown para la producción de XML científico.
3. Analizar la complementariedad semántica entre los elementos estructurales de Markdown y los elementos nucleares de JATS.
4. Examinar las ventajas pragmáticas de Markdown como protocolo de entrada en contextos editoriales con recursos limitados.
5. Proyectar las tendencias de convergencia entre Markdown, ciencia abierta y estándares de publicación estructurada.

### Estructura del artículo

El artículo está organizado conforme a la estructura [IMRyD](https://es.wikipedia.org/wiki/Introducci%C3%B3n,_M%C3%A9todos,_Resultados_y_Discusi%C3%B3n). La sección de Materiales y Métodos describe el enfoque metodológico adoptado para la revisión de la literatura y el análisis de estándares. La sección de Resultados desarrolla los cinco ejes temáticos identificados: historia, estado del arte, complementariedad semántica, dimensión pragmática y proyección futura. La sección de Discusión integra estos hallazgos en una argumentación cohesiva sobre la centralidad de Markdown en las cadenas editoriales orientadas a JATS canónico. Las Conclusiones sintetizan las implicaciones prácticas y teóricas del análisis, con énfasis en el diseño de herramientas editoriales como gbpublisher.

## 2. Materiales y métodos: diseño del estudio

Se realizó una revisión narrativa de alcance amplio (*scoping review* en la terminología anglosajona), orientada a mapear el estado del conocimiento sobre Markdown como protocolo de entrada en cadenas editoriales científicas orientadas a XML-JATS. Se eligió la revisión narrativa —en lugar de una revisión sistemática con metaanálisis— porque el objeto de estudio combina dimensiones históricas, técnicas y de política editorial que no son reducibles a un conjunto homogéneo de estudios primarios cuantificables [16].

Este tipo de revisión es reconocido como metodológicamente apropiado cuando el objetivo es sintetizar conocimiento heterogéneo sobre un tema emergente, identificar brechas conceptuales y construir marcos analíticos para la práctica [17]. Su limitación principal —la ausencia de un protocolo de búsqueda exhaustivo y reproducible con criterios [PRISMA](https://www.prisma-statement.org/)— es asumida explícitamente como una restricción del presente trabajo.

### Fuentes y estrategia de búsqueda

La búsqueda bibliográfica se realizó en las siguientes fuentes:

**Bases de datos académicas:**
- PubMed/MEDLINE, para literatura sobre flujos de producción XML
  en publicación biomédica y especificaciones JATS/NLM DTD.
- Scopus y Web of Science, para literatura sobre comunicación
  científica, acceso abierto y estándares de publicación.
- [ACM Digital Library](https://dl.acm.org/) y [IEEE Xplore](https://ieeexplore.ieee.org/Xplore/home.jsp), para literatura técnica sobre
  sistemas de marcado de documentos y cadenas de herramientas
  de conversión.
- [SciELO](https://www.scielo.org/es/) y [Redalyc](https://www.redalyc.org/), para literatura latinoamericana sobre flujos
  editoriales y modelos de acceso abierto.

**Repositorios y documentación técnica:**
- Especificaciones formales de JATS publicadas por NISO
  (National Information Standards Organization).
- Documentación oficial de Pandoc.
- Especificaciones del SciELO Publishing Schema ([SPS](https://scielo.readthedocs.io/projects/scielo-pc-programs/en/latest/index_es.html)).
- Especificaciones de [JATS4R](https://jats4r.niso.org/).
- Repositorios de código de herramientas relevantes
  en GitHub/GitLab.
- Documentación del proyecto [ORCID](https://orcid.org/), [CrossRef](https://www.crossref.org/) y [DataCite](https://datacite.org/) en lo relativo a metadatos estructurados.

**Literatura gris:**
- Informes y documentos de trabajo de organizaciones como SPARC, FORCE11, NISO y CLACSO.
- Entradas de blogs técnicos especializados de amplia circulación en la comunidad de software académico, como [*Scholarly Kitchen*](https://scholarlykitchen.sspnet.org/), [*PLOS Tech*](https://plos.org/) y el blog del proyecto Pandoc.

Los términos de búsqueda empleados —en inglés y español— incluyeron combinaciones de: *Markdown*, *JATS*, *XML*, *scientific publishing*, *editorial workflow*, *Pandoc*, *lightweight markup*, *structured authoring*, *diamond open access*, *SciELO*, *Redalyc*, *Latin America*, *document conversion*, *semantic markup*.

### Criterios de inclusión y exclusión

Se incluyeron fuentes que:
- Abordaran directamente la producción o conversión de documentos científicos en formatos de marcado estructurado.
- Documentaran especificaciones técnicas de JATS, Markdown o sus variantes académicas.
- Analizaran flujos editoriales en el contexto de acceso abierto, con énfasis en América Latina.
- Fueran publicadas preferentemente desde el año 2000 en adelante, salvo para referencias históricas sobre los orígenes de los lenguajes de marcado (SGML, TeX y GML).

Se excluyeron fuentes que:
- Abordaran Markdown exclusivamente en contextos no editoriales (documentación de software de propósito general, foros de discusión no especializados).
- Presentaran especificaciones técnicas obsoletas sin continuidad en versiones vigentes.
- Fueran de origen incierto o no atribuibles a organizaciones o autores identificables.

### Proceso de análisis

El análisis se organizó en torno a cinco dimensiones temáticas determinadas *a priori*, correspondientes a los cinco ejes de la pregunta de investigación: historia, estado del arte, complementariedad semántica, dimensión pragmática y proyección futura. Para cada dimensión se identificaron los argumentos centrales presentes en la literatura, se verificó su consistencia con las especificaciones técnicas de los estándares vigentes y se construyeron análisis comparativos donde correspondía.

Cuando la literatura no ofrecía evidencia directa sobre algún punto específico, se optó explícitamente por señalarlo como inferencia argumentada a partir de evidencia indirecta, en lugar de presentarlo como hallazgo establecido. Esta distinción es metodológicamente central para la integridad del presente trabajo.

### Alcances y limitaciones metodológicas

La principal limitación de este trabajo es su naturaleza de revisión narrativa, que introduce un grado de selección subjetiva de fuentes imposible de eliminar completamente. La segunda limitación relevante es la escasez relativa de literatura académica formal sobre flujos Markdown-a-JATS en el contexto latinoamericano específicamente: gran parte del conocimiento técnico disponible en esta área circula como documentación de herramientas, posteos técnicos o comunicaciones en conferencias de la comunidad de software académico, más que como artículos en revistas indexadas.

Esta escasez es en sí misma un hallazgo relevante, que subraya la pertinencia del presente artículo como contribución a la sistematización de ese conocimiento disperso.

## 3. Resultados: genealogía histórica. Markdown y JATS como expresiones del mismo principio fundacional

#### El principio de separación entre contenido y forma

Para comprender por qué Markdown es un protocolo de entrada naturalmente compatible con JATS, es necesario remontarse al principio arquitectónico que ambos comparten: la **separación entre contenido y presentación**. Este principio no es trivial ni evidente; es el resultado de décadas de evolución en el pensamiento sobre procesamiento de documentos, y su comprensión histórica es indispensable para evaluar su relevancia actual.

El primer hito en esta historia es la publicación, en 1969, del Generalized Markup Language (GML) por Charles Goldfarb, Edward Mosher y Raymond Lorie en IBM [18]. GML fue concebido como una respuesta al problema de los sistemas de composición tipográfica de la época, que mezclaban instrucciones de formato específicas de cada dispositivo de salida con el contenido del documento, haciéndolo no portable. La idea central de GML era radicalmente simple y, a la vez, de consecuencias enormes: las marcas en un documento deben describir **qué es** un elemento (un título, un párrafo, una referencia), no **cómo debe verse** en un dispositivo particular [18,19].

Esta distinción —que en la terminología contemporánea se expresa como la diferencia entre **marcado semántico** y **marcado de presentación**— es el fundamento común de toda la genealogía que conduce tanto a JATS como a Markdown.

#### De GML a SGML: la formalización del marcado genérico

GML evolucionó hacia el Standard Generalized Markup Language ([SGML](https://es.wikipedia.org/wiki/SGML)), formalizado como estándar ISO en 1986 (ISO 8879:1986) [20]. SGML estableció la noción de *Document Type Definition* ([DTD](https://en.wikipedia.org/wiki/Document_type_definition)): un esquema formal que define los elementos válidos en un tipo de documento, sus relaciones jerárquicas y sus atributos. Esta arquitectura —separación entre el esquema (DTD) y el documento instancia— es el precursor directo de XML y, por extensión, de JATS [20,21].

La influencia de SGML en la publicación académica fue significativa: la Association of American Publishers ([AAP](https://publishers.org/)) desarrolló en 1986 un conjunto de DTDs basadas en SGML para la estructuración de artículos científicos, que constituyen el antecedente más directo de lo que eventualmente se convertiría en el estándar JATS [7]. El trabajo de la AAP reconocía que la producción de artículos científicos tenía características estructurales recurrentes —resúmenes, autorías, referencias bibliográficas, tablas, figuras— que merecían ser codificadas en un esquema formal y portable.

#### El nacimiento de XML y el NLM DTD

La aparición de XML 1.0, publicado por el [W3C](https://www.w3.org/) en 1998 como una simplificación de SGML orientada a la web [21], proporcionó la base técnica sobre la cual se construirían todos los estándares de marcado documental del siglo XXI. XML retiene los principios fundamentales de SGML —validación contra un esquema, separación entre contenido y presentación, portabilidad— mientras elimina las complejidades sintácticas que dificultaban su implementación práctica.

Sobre esta base, la National Library of Medicine de Estados Unidos desarrolló, a partir del año 2000, el NLM Journal Publishing DTD, diseñado específicamente para el archivo y distribución de artículos científicos en PubMed Central [7,9]. Este DTD fue el resultado de un esfuerzo colectivo que involucró a editores, bibliotecarios y especialistas en información científica, con el objetivo de crear un esquema suficientemente expresivo para capturar la semántica completa de un artículo científico, incluyendo no solo el cuerpo del texto sino también los metadatos administrativos, de autoría, financiamiento y citación [7].

La versión 3.0 del NLM DTD, publicada en 2008, fue la base directa a partir de la cual NISO desarrolló el estándar JATS (NISO Z39.96), formalizado en 2012 y actualizado en versiones sucesivas [7,22]. La transición de NLM DTD a JATS implicó principalmente una ampliación del alcance disciplinar del esquema y una formalización de su proceso de mantenimiento bajo una organización de estándares independiente, sin alterar sus principios de diseño fundamentales.

#### La tradición paralela: procesamiento ligero de texto

Mientras la tradición SGML/XML construía estándares cada vez más formalizados y exhaustivos para la representación semántica de documentos, una tradición paralela y aparentemente divergente se desarrollaba en el mundo de la escritura técnica y la informática: la búsqueda de formatos de texto plano que pudieran ser escritos por humanos sin asistencia de herramientas especializadas y procesados al mismo tiempo de manera automática para generar diferentes salidas formateadas.

El antecedente más influyente de esta tradición es [TeX](https://es.wikipedia.org/wiki/TeX), desarrollado por [Donald Knuth](https://es.wikipedia.org/wiki/Donald_Knuth) entre 1977 y 1989 para la composición tipográfica de documentos matemáticos [23]. TeX introdujo el principio de que un autor podía escribir en texto plano con marcas mínimas y obtener salidas tipográficas de alta calidad. LaTeX, la extensión de TeX desarrollada por [Leslie Lamport](https://es.wikipedia.org/wiki/Leslie_Lamport) a partir de 1984, popularizó este enfoque en la comunidad científica internacional, particularmente en matemáticas, física y ciencias de la computación [24].

Sin embargo, tanto TeX como LaTeX mantenían una sintaxis relativamente densa —abundante en caracteres de control, llaves y comandos— que aunque era más legible que XML, seguía requiriendo un aprendizaje específico y no resultaba cómoda para disciplinas que no tuvieran una tradición fuerte de composición tipográfica manual.

#### Markdown: la síntesis minimalista

En este contexto histórico, la creación de [Markdown](https://es.wikipedia.org/wiki/Markdown) por John Gruber y Aaron Swartz en 2004 representa menos una invención radical que una síntesis de tendencias previas llevada a su expresión más minimalista [25]. La declaración de diseño original de Gruber es elocuente en su ambición: Markdown debía ser

> lo más legible posible tal como está escrito [25]

de manera que un documento Markdown fuera inteligible incluso sin procesamiento, como texto plano ordinario.

Esta decisión de diseño —priorizar la legibilidad del texto fuente sobre la exhaustividad del marcado— es exactamente la decisión opuesta a la que tomaron los diseñadores de SGML y XML, y sin embargo conduce, como este artículo argumenta, a un resultado que es funcional y semánticamente compatible con los objetivos de JATS.

La intuición fundamental de Gruber fue que los usos más comunes del marcado estructural en la escritura cotidiana —encabezados, énfasis, listas, bloques de código, referencias— podían representarse con una sintaxis tan natural que el costo cognitivo de aprenderla fuera prácticamente nulo. En lugar de `<h2>Título</h2>`, se escribe `## Título`. En lugar de `<em>texto</em>`, se escribe `*texto*`. Esta correspondencia casi directa entre la intuición tipográfica del escritor y la sintaxis del marcado es el núcleo de la potencia de Markdown [25,26].

#### La convergencia: por qué dos tradiciones distintas producen resultados compatibles

La aparente paradoja de que Markdown —diseñado con intenciones minimalistas para la escritura en blogs— sea compatible con JATS —diseñado con rigor formal para el archivo de literatura científica— se resuelve al reconocer que ambos están anclados en el mismo principio genealógico: la separación entre contenido y presentación, y la representación de estructura semántica mediante marcas explícitas.

La diferencia es de exhaustividad, no de principio. JATS es un esquema exhaustivo que puede representar con precisión absoluta cada elemento semántico posible de un artículo científico. Markdown es un esquema minimalista que representa con elegancia los elementos semánticos más frecuentes de cualquier documento de texto. La cadena de conversión — en la práctica, Pandoc y su capacidad de generar XML-JATS desde Markdown— es el puente que convierte la suficiencia del esquema minimalista en la exhaustividad del esquema canónico [13,27].

Comprender esta convergencia como histórica y principial —no meramente accidental o tecnológica— es fundamental para argumentar que la elección de Markdown como protocolo de entrada hacia JATS no es una solución de compromiso, sino una decisión arquitectónica coherente con la mejor tradición del pensamiento sobre documentos estructurados.

#### La consolidación del ecosistema académico de Markdown

El período 2008-2020 marcó la consolidación de Markdown como herramienta de escritura académica, más allá de su uso original en blogs y documentación de software. Tres hitos son especialmente relevantes para la narrativa de este artículo:

**Pandoc (2006-presente).** El desarrollo de Pandoc por John MacFarlane a partir de 2006 transformó radicalmente las posibilidades de Markdown como formato de intercambio documental [27]. Pandoc introdujo extensiones al Markdown básico —notas al pie, tablas, metadatos YAML, citas bibliográficas, fórmulas matemáticas— que cubrían las necesidades específicas de la escritura académica, y desarrolló conversores a y desde decenas de formatos, incluyendo XML-JATS. La arquitectura de Pandoc —basada en un modelo de documento intermedio agnóstico del formato— es el fundamento técnico que hace posible la cadena Markdown --> JATS [27,28].

**R Markdown y el paradigma de la ciencia reproducible (2012-presente).** El desarrollo de R Markdown por Yihui Xie y el equipo de RStudio (hoy Posit) a partir de 2012 extendió Markdown hacia el paradigma de los documentos computacionales: documentos que integran código ejecutable, resultados y narrativa en un único archivo de texto plano [29]. Este desarrollo vinculó definitivamente Markdown con la agenda de reproducibilidad científica, y posicionó el formato como herramienta legítima de producción académica —no meramente de documentación técnica.

**Quarto (2022-presente).** La evolución de R Markdown hacia Quarto, un sistema de publicación científica y técnica de próxima generación desarrollado por Posit, consolidó el lugar de Markdown en el ecosistema de la publicación académica multinivel [30]. Quarto produce salidas en múltiples formatos —HTML, PDF, DOCX, JATS— desde una única fuente Markdown, con soporte nativo para múltiples lenguajes de programación y un sistema de metadatos YAML extensible y compatible con las necesidades de la publicación científica formal.

Estos tres hitos configuran el ecosistema dentro del cual Markdown se ha convertido, para un segmento creciente de la comunidad científica y editorial, en el formato de elección para la producción de documentos que deben circular en múltiples plataformas con integridad semántica.

### Estado del arte: el ecosistema de herramientas y markdown --> JATS en la publicación científica actual

#### Pandoc como núcleo de la cadena de conversión

Cualquier análisis del estado del arte en la producción de XML-JATS desde Markdown debe comenzar por Pandoc, porque Pandoc no es simplemente una herramienta más en este ecosistema: es su infraestructura central [27,28]. Desarrollado por John MacFarlane —profesor de filosofía en la Universidad de California Berkeley y programador funcional en Haskell— Pandoc ha evolucionado desde una utilidad de línea de comandos para conversión de formatos hacia una biblioteca de procesamiento documental de propósito general, con una arquitectura de filtros extensible que permite transformaciones arbitrarias sobre la representación interna del documento [27].

La arquitectura de Pandoc es relevante para este análisis por una razón específica: no realiza conversiones directas de formato a formato. En cambio, construye un modelo de documento intermedio —un árbol de sintaxis abstracta (AST) representado en un tipo de datos algebraico en Haskell— que es independiente tanto del formato de entrada como del formato de salida [28]. Este modelo intermedio es el que garantiza que la conversión Markdown --> JATS no sea una simple sustitución de marcas, sino una transformación semántica que preserva la estructura intelectual del documento.

Desde la versión 2.11 (2020), Pandoc incluye soporte para la generación de XML-JATS conforme al estándar NISO Z39.96, con capacidad para producir tanto el elemento `<journal-article>` con su estructura completa como los metadatos del encabezado (`<article-meta>`, `<journal-meta>`) a partir del bloque YAML front matter del documento Markdown [27,28]. Las versiones sucesivas han refinado este soporte, incorporando el manejo de elementos como `<funding-group>`, `<contrib-group>` con afiliaciones múltiples, y `<ref-list>` con citas en formato CSL (Citation Style Language).

Una limitación importante del soporte JATS de Pandoc, que debe señalarse con precisión, es que produce JATS válido pero no necesariamente JATS conforme a los perfiles específicos de cada plataforma de indexación. El XML generado por Pandoc es válido contra el DTD de JATS, pero puede requerir transformaciones adicionales para cumplir con el SciELO Publishing Schema, las especificaciones de JATS4R o los requerimientos particulares de PubMed Central [3,31]. Esta brecha entre JATS genérico y JATS perfilado es precisamente el espacio que herramientas como gbpublisher están diseñadas para cubrir.

#### El sistema CSL y la gestión de referencias bibliográficas

Un componente crítico de cualquier flujo de producción académica es el manejo de las referencias bibliográficas. Markdown básico no tiene sintaxis nativa para citas: es una extensión de Pandoc —implementada mediante pandoc-citeproc y posteriormente integrada al núcleo de Pandoc— la que proporciona esta capacidad [32].

El sistema de citas de Pandoc se basa en el Citation Style Language (CSL), un estándar abierto desarrollado originalmente por Bruce D'Arcus y mantenido actualmente por una comunidad activa bajo el paraguas de Zotero y Mendeley [32,33]. CSL permite definir estilos bibliográficos en un formato XML declarativo, con más de diez mil estilos disponibles en el repositorio oficial, incluyendo Vancouver, APA, Chicago, MLA y los estilos específicos de las principales revistas científicas internacionales.

En el flujo Markdown --> JATS mediado por Pandoc, las citas se insertan en el texto Markdown mediante la sintaxis `[@citekey]`, donde `citekey` es el identificador de una entrada en un archivo de bibliografía en formato BibTeX, CSL-JSON o RIS. Pandoc procesa estas citas, las resuelve contra la base de datos bibliográfica del autor, genera las llamadas en el texto en el formato CSL especificado y construye automáticamente el elemento `<ref-list>` en el XML-JATS resultante [27,32].

La importancia de este componente no puede subestimarse: la generación automática y semánticamente correcta de `<ref-list>` es uno de los aspectos más costosos y propensos a errores del marcado manual de artículos en XML-JATS. El sistema CSL-Pandoc resuelve este problema de manera elegante y consistente, produciendo elementos `<ref>` con la estructura interna correcta para cada tipo de fuente (artículo, libro, capítulo, software, conjunto de datos) [28,32].

#### Quarto: la evolución hacia la publicación científica integral desde Markdown

Quarto, lanzado en versión estable por Posit en 2022, representa el estado del arte actual en sistemas de publicación científica basados en Markdown [30]. A diferencia de R Markdown, que estaba acoplado al entorno de R, Quarto es un sistema agnóstico del lenguaje de programación, con soporte nativo para R, Python, Julia y Observable JavaScript, y una arquitectura basada en Pandoc como motor de conversión.

Desde la perspectiva de la producción JATS, Quarto ofrece capacidades significativas. Su formato nativo `.qmd` (Quarto Markdown) extiende Pandoc Markdown con una sintaxis enriquecida para elementos científicos: figuras con atributos de accesibilidad, tablas con identificadores y títulos formales, callouts estructurados, referencias cruzadas y un sistema de metadatos YAML más expresivo. La salida JATS de Quarto hereda y extiende la del Pandoc subyacente, con manejo mejorado de algunos elementos específicos de la publicación académica [30,34].

Un desarrollo particularmente relevante es el soporte de Quarto para el formato `jats` como objetivo de salida en su sistema de journals templates, que permite a revistas científicas definir plantillas de publicación que generan XML-JATS directamente desde documentos `.qmd` con metadatos completos [34]. Aunque este soporte está aún en desarrollo, su trayectoria indica una consolidación creciente de la cadena Markdown --> JATS en el ecosistema de la publicación científica de código abierto.

#### Manubot: Markdown colaborativo para publicación continua

Manubot es un sistema de escritura colaborativa y publicación continua desarrollado por Daniel Himmelstein y colaboradores, basado en Markdown, Pandoc y GitHub Actions [35]. Su diseño responde a las necesidades de la ciencia abierta: manuscritos que se escriben colaborativamente, se versionan con git, se revisan públicamente y se publican de manera continua en la web y, eventualmente, en formatos de archivo como PDF y XML.

Manubot es relevante para el presente análisis porque representa una implementación completa y documentada de la tesis que este artículo defiende: que Markdown, combinado con un sistema de gestión de metadatos y referencias adecuado, puede sostener un flujo de producción editorial científica de extremo a extremo. Los artículos producidos con Manubot han sido publicados en revistas indexadas de alto impacto, incluyendo contribuciones en *PLOS Computational Biology* y *eLife* [35,36].

#### Iniciativas institucionales y editoriales

Más allá de las herramientas de propósito general, diversas iniciativas institucionales han adoptado Markdown como componente de sus flujos de producción editorial, con resultados documentados.

**eLife Sciences.** La revista *eLife*, una de las publicaciones de acceso abierto de mayor impacto en ciencias biológicas y biomédicas, adoptó y extendió el proyecto Texture, desarrollado originalmente por Substance, para la edición de artículos en XML-JATS con una interfaz orientada a documentos [37]. Aunque Texture utiliza JATS como formato nativo en lugar de Markdown, su filosofía de diseño —edición semántica accesible para autores sin conocimientos XML— comparte los principios que fundamentan el uso de Markdown como formato de entrada.

**Stencila.** El proyecto Stencila, desarrollado por Nokome Bentley y colaboradores en el marco de Code for Science and Society, implementa un ecosistema de documentos científicos ejecutables que puede interoperar con Markdown y otros formatos ligeros como fuentes de entrada, y generar, entre otros, XML-JATS como salida [38]. Stencila aborda específicamente la integración de código ejecutable con narrativa científica en un flujo orientado a la publicación formal.

**Journal of Open Source Software (JOSS)**. Journal of Open Source Software utiliza Markdown como formato nativo para los artículos enviados, con una cadena de producción automatizada basada en Pandoc que genera PDF y otros formatos de distribución [39]. Aunque JOSS no produce XML-JATS actualmente, su modelo de producción basado en Markdown y revisión en GitHub es una referencia ampliamente citada en la literatura sobre flujos editoriales abiertos y reproducibles.

**Latinoamérica: iniciativas emergentes.** En el contexto latinoamericano, la adopción de flujos basados en Markdown para la producción de JATS es aún incipiente pero documentada en iniciativas como el programa SciELO en Brasil, que ha explorado la integración de herramientas de conversión desde formatos ligeros como componente de su flujo de producción de nueva generación [3,40]. La tensión entre la necesidad de reducir costos de producción y la exigencia de XML de alta calidad es reconocida explícitamente en los documentos estratégicos del programa [3].

#### Brechas identificadas en el estado del arte

El análisis del estado del arte permite identificar cuatro brechas que justifican el desarrollo de herramientas específicas para el contexto editorial latinoamericano:

**Brecha 1: perfilado de JATS.** Las herramientas genéricas de conversión (Pandoc, Quarto) producen JATS válido pero no perfilado para plataformas específicas (SciELO, Redalyc, JATS4R). La transformación desde JATS genérico hacia JATS perfilado requiere XSLT o procesamiento adicional que no está incorporado en las herramientas estándar.

**Brecha 2: metadatos complejos.** Los elementos de metadatos más complejos de JATS —identificadores de autor (ORCID), financiamiento (FundRef), licencias (Creative Commons URI), declaraciones de conflicto de interés— no tienen equivalentes directos en la sintaxis Markdown estándar ni en el YAML front matter de Pandoc. Su manejo requiere extensiones o convenciones específicas.

**Brecha 3: elementos visuales y suplementarios.** El manejo de figuras con múltiples formatos, tablas complejas, material suplementario y medios enriquecidos en el contexto JATS no está completamente resuelto en la cadena Pandoc/Quarto.

**Brecha 4: interfaz para equipos no técnicos.** Las herramientas disponibles requieren familiaridad con la línea de comandos, editores de texto plano y configuración de archivos YAML, lo que constituye una barrera significativa para los equipos editoriales de revistas sin soporte técnico especializado.

Estas cuatro brechas definen con precisión el espacio de diseño de herramientas como gbpublisher: no reemplazar la cadena Pandoc --> JATS, sino extenderla con perfilado de plataforma, gestión de metadatos complejos (que incluya gobernanza) y una interfaz accesible (con los principios de una aplicación nativa para escritorio) para equipos editoriales no técnicos.

### Complementariedad semántica: los elementos de Markdown y sus equivalentes en JATS

#### El principio de correspondencia estructural

La compatibilidad entre Markdown y JATS no es accidental ni meramente técnica: refleja una correspondencia estructural profunda entre los elementos que ambos sistemas reconocen como unidades semánticas de un texto científico. Esta sección documenta esa correspondencia de manera sistemática, identificando tanto las zonas de equivalencia directa como las zonas de fricción donde Markdown requiere extensiones o convenciones adicionales para capturar la semántica completa de JATS.

#### Correspondencias directas en la estructura del cuerpo

La tabla 1 documenta las correspondencias directas entre los elementos de Pandoc Markdown y los elementos JATS en la estructura del cuerpo del artículo.

**Tabla 1.** Correspondencia entre elementos de Markdown (Pandoc) y elementos JATS en el cuerpo del artículo.

| Elemento semántico      | Markdown (Pandoc)        | JATS                          |
|------------------------|--------------------------|-------------------------------|
| Sección de nivel 1     | `# Título`               | `<sec><title>Título</title>`  |
| Sección de nivel 2     | `## Título`              | `<sec><sec><title>`           |
| Párrafo                | Bloque de texto          | `<p>`                         |
| Énfasis (cursiva)      | `*texto*`                | `<italic>`                    |
| Énfasis fuerte (negrita)| `**texto**`             | `<bold>`                      |
| Énfasis combinado      | `***texto***`            | `<bold><italic>`              |
| Lista no ordenada      | `- ítem`                 | `<list list-type="bullet">`   |
| Lista ordenada         | `1. ítem`                | `<list list-type="order">`    |
| Bloque de código       | ` ``` código ``` `       | `<code>`                      |
| Código en línea        | `` `código` ``           | `<monospace>`                 |
| Cita en bloque         | `> texto`                | `<disp-quote>`                |
| Línea horizontal       | `---`                    | `<hr/>`                       |
| Nota al pie (Pandoc)   | `[^nota]`                | `<fn>`                        |
| Tabla                  | Tabla GFM                | `<table-wrap><table>`         |
| Figura (imagen)        | `![alt](ruta)`           | `<fig><graphic>`              |
| Enlace externo         | `[texto](url)`           | `<ext-link>`                  |
| Fórmula en línea       | `$ecuación$`             | `<inline-formula>`            |
| Fórmula en bloque      | `$$ecuación$$`           | `<disp-formula>`              |
| Cita bibliográfica     | `[@citekey]`             | `<xref ref-type="bibr">`      |
| Referencia cruzada     | `@fig-id`, `@tbl-id`     | `<xref ref-type="fig/table">` |

Fuente: elaboración propia a partir de las especificaciones de Pandoc [27,28] y la documentación de JATS [7,22].

Esta tabla revela una cobertura notable: los elementos que aparecen en el noventa por ciento o más de los artículos científicos estándar tienen equivalentes directos y bien definidos en la cadena Pandoc --> JATS. La correspondencia no es superficial: Pandoc no se limita a sustituir marcas; construye la estructura jerárquica correcta en JATS, incluyendo los atributos requeridos por el estándar.

#### Los metadatos: el YAML front matter como `<article-meta>`

El elemento `<article-meta>` de JATS es probablemente el más complejo y rico semánticamente de todo el esquema: contiene los metadatos administrativos, de autoría, de publicación y de clasificación del artículo. Su correcta implementación es crítica para la indexación: los sistemas como PubMed, SciELO y Redalyc procesan `<article-meta>` para extraer los datos que alimentan sus índices y bases de datos [7,3].

En la cadena Pandoc --> JATS, el bloque YAML front matter del documento Markdown es el que alimenta la construcción de `<article-meta>`. La tabla 2 documenta las correspondencias principales.

**Tabla 2.** Correspondencia entre campos YAML (Pandoc Markdown) y elementos `<article-meta>` en JATS.

| Campo YAML (Pandoc)     | Elemento JATS                              |
|------------------------|--------------------------------------------|
| `title`                | `<article-title>`                          |
| `subtitle`             | `<subtitle>`                               |
| `author: name`         | `<contrib><name>`                          |
| `author: orcid`        | `<contrib-id contrib-id-type="orcid">`     |
| `author: affiliation`  | `<aff>`                                    |
| `author: email`        | `<email>`                                  |
| `author: equal-contrib`| `<contrib equal-contrib="yes">`            |
| `author: corresponding`| `<contrib corresp="yes">`                  |
| `abstract`             | `<abstract>`                               |
| `keywords`             | `<kwd-group><kwd>`                         |
| `date`                 | `<pub-date>`                               |
| `doi`                  | `<article-id pub-id-type="doi">`           |
| `journal: title`       | `<journal-title>`                          |
| `journal: issn`        | `<issn>`                                   |
| `volume`               | `<volume>`                                 |
| `issue`                | `<issue>`                                  |
| `fpage` / `lpage`      | `<fpage>` / `<lpage>`                      |
| `license: type`        | `<license license-type="...">` en `<permissions>` |
| `funding-statement`    | `<funding-group><funding-statement>`        |

Fuente: elaboración propia a partir de las especificaciones de Pandoc [27,28] y la documentación de JATS [7,22].

Esta correspondencia es funcionalmente completa para los metadatos requeridos por la mayoría de los sistemas de indexación. Sin embargo, algunos elementos de `<article-meta>` que tienen importancia creciente en el ecosistema de la ciencia abierta no tienen equivalentes directos en el esquema YAML de Pandoc estándar, incluyendo:

- `<funding-group>` con identificadores FundRef (Crossref Funder Registry) por financiador individual.
- `<contrib-group>` con roles CRediT (Contributor Roles Taxonomy) por colaborador.
- `<custom-meta-group>` para metadatos específicos de plataforma.
- `<history>` con fechas de recepción, revisión y aceptación del manuscrito.

Estos elementos pueden incorporarse mediante extensiones del esquema YAML —convenciones adicionales definidas por la herramienta o la revista— y representan una de las áreas de desarrollo activo en el ecosistema Markdown --> JATS.

#### Las referencias bibliográficas: de CSL a `<ref-list>`

La correspondencia entre el sistema de referencias de Pandoc (CSL-JSON/BibTeX + pandoc-citeproc) y el elemento `<ref-list>` de JATS es una de las más elaboradas y técnicamente sofisticadas de toda la cadena de conversión. Merece un análisis específico porque la calidad de `<ref-list>` es un indicador crítico de la calidad del XML-JATS resultante para los sistemas de indexación [31,41].

En JATS, cada referencia bibliográfica se representa mediante un elemento `<ref>` que contiene un elemento hijo cuyo tipo depende del tipo de fuente: `<element-citation>` o `<mixed-citation>`. La diferencia entre ambos es semánticamente importante: `<element-citation>` separa cada componente bibliográfico en su propio elemento (`<person-group>`, `<article-title>`, `<source>`, `<year>`, `<volume>`, `<issue>`, `<fpage>`, `<lpage>`, `<pub-id>`), mientras que `<mixed-citation>` permite texto libre mezclado con elementos semánticos [7,22].

Pandoc genera referencias del tipo `<element-citation>` cuando dispone de la información estructurada en CSL-JSON, lo que es el caso cuando la bibliografía proviene de gestores de referencias como Zotero, Mendeley o JabRef que exportan en este formato [27,32]. La calidad del resultado depende directamente de la calidad de los metadatos bibliográficos en la base de datos del autor: entradas incompletas o mal estructuradas producen elementos `<ref>` con información faltante.

Este punto es importante para el diseño de flujos editoriales: la adopción de Markdown --> JATS no elimina la necesidad de rigor bibliográfico; lo desplaza desde la fase de marcado manual hacia la fase de gestión de referencias, que es donde realmente pertenece.

#### Zonas de fricción y sus soluciones actuales

A pesar de la amplia cobertura documentada en las secciones anteriores, existen zonas de fricción específicas donde la correspondencia Markdown --> JATS no es directa ni completamente satisfactoria. Su identificación precisa es tan importante como la documentación de las correspondencias exitosas, porque define el espacio de trabajo que las herramientas editoriales especializadas deben abordar.

**Fricción 1: elementos de marcado biomédico específico.** JATS incluye elementos semánticos propios del dominio biomédico que no tienen análogos en Markdown: `<named-content>` para términos con semántica de dominio (nombres de genes, fármacos, organismos), `<alternatives>` para contenido en múltiples formatos, `<supplementary-material>` con metadatos completos. Estos elementos deben incorporarse mediante mecanismos adicionales, como atributos de span personalizados (disponibles en Pandoc con la extensión `bracketed_spans`) o preprocesamiento específico [28].

**Fricción 2: tablas complejas.** La sintaxis de tablas en Pandoc Markdown (GFM o tablas de cuadrícula) admite alineación y formatos básicos, pero no celdas combinadas (`rowspan`/`colspan`), tablas con encabezados múltiples o tablas con notas al pie, todos presentes en la especificación JATS para `<table-wrap>`. Las tablas complejas requieren inserción directa de HTML o XML, rompiendo la homogeneidad del flujo Markdown.

**Fricción 3: figuras compuestas y subfiguras.** JATS permite `<fig-group>` para figuras compuestas con múltiples subfiguras, cada una con su propio `<label>`, `<caption>` y `<graphic>`. La sintaxis Markdown estándar no tiene un equivalente directo para esta estructura. Quarto implementa una solución parcial mediante su sintaxis de subfiguras, pero no cubre todos los casos posibles en JATS.

**Fricción 4: historial editorial y permisos detallados.** Los elementos `<history>` (fechas de recepción, revisión y aceptación), `<permissions>` con URI de licencia Creative Commons y `<copyright-statement>` detallado son críticos para la indexación en SciELO y PubMed Central, pero su incorporación en el YAML front matter de Pandoc requiere convenciones adicionales no estandarizadas entre herramientas.

**Soluciones en la práctica.** La literatura técnica y la documentación de proyectos como Quarto y Manubot muestran que estas fricciones se gestionan en la práctica mediante tres estrategias: (1) extensión del esquema YAML con campos específicos de la plataforma editorial; (2) uso de filtros Lua en Pandoc para transformaciones específicas del árbol AST; y (3) postprocesamiento XSLT sobre el XML-JATS generado para incorporar los elementos no cubiertos por la conversión directa [27,28,30]. La combinación de estas tres estrategias cubre la totalidad del espacio semántico de JATS para la mayoría de los casos editoriales prácticos.

#### La semántica suficiente como principio de diseño

El análisis de la correspondencia Markdown --> JATS permite formular un principio de diseño que es central para la argumentación de este artículo: el principio de **semántica suficiente**.

Markdown no captura el cien por ciento de la semántica de JATS. Tampoco necesita hacerlo para ser un protocolo de entrada efectivo. Lo que necesita —y lo que tiene— es capturar la semántica suficiente: todos los elementos estructurales que aparecen en la gran mayoría de los artículos científicos estándar, con la profundidad suficiente para que una cadena de conversión bien diseñada pueda derivar el JATS canónico completo a partir de esa representación inicial.

Los elementos que Markdown no captura directamente —los casos de fricción documentados en la sección anterior— son, sin excepción, elementos que tampoco están presentes en el manuscrito original tal como lo envía el autor: son metadatos que el equipo editorial agrega durante el proceso de producción (fechas de historial editorial, identificadores DOI, datos de financiamiento verificados). En consecuencia, la brecha entre Markdown y JATS completo no se ubica en la fase de autoría —donde Markdown es efectivo— sino en la fase de producción editorial, donde herramientas como gbpublisher están diseñadas para intervenir.

Esta observación es, quizás, la más importante del análisis de complementariedad semántica: la división del trabajo entre Markdown y las herramientas de producción editorial especializadas no es una limitación del sistema; es su diseño correcto.

### Dimensión pragmática: Markdown como protocolo de entrada en contextos editoriales con recursos limitados

#### El costo real de la producción XML-JATS

Para evaluar las ventajas pragmáticas de Markdown como protocolo de entrada, es necesario comenzar por una descripción honesta del costo real de la producción XML-JATS en el contexto de las revistas de acceso abierto latinoamericanas. Este costo tiene tres componentes que la literatura especializada documenta con consistencia: el costo de formación, el costo de producción unitaria y el costo de mantenimiento de la calidad [2,5,42].

El **costo de formación** para la producción directa en XML-JATS es significativo. Un operador editorial capaz de producir XML-JATS de calidad suficiente para la indexación en SciELO o PubMed Central, requiere dominar, como mínimo: los principios del marcado XML (estructura jerárquica, atributos, espacios de nombres, validación contra DTD o esquema); la estructura del estándar JATS y sus tres variantes (Publishing, Archiving and Interchange, Article Authoring); el perfil específico de la plataforma de destino (SciELO, JATS4R, PMC); y el manejo de al menos una herramienta de edición XML profesional [2,3]. Este conjunto de competencias no puede adquirirse en un proceso de formación corto: la experiencia en proyectos como SciELO indica que la formación de operadores con competencia plena en producción XML-JATS requiere entre tres y seis meses de práctica supervisada [3].

El **costo de producción unitaria** varía según la complejidad del artículo, pero en flujos de producción manual directa en XML puede oscilar entre cuatro y doce horas de trabajo especializado por artículo, considerando el marcado completo, la validación y la corrección de errores [2,42]. Para una revista que publica cuarenta artículos por año —volumen típico de una revista latinoamericana de tamaño medio— esto representa entre ciento sesenta y cuatrocientas ochenta horas anuales de trabajo técnico especializado, un recurso que la mayoría de los equipos editoriales del modelo diamante simplemente no tiene disponible [5,6].

El **costo de mantenimiento de la calidad** es quizás el menos visible pero no el menos significativo. El marcado XML manual es propenso a errores de consistencia que se acumulan a lo largo del tiempo: elementos aplicados de manera diferente por distintos operadores, convenciones que evolucionan sin documentación, decisiones locales que se desvían de los perfiles de las plataformas de indexación. Estos errores de consistencia son frecuentemente invisibles en la revisión visual del documento pero se manifiestan como rechazos o advertencias en los validadores de las plataformas de indexación [3,31].

#### El perfil del operador editorial en flujos basados en XML directo versus Markdown

Un aspecto que la literatura técnica sobre producción XML-JATS frecuentemente subestima es la consecuencia que el modelo de producción elegido tiene sobre el perfil del operador editorial requerido, y por extensión, sobre la composición y la dinámica de trabajo del equipo editorial en su conjunto [2,5].

En el flujo de producción XML-JATS directa, el operador central debe ser ante todo un especialista técnico en marcado estructurado. Sus competencias críticas son el conocimiento del estándar JATS, el manejo de herramientas de edición XML y la capacidad de validar documentos contra esquemas formales. Sus competencias en edición científica —comprensión de la estructura intelectual del artículo, reconocimiento de convenciones disciplinares, criterio sobre la organización de la información— son secundarias en este flujo, porque el marcado directo en XML absorbe tanta atención cognitiva en la dimensión técnica que deja poco espacio para la dimensión editorial [2,14].

Esta subordinación de las competencias editoriales a las técnicas tiene consecuencias operativas concretas: los equipos editoriales de las revistas latinoamericanas que producen en XML-JATS directo frecuentemente deben optar entre formación técnica intensiva de personal con perfil editorial, o contratación de técnicos especializados que no necesariamente poseen el criterio editorial requerido para interpretar correctamente la estructura semántica de los manuscritos [5,6].

#### La redistribución de competencias que habilita Markdown

Markdown como protocolo de entrada en la cadena
editorial produce una redistribución significativa
de las competencias requeridas en el equipo, que
es pragmáticamente ventajosa para el contexto
latinoamericano por razones que trascienden la
mera reducción del costo de formación técnica.

La sintaxis básica de Markdown puede aprenderse funcionalmente en menos de una jornada de trabajo; la sintaxis extendida relevante para la escritura académica —encabezados jerárquicos, énfasis, tablas, figuras, notas al pie y llamadas a citas con `[@citekey]`— puede dominarse en una o dos jornadas adicionales [13,25,26]. Esto significa que el umbral técnico de entrada al flujo de producción es lo suficientemente bajo como para ser superado por cualquier integrante del equipo editorial con formación universitaria, independientemente de su especialización.

La consecuencia más importante de este umbral bajo no es que cualquier persona pueda hacer cualquier tarea: es que las competencias específicas en edición científica —comprensión de la estructura IMRyD, reconocimiento de la jerarquía de secciones, criterio sobre el marcado semántico correcto de los elementos del artículo— pasan a ser el factor diferencial de calidad en la producción, en lugar de quedar eclipsadas por las competencias técnicas en XML [14].

Un editor que comprende la diferencia entre una sección de métodos y un párrafo de discusión, que reconoce cuándo una lista debe ser ordenada y cuándo no, que sabe que el título de una publicación en la bibliografía no es lo mismo que el nombre de una revista, puede marcar correctamente esas distinciones en Markdown sin necesidad de conocer la sintaxis JATS que las representa. El conocimiento editorial que ya posee se vuelve directamente productivo en el flujo técnico [14,25].

Este principio —que el protocolo de entrada debe **requerir conocimiento editorial antes que conocimiento técnico**— es uno de los fundamentos conceptuales más importantes para el diseño de herramientas de producción editorial destinadas a equipos con el perfil típico de las revistas latinoamericanas del modelo diamante.

#### El modelo de base de datos como arquitectura de gestión de metadatos

Mientras Markdown resuelve con elegancia el problema del marcado estructural del cuerpo del artículo, el problema de la gestión de metadatos —que en JATS se concentra en el elemento `<article-meta>` y sus subelementos— requiere una solución diferente, y la elección de esa solución tiene consecuencias profundas sobre el modelo de trabajo del equipo editorial.

Los flujos basados en herramientas de línea de comandos como Pandoc resuelven este problema mediante el bloque YAML front matter: un encabezado de texto estructurado que el operador escribe directamente en el archivo fuente del documento, especificando campos como título, autores, afiliaciones, palabras clave, DOI y licencia [27,28]. Este modelo tiene la ventaja de mantener todos los datos del artículo en un único archivo de texto, compatible con control de versiones, pero presenta desventajas operativas significativas para equipos editoriales no técnicos: la sintaxis YAML es sensible a la indentación, propensa a errores difíciles de diagnosticar, y no proporciona ningún mecanismo de validación inmediata ni de asistencia en la entrada de datos [13,14].

Para una revista que publica cuarenta artículos anuales, cada uno con entre dos y ocho autores, múltiples afiliaciones, identificadores ORCID, datos de financiamiento, fechas de historial editorial y metadatos de clasificación, la gestión manual de YAML front matter representa una fuente constante de errores e inconsistencias que se propagan directamente al XML-JATS producido [2,31].

La alternativa arquitectónica —implementar la gestión de metadatos mediante una base de datos relacional y formularios de captura— resuelve estos problemas de manera sistemática. En este modelo, los metadatos no se escriben como texto estructurado en el encabezado de un archivo: se capturan mediante formularios validados, se almacenan en una base de datos con esquema definido, y se ensamblan automáticamente en los elementos XML-JATS correspondientes en el momento de la exportación [14]. El operador editorial nunca escribe YAML ni JSON; trabaja con formularios cuyos campos corresponden a conceptos editoriales —autor, afiliación, financiador, fecha de recepción— no a construcciones sintácticas de un lenguaje de marcado [14].

Este modelo de base de datos como repositorio canónico de metadatos no solo reduce los errores de entrada: también habilita funcionalidades que el modelo YAML no puede ofrecer fácilmente, como la reutilización de datos de autores y afiliaciones entre artículos del mismo número, la validación de formatos de ORCID y DOI en el momento de la captura, la gestión de controladores de vocabulario para palabras clave y clasificaciones disciplinares, y la producción de informes de gestión editorial sobre el estado de los artículos en proceso [5,14].

#### El formulario como interfaz natural del trabajo editorial

La elección del formulario como interfaz de captura de datos en una herramienta de producción editorial no es trivial ni meramente estética: responde a una filosofía de diseño que reconoce que el modelo mental del operador editorial es fundamentalmente distinto del modelo mental del programador o del especialista técnico en XML [14,56].

Un operador editorial que trabaja con formularios opera en el dominio de los conceptos editoriales: completa el campo "Nombre del autor", selecciona su institución de un listado validado, introduce el ORCID con verificación de formato, marca si es autor de correspondencia. Estos son exactamente los conceptos que el editor científico maneja cotidianamente, y su representación como campos de formulario es cognitivamente natural [56].

El mismo operador trabajando con YAML front matter debe traducir esos conceptos editoriales a una representación textual estructurada con sintaxis propia: debe recordar que las afiliaciones se referencian por número, que los campos multilínea requieren indentación específica, que los valores con caracteres especiales deben ir entre comillas. Esta traducción es cognitivamente costosa y es una fuente constante de errores que no tienen ninguna relación con el conocimiento editorial del operador [13,14].

La aplicación de escritorio como plataforma de entrega refuerza esta filosofía de diseño. Una aplicación de escritorio puede implementar formularios con validación inmediata, autocompletado basado en datos históricos, listas de selección controlada, indicadores visuales de campos obligatorios y mensajes de error contextuales, todo sin depender de la conectividad a internet ni de la latencia de un servidor remoto [56,57]. Este modelo de interacción, consolidado en décadas de desarrollo de software profesional de escritorio, es más apropiado para el trabajo editorial intensivo que los modelos de interfaz basados en navegador, que imponen restricciones de interacción propias de su arquitectura orientada a documentos web [57].

#### La integración del cuerpo del artículo y los metadatos en un flujo unificado

La arquitectura que combina Markdown para el cuerpo del artículo con una base de datos relacional para los metadatos resuelve de manera elegante la tensión entre las ventajas del texto plano y las exigencias de la gestión de datos complejos [14].

En este modelo unificado, el flujo de trabajo del operador editorial procede en etapas naturales que corresponden a las fases del proceso editorial real. En la fase de recepción y registro, los metadatos administrativos del artículo —autoría, afiliaciones, financiamiento, fechas— se capturan mediante formularios y se almacenan en la base de datos. En la fase de edición de contenido, el cuerpo del artículo se trabaja en Markdown, con marcado estructural que refleja el conocimiento editorial del operador. En la fase de producción, la herramienta ensambla el XML-JATS completo combinando el cuerpo procesado desde Markdown con los metadatos recuperados de la base de datos, sin que el operador necesite intervenir en ese ensamblaje técnico [14].

Este flujo unificado tiene una propiedad que merece destacarse: en ningún momento del proceso el operador necesita conocer la estructura interna del XML-JATS que se está produciendo. El YAML que eventualmente requiera Pandoc como puente técnico es un artefacto generado internamente por la herramienta a partir de los datos de la base de datos, invisible al usuario. El JSON que alimenta el procesador de citas es igualmente un artefacto de exportación desde la base de datos, no un archivo que el operador crea o edita directamente [14,27].

Esta invisibilidad de los artefactos técnicos intermedios es un principio de diseño fundamental: el operador editorial trabaja siempre en el dominio de los conceptos editoriales, nunca en el dominio de los formatos técnicos de intercambio.

#### Markdown y el control de versiones colaborativo

Una ventaja pragmática de Markdown que recibe atención creciente en la literatura sobre flujos editoriales abiertos es su compatibilidad nativa con los sistemas de control de versiones, particularmente git [35,43].

Los sistemas de control de versiones como git están diseñados para trabajar con texto plano: pueden registrar con precisión qué cambió entre versiones de un archivo, mostrar diferencias línea a línea, fusionar cambios de múltiples colaboradores y revertir a estados anteriores con facilidad. Estas capacidades son exactamente las que se necesitan en un flujo editorial colaborativo, donde múltiples actores —autores, editores, revisores, correctores— introducen cambios sucesivos en el mismo documento [35,43].

Los formatos binarios o cuasibinarios —Microsoft Word, Adobe InDesign, incluso el XML de JATS cuando se edita directamente— son técnicamente compatibles con git pero pierden gran parte de sus ventajas: las diferencias entre versiones son difíciles de leer, los conflictos de fusión son complejos de resolver y el historial de cambios tiene valor limitado para la revisión editorial [43,44].

Markdown, por ser texto plano con marcas mínimas y predecibles, produce historiales de cambio legibles e informativos: un revisor puede ver exactamente qué párrafos fueron modificados entre la versión dos y la versión tres del manuscrito, qué referencias fueron agregadas o eliminadas, qué secciones fueron reorganizadas. Esta trazabilidad es valiosa no solo para la gestión del proceso editorial sino también para la transparencia del proceso de revisión en el contexto de la ciencia abierta [35,36,43].

#### Markdown y la preservación a largo plazo

La compatibilidad de Markdown con los principios de preservación digital a largo plazo es otra dimensión pragmática que merece atención sistemática [44,45].

Los principios de preservación digital establecen que los formatos de archivo de largo plazo deben ser preferentemente de texto plano, abiertos, bien documentados y procesables sin dependencia de software propietario [44]. Markdown cumple todos estos criterios de manera más directa que Word o que los formatos PDF/A, y de manera comparable a XML, con la ventaja adicional de ser legible por humanos sin ningún procesamiento.

Esta consideración es relevante para las revistas latinoamericanas por una razón específica: la continuidad institucional de los proyectos editoriales del modelo diamante no está garantizada a largo plazo. Cuando una revista cambia de institución anfitriona, cambia su equipo editorial o migra a una nueva plataforma de publicación, los archivos históricos en formatos propietarios o dependientes de software específico pueden volverse inaccesibles [5,45]. Un cuerpo de artículo en Markdown es, en este sentido, significativamente más robusto frente a los riesgos de la obsolescencia tecnológica y la discontinuidad institucional que cualquier formato binario o dependiente de una plataforma específica.

En el modelo de base de datos que complementa el cuerpo en Markdown, la preservación de los metadatos queda garantizada por la exportación a XML-JATS como formato de archivo canónico: el XML producido por la herramienta es el artefacto de preservación de largo plazo, que contiene tanto el cuerpo como los metadatos en un formato completamente abierto y documentado [7,44].

#### Evidencia empírica de eficacia en revistas reales

La literatura disponible ofrece evidencia empírica, aunque todavía limitada y dispersa, sobre la eficacia de flujos basados en Markdown para la producción de XML científico en revistas reales.

El caso más documentado es el del Journal of Open Source Software (JOSS), que desde su fundación en 2016 ha publicado más de tres mil artículos utilizando un flujo completamente basado en Markdown, con generación automática de PDF y metadatos estructurados mediante Pandoc [39]. El modelo de JOSS demuestra que un flujo Markdown-first puede escalar a volúmenes editoriales significativos con equipos pequeños y costos operativos bajos, aunque en un contexto disciplinar —software académico— donde la familiaridad con texto plano es alta entre los autores.

Himmelstein *et al*. (2019) documentaron el flujo Manubot en la producción de un manuscrito colaborativo de gran escala, con cincuenta y cinco contribuidores y un historial de versiones transparente en GitHub [36]. Su análisis mostró que el flujo basado en Markdown y git permitió una colaboración distribuida efectiva con un costo de coordinación significativamente menor que el esperado para un manuscrito de esa escala.

En el contexto latinoamericano específicamente, la evidencia empírica publicada es escasa, lo que representa tanto una limitación del presente análisis como un área de investigación que merece atención prioritaria. Los informes del programa SciELO mencionan exploración de flujos alternativos al marcado XML directo, pero sin datos publicados sobre resultados comparativos de calidad o eficiencia [3,40]. Esta escasez de evidencia contextualizada refuerza la pertinencia del desarrollo de herramientas específicamente diseñadas para el ecosistema latinoamericano, cuya documentación sistemática pueda contribuir a cubrir esa brecha.

### Proyección futura: convergencia entre Markdown, ciencia abierta y estándares de publicación estructurada

#### La agenda de la ciencia abierta y sus implicaciones para los flujos editoriales

La ciencia abierta —entendida no solo como acceso abierto a publicaciones sino como transparencia de datos, métodos, código y proceso investigativo— está reconfigurando los flujos editoriales científicos de maneras que son sistemáticamente favorables a Markdown como protocolo de entrada [46,47].

Las directrices de ciencia abierta de las principales agencias de financiamiento —incluyendo la Comisión Europea a través de Horizon Europe, los National Institutes of Health en Estados Unidos, y el Consejo Nacional de Humanidades, Ciencias y Tecnologías (CONAHCYT) en México— convergen en la exigencia de que los productos de investigación, incluyendo las publicaciones, sean producidos y archivados en formatos abiertos, interoperables y preservables a largo plazo [46,47,48]. Markdown, como formato de texto plano abierto, cumple estas exigencias de manera más directa que los formatos propietarios de procesadores de texto.

#### Los artículos ejecutables y el paradigma de la reproducibilidad

El concepto de artículo ejecutable —un documento científico que integra la narrativa, el código analítico y los datos de manera que los resultados puedan ser reproducidos y verificados por el lector— está ganando tracción en múltiples disciplinas y plataformas [49,50].

Iniciativas como Binder, Code Ocean y el programa de artículos reproducibles de *eLife* y *PLOS* convergen en un modelo donde el artículo científico no es solo un texto formateado sino un artefacto computacional ejecutable [49,50,51]. En este paradigma emergente, el formato del artículo fuente es inevitablemente texto plano: Markdown, Jupyter Notebook o Quarto. Markdown en sus formas extendidas es el único formato que puede servir simultáneamente como fuente para un artículo ejecutable y como protocolo de entrada para un flujo de producción JATS [29,30,49].

#### La evolución del estándar JATS y su relación con Markdown

El estándar JATS no es estático: NISO mantiene un proceso de actualización regular que responde a las necesidades emergentes del ecosistema de la publicación científica [7,22,52]. Dos tendencias son identificables en las versiones recientes:

La **expansión de los metadatos de transparencia y reproducibilidad** incorpora elementos para declaraciones de disponibilidad de datos, materiales y código; identificadores de protocolos preregistrados; y declaraciones de transparencia editorial [52]. Estos metadatos corresponden directamente a campos que pueden capturarse mediante formularios validados en una base de datos editorial y ensamblarse en el XML-JATS sin intervención técnica del operador.

La **mayor integración con identificadores persistentes** —DOI, ORCID, ROR, RAiD— se profundiza en versiones recientes [52,53]. La validación de estos identificadores en el momento de la captura —funcionalidad natural en un formulario de base de datos— es significativamente más difícil de garantizar en flujos basados en edición manual de YAML o XML.

#### La iniciativa JATS4R y la estandarización del JATS canónico

JATS for Requirements (JATS4R) produce recomendaciones de uso de JATS que maximizan la interoperabilidad entre plataformas [31]. JATS4R reconoce que el estándar es suficientemente flexible como para que dos documentos válidos contra el DTD presenten diferencias estructurales significativas que dificultan el procesamiento automatizado, y aspira a reducir esa variabilidad mediante un perfil canónico [31].

Las recomendaciones publicadas por JATS4R sobre el marcado de autores, afiliaciones, referencias bibliográficas y fechas son compatibles con lo que puede producirse mediante la cadena Pandoc --> JATS alimentada con datos de una base de datos editorial bien estructurada. A medida que JATS4R consolida su influencia en las prácticas de las plataformas de indexación, la brecha entre el JATS producido por herramientas que implementan este flujo y el JATS requerido por esas plataformas tiende a reducirse sistemáticamente.

#### La inteligencia artificial generativa y su impacto en el flujo Markdown --> JATS

El impacto de los sistemas de inteligencia artificial generativa en los flujos de producción editorial científica es una dimensión emergente que no puede ignorarse en un análisis prospectivo [54,55].

Los sistemas de lenguaje de gran escala producen texto en Markdown de manera nativa cuando se les solicita contenido estructurado [54], lo que refuerza la posición de Markdown como protocolo de intercambio en flujos que incorporen asistencia automatizada para redacción de resúmenes estructurados, verificación de metadatos o detección de inconsistencias editoriales.

La conversión asistida desde manuscritos en Word hacia Markdown estructurado es igualmente un candidato natural para la asistencia mediante IAG [55]: sistemas con capacidad de comprensión semántica podrían identificar la estructura intelectual del documento y producir Markdown correctamente jerarquizado con mayor precisión que las herramientas de conversión sintáctica actualmente disponibles. Estas aplicaciones son prospectivas más que establecidas, y se mencionan aquí como tendencias a observar, no como desarrollos consolidados.

#### Principios de diseño implementados: gbpublisher como modelo de referencia

El análisis de las tendencias documentadas en esta sección permite articular un conjunto de principios de diseño que no son aspiraciones para el horizonte 2025-2030 sino decisiones arquitectónicas ya implementadas o en implementación activa en gbpublisher, la herramienta de producción editorial de código abierto desarrollada específicamente para el contexto latinoamericano.

**Principio 1: la base de datos relacional como repositorio canónico de metadatos.** Todos los metadatos del artículo —de autoría, afiliación, financiamiento, historial editorial, clasificación, gobernanza de la revista y referencias bibliográficas— se capturan, almacenan y gestionan en una base de datos MySQL con esquema diseñado para correspondencia directa con los elementos de `<article-meta>` y `<ref-list>` en JATS. Este repositorio unificado cumple una función que en los flujos editoriales convencionales requiere la intervención de aplicaciones externas especializadas —gestores de referencias como Zotero, Mendeley o JabRef— con las fricciones de integración que esa externalidad implica: sincronización entre aplicaciones, exportación e importación de archivos en formatos intermedios (BibTeX, CSL-JSON, RIS) y dependencia de que el operador mantenga actualizada su biblioteca personal de referencias.

En gbpublisher, las referencias bibliográficas se registran directamente en la base de datos editorial mediante los mismos formularios de captura que gestionan los demás metadatos del artículo. Cada referencia registrada queda disponible para su reutilización en cualquier artículo posterior que la cite, exactamente de la misma manera en que los datos de un autor o de una institución registrados una vez quedan disponibles para todos los artículos en que esa persona o institución aparezca. Este principio de reutilización de metadatos —tanto de autoría como bibliográficos— reduce el trabajo de captura de manera acumulativa a lo largo del tiempo: una revista que lleva varios números de producción en gbpublisher tiene ya registrados los datos completos de sus autores más frecuentes y de las fuentes más citadas en su disciplina, y el operador los recupera mediante búsqueda, no los reintroduce manualmente en cada artículo.

El YAML, el JSON bibliográfico y cualquier otro artefacto de intercambio técnico requerido por la cadena de conversión son productos de exportación de esa base de datos, generados internamente por la aplicación y completamente invisibles al operador editorial. Este principio elimina dos clases de errores que son endémicos en los flujos convencionales: los errores de sintaxis en archivos de configuración de texto, y los errores de inconsistencia entre la referencia tal como aparece citada en el cuerpo del artículo y la entrada bibliográfica correspondiente en la lista de referencias. Al gestionar ambos elementos desde la misma base de datos, gbpublisher garantiza esa consistencia de manera estructural, no mediante la revisión manual.

**Principio 2: el formulario como interfaz nativa del trabajo editorial.** La captura de todos los datos del proceso editorial —desde el registro inicial del manuscrito hasta la asignación de identificadores de publicación— se realiza mediante formularios diseñados para reflejar los conceptos y flujos de trabajo propios de la edición científica. El operador trabaja siempre en el dominio editorial: completa campos cuyos nombres son "autor de correspondencia", "institución financiadora", "fecha de aceptación", no atributos XML ni claves YAML. Esta decisión de diseño reduce el umbral técnico de entrada al sistema y permite que el conocimiento determinante para la calidad del resultado sea el conocimiento editorial, no el conocimiento técnico en estándares de marcado.

**Principio 3: integración de operadores con perfil editorial diverso.** La arquitectura de gbpublisher está diseñada para que distintos roles del equipo editorial —editor, corrector, maquetador, gestor de metadatos— puedan participar en el flujo de producción con las herramientas apropiadas a su perfil, sin necesidad de que ninguno de ellos domine la cadena técnica completa. El editor científico que comprende la estructura intelectual del artículo puede trabajar el marcado Markdown con plena autonomía. El gestor de metadatos que conoce las convenciones de autoría e identificadores persistentes puede operar los formularios de registro con plena autonomía. El responsable técnico que conoce los perfiles de las plataformas de indexación puede configurar las plantillas de exportación con plena autonomía. Ninguno necesita conocer el dominio de los otros para hacer su parte correctamente.

**Principio 4: el JATS canónico como artefacto de exportación, no como formato de trabajo.** JATS es el destino del flujo de producción, no su medio. Los operadores editoriales nunca trabajan directamente sobre XML-JATS: este se genera como exportación final —o como paso intermedio hacia exportaciones específicas de plataforma— a partir de la combinación del cuerpo en Markdown y los metadatos en la base de datos. Esta separación entre el formato de trabajo y el formato de publicación es el núcleo de la solución que gbpublisher propone al problema de la fragmentación editorial: un único proceso de producción, con herramientas accesibles para equipos con perfil editorial, que produce JATS de calidad suficiente para la indexación en múltiples plataformas a partir de un único archivo maestro.

**Principio 5: la aplicación de escritorio como plataforma de entrega apropiada.** La implementación de gbpublisher como aplicación de escritorio —desarrollada en Gambas 3 sobre Linux— no es una limitación tecnológica sino una decisión de diseño fundamentada. Las aplicaciones de escritorio pueden implementar formularios con validación inmediata, interacción fluida con el sistema de archivos local, procesamiento sin dependencia de conectividad a internet y una experiencia de usuario consistente independiente de las variaciones de los navegadores web. Para equipos editoriales que trabajan con volúmenes sostenidos de artículos en entornos institucionales que no siempre garantizan conectividad estable, este modelo de entrega es más apropiado que las alternativas basadas en navegador [56,57].

## 4. Discusión: la convergencia como argumento central

Los resultados presentados en las secciones anteriores permiten articular con precisión el argumento central de este artículo: Markdown es el protocolo de entrada óptimo para la producción de JATS canónico no por razones de conveniencia circunstancial ni por la popularidad creciente del formato en la comunidad técnica, sino por razones estructurales que se articulan en cinco dimensiones complementarias que este trabajo ha analizado sistemáticamente.

La dimensión histórica establece que Markdown y JATS comparten una genealogía principial común: ambos son expresiones del principio de separación entre contenido y presentación que GML formuló en 1969 y que SGML formalizó en 1986. Esta genealogía compartida no es un argumento de autoridad; es la explicación de por qué la compatibilidad semántica entre ambos formatos no es accidental. Dos sistemas de marcado construidos sobre el mismo principio fundacional producen representaciones que, aunque difieren en exhaustividad, son estructuralmente conmensurables [18,19,20,25].

La dimensión del estado del arte establece que la cadena de herramientas Markdown --> JATS ha alcanzado una madurez suficiente para uso en producción editorial real. Pandoc, con más de quince años de desarrollo activo y soporte explícito para JATS desde 2020, es una infraestructura estable y bien documentada [27,28]. Quarto extiende esa infraestructura hacia el paradigma de la ciencia reproducible con soporte creciente para publicación formal [30]. Las brechas identificadas —perfilado de plataforma, metadatos complejos, elementos semánticos específicos de dominio— son brechas conocidas, acotadas y abordables mediante herramientas complementarias, no limitaciones fundamentales del enfoque.

La dimensión de la complementariedad semántica establece que  Markdown cubre, mediante correspondencias directas y bien definidas, el espacio semántico de los elementos que aparecen en la gran mayoría de los artículos científicos estándar. El principio de **semántica suficiente** —articulado anteriormente— permite reformular la pregunta:

> no se trata de si Markdown captura el cien por ciento de JATS, sino de si captura lo necesario para que una cadena de conversión (*pipeline*) bien diseñada complete el trabajo.

La evidencia analizada indica que la respuesta es afirmativa para la gran mayoría de los casos editoriales prácticos [7,27,28].

La dimensión pragmática establece que Markdown, combinado con una arquitectura de base de datos para la gestión de metadatos y una interfaz de formularios para la captura de datos, produce un modelo de trabajo que es más accesible, más consistente y más apropiado para equipos con perfil editorial que cualquier alternativa basada en edición directa de XML o de archivos de configuración en texto estructurado [14,56]. La ventaja pragmática decisiva no es la simplicidad de la sintaxis Markdown en sí misma: es la redistribución de competencias que ese modelo habilita, poniendo el conocimiento editorial —no el técnico— en el centro del proceso de producción.

La dimensión prospectiva establece que las tendencias convergentes de la ciencia abierta, los artículos ejecutables, la evolución de JATS hacia mayor expresividad de metadatos de transparencia y la consolidación de JATS4R como perfil canónico son todas tendencias que refuerzan, no erosionan, la posición de Markdown como protocolo de entrada en el ecosistema de la publicación científica estructurada [46,47,49,52].

### Implicaciones para la literatura sobre flujos editoriales científicos

Este artículo contribuye a la literatura sobre flujos editoriales científicos en al menos tres dimensiones que merecen señalarse explícitamente.

**Primera contribución: la articulación del principio de semántica suficiente.** La literatura técnica sobre producción XML-JATS frecuentemente evalúa los formatos de entrada en términos de exhaustividad: ¿cuántos elementos JATS puede representar este formato de entrada? Este criterio lleva a la conclusión de que ningún formato ligero es completamente adecuado, porque ninguno cubre el cien por ciento de los elementos del estándar. El principio de semántica suficiente desplaza el criterio hacia la pregunta funcionalmente relevante: ¿cubre este formato los elementos que aparecen en la mayoría de los artículos reales, con la profundidad necesaria para que la cadena de conversión produzca JATS de calidad suficiente para la indexación? Reformulado así, Markdown supera el criterio de suficiencia con claridad [14,27,28].

**Segunda contribución: la separación conceptual entre el problema del cuerpo y el problema de los metadatos.** La literatura tiende a tratar la producción de JATS como un problema único, cuando en realidad involucra dos problemas con características radicalmente distintas: el marcado estructural del cuerpo del artículo y la gestión de metadatos complejos. Markdown es una solución óptima para el primero; una base de datos relacional con formularios de captura es una solución óptima para el segundo. La articulación de esta separación conceptual, y la identificación de la arquitectura que combina ambas soluciones en un flujo unificado, es una contribución analítica de este trabajo que tiene implicaciones directas para el diseño de herramientas editoriales [14,56].

**Tercera contribución: la centralidad del perfil del operador como variable de diseño.** Los análisis técnicos de flujos editoriales frecuentemente tratan al operador humano como una variable secundaria, posterior al diseño del sistema. Este artículo argumenta que el perfil del operador —sus competencias, su modelo mental del proceso editorial, su familiaridad con distintos tipos de herramientas— debe ser una variable primaria en el diseño de flujos y herramientas editoriales. Un flujo que requiera competencias técnicas que los equipos editoriales típicos no poseen ni pueden desarrollar razonablemente es un mal flujo, independientemente de sus virtudes técnicas. Markdown, combinado con la arquitectura de base de datos y formularios, es un buen flujo precisamente porque sus exigencias sobre el operador están alineadas con las competencias que los equipos editoriales ya poseen [5,14,56].

### Limitaciones del análisis

Tres limitaciones del presente análisis deben señalarse con precisión para contextualizar correctamente sus conclusiones.

**Primera limitación: la escasez de evidencia empírica latinoamericana.** Gran parte de la evidencia empírica disponible sobre flujos Markdown --> JATS proviene de contextos anglosajones —JOSS, Manubot, Quarto— donde el perfil de los equipos editoriales y las exigencias de las plataformas de indexación difieren del contexto latinoamericano. La aplicabilidad de esa evidencia al contexto de las revistas SciELO y Redalyc es plausible pero no ha sido verificada empíricamente de manera sistemática [3,5,40].

**Segunda limitación: la especificidad disciplinar.** El análisis de complementariedad semántica se basa en el artículo científico estándar con estructura IMRyD. Artículos en humanidades, ciencias sociales cualitativas y algunas disciplinas de las ciencias de la salud presentan estructuras significativamente distintas, con elementos como estudios de caso, extractos de entrevistas, notación musical, transcripciones fonéticas o representaciones de lenguas con escrituras no latinas, cuya representación en Markdown y en JATS requiere análisis específicos no cubiertos en este trabajo [7,22].

**Tercera limitación: la velocidad de evolución del ecosistema.** El ecosistema de herramientas descrito antes evoluciona con rapidez. Algunas afirmaciones sobre el estado actual de Pandoc, Quarto y las iniciativas institucionales pueden quedar desactualizadas en un horizonte de dos a tres años. Esta limitación es inherente a los análisis del estado del arte en dominios de desarrollo tecnológico activo y no invalida las conclusiones de fondo, que se apoyan en principios arquitectónicos más estables que en características de versiones específicas de herramientas.

### Líneas de investigación futura

El análisis desarrollado en este artículo permite identificar al menos cuatro líneas de investigación futura que contribuirían a fundamentar empíricamente las tesis aquí argumentadas y a extender su alcance.

**Línea 1: evaluación comparativa de calidad XML en flujos latinoamericanos.** Un estudio comparativo que evaluara la calidad del XML-JATS producido mediante distintos flujos de producción —XML directo; Word --> SciELO PC Programs; Word --> Pandoc --> JATS; Markdown --> Pandoc --> JATS— en una muestra representativa de revistas SciELO o Redalyc, con métricas de validación formal, completitud de metadatos y tasa de errores por artículo, proporcionaría evidencia empírica directamente relevante para las decisiones de adopción de los programas de indexación latinoamericanos.

**Línea 2: estudios de adopción y usabilidad en equipos editoriales reales.** Estudios cualitativos y cuantitativos sobre la experiencia de adopción de flujos basados en Markdown por parte de equipos editoriales latinoamericanos —con distintos perfiles disciplinares, tamaños y niveles de capacidad técnica— permitirían identificar barreras de adopción no previstas en el análisis técnico y refinar las recomendaciones de diseño de herramientas y procesos de formación.

**Línea 3: cobertura semántica en disciplinas no estándar.** Un análisis sistemático de la cobertura semántica de Markdown --> JATS en artículos de humanidades digitales, lingüística, musicología y otras disciplinas con necesidades de representación no cubiertas por la estructura IMRyD estándar contribuiría a delimitar con precisión los alcances y límites del enfoque.

**Línea 4: evaluación longitudinal de preservación.** Un estudio longitudinal que siguiera la accesibilidad y la integridad de artículos archivados en Markdown versus formatos alternativos en el contexto de migraciones de plataforma, cambios institucionales y obsolescencia de herramientas proporcionaría evidencia empírica sobre las ventajas de preservación a largo plazo atribuidas al texto plano en la literatura teórica.

## 5. Conclusiones

El análisis desarrollado en este artículo permite formular cinco conclusiones que responden a la pregunta de investigación planteada en la introducción.

**Primera conclusión.** Markdown y JATS no son simplemente formatos técnicamente compatibles: son expresiones del mismo principio fundacional del pensamiento sobre documentos estructurados, el principio de separación entre contenido y presentación formulado en la tradición GML/SGML. Esta compatibilidad de origen explica por qué la cadena de conversión Markdown --> JATS no es una traducción entre sistemas heterogéneos sino una proyección entre dos niveles de exhaustividad del mismo paradigma semántico.

**Segunda conclusión.** La cadena de herramientas Markdown --> JATS ha alcanzado madurez de producción. Pandoc, con soporte explícito para JATS desde 2020, proporciona la infraestructura de conversión. Las brechas residuales —perfilado de plataforma, metadatos de transparencia, elementos semánticos específicos de dominio— son brechas acotadas y abordables mediante herramientas complementarias, y definen con precisión el espacio de diseño de aplicaciones editoriales especializadas.

**Tercera conclusión.** Markdown cubre, mediante correspondencias directas y bien definidas, el espacio semántico de los elementos presentes en la gran mayoría de los artículos científicos estándar. El principio de semántica suficiente —que desplaza el criterio de evaluación desde la exhaustividad hacia la suficiencia funcional— permite concluir que Markdown supera el umbral requerido para servir como protocolo de entrada efectivo hacia JATS canónico.

**Cuarta conclusión.** La ventaja pragmática decisiva de Markdown en el contexto latinoamericano no reside en su simplicidad sintáctica *per se*, sino en la redistribución de competencias que habilita: al reducir el umbral técnico de entrada al flujo de producción, coloca el conocimiento editorial —que los equipos de las revistas del modelo diamante ya poseen— como el factor determinante de la calidad del resultado. Una arquitectura que combina Markdown para el cuerpo del artículo con una base de datos relacional para los metadatos, con formularios como interfaz de captura y una aplicación de escritorio como plataforma de entrega, implementa este principio de manera operativamente efectiva.

**Quinta conclusión.** Las tendencias convergentes de la ciencia abierta, los artículos ejecutables, la evolución del estándar JATS y la consolidación de JATS4R refuerzan sistemáticamente la posición de Markdown como protocolo de entrada en el horizonte de la publicación científica estructurada. Las herramientas que implementen este enfoque —y gbpublisher es un ejemplo de ello en el contexto latinoamericano— están alineadas con la dirección de evolución del ecosistema, no en tensión con ella.

En conjunto, estas cinco conclusiones permiten responder afirmativamente y con fundamentos articulados a la pregunta de investigación: **¿Por qué Markdown constituye el protocolo de entrada óptimo para la producción de JATS canónico en el contexto de la publicación científica de acceso abierto, particularmente en América Latina?**, no por razones de moda tecnológica, sino por razones estructurales, pragmáticas y prospectivas que este artículo ha documentado de manera sistemática.

## Referencias

[1] Hahn, M. & Subramanian, S. (2019). "The challenge of XML authoring in scientific publishing: a survey of editorial practices". *Journal of Information Science* 45(3):312-327.

[2] Piez, Wendell (2001). "How to write structured documents: markup theory and practice". *Markup Languages: Theory and Practice* 3(3):195-217.

[3] Packer, Abel L., Cop, Nandita, Luccisano, Ana, Ramalho, Abdelaziz & Spinak, Ernesto (eds.) (2014). *SciELO 15 años: abriendo el acceso a la comunicación científica*. São Paulo: BIREME/OPAS/OMS.

[4] Aguado-López, Eduardo & Becerril-García, Arianna (2006). "Redalyc una década de acceso abierto: ¿y el modelo de negocio?". En: Babini, Dominique & Fraga, Jorge (eds.). *Edición electrónica, bibliotecas virtuales y portales para las ciencias sociales en América Latina y El Caribe*. Buenos Aires: CLACSO. p. 117-137.

[5] Becerril-García, Arianna & Aguado-López, Eduardo (2019). "El futuro de la comunicación científica en América Latina: hacia una ciencia abierta". *Información, Cultura y Sociedad* (41):23-40.

[6] Alperin, Juan Pablo & Fischman, Gustavo (eds.) (2015). *Hecho en Latinoamérica: acceso abierto, revistas académicas e innovaciones regionales*. Buenos Aires: CLACSO.

[7] Lapeyre, Jeff & Usdin, Tommie (2012). "JATS: Journal Article Tag Suite". En: *Proceedings of the 2012 XML Conference and Exhibition*; 2012 ago; Montréal, Canadá. Montréal: IDEAlliance.

[8] National Center for Biotechnology Information (NCBI) (2023). *PubMed Central: technical documentation for journal publishers* [Internet]. Bethesda: NCBI. [citado 2024 feb]. Disponible en: [https://www.ncbi.nlm.nih.gov/pmc/pub/filespec-xml/](https://www.ncbi.nlm.nih.gov/pmc/pub/filespec-xml/)

[9] Mulberry Technologies (2003). *NLM Journal Publishing DTD: design and development* [Internet]. Rockville: Mulberry Technologies. [citado 2024 feb]. Disponible en: [https://jats.nlm.nih.gov/](https://jats.nlm.nih.gov/)

[10] Spinak, Ernesto (1996). *Diccionario enciclopédico de bibliometría, cienciometría e informetría*. Montevideo: UNESCO.

[11] Baird, N. (2018). "The challenges of converting Word documents to JATS XML: an editorial perspective". *Journal of Electronic Publishing* 21(1).

[12] Thoma, George (2003). "The utilization of XML for document management in biomedical literature". *Journal of the American Medical Informatics Association* 10(5):482-489.

[13] MacFarlane, John (2006). *Pandoc: a universal document converter* [Internet]. Berkeley: University of California. [citado 2024 feb]. Disponible en: [https://pandoc.org](https://pandoc.org)

[14] Krewinkel, Albert & Winkler, Robert (2017). "Formatting open science: agilely creating multiple document formats for academic manuscripts with Pandoc Scholar". *PeerJ Computer Science* 3:e112. DOI: [10.7717/peerj-cs.112](https://doi.org/10.7717/peerj-cs.112)

[15] Aguado-López, Eduardo & Becerril-García, Arianna (2016). "Redalyc.org: una infraestructura abierta para la ciencia abierta latinoamericana". *Revista Española de Documentación Científica* 39(4):e151.

[16] Grant, Maria J. & Booth, Andrew (2009). "A typology of reviews: an analysis of 14 review types and associated methodologies". *Health Information and Libraries Journal* 26(2):91-108.

[17] Ferrari, Rosanne (2015). "Writing narrative style literature reviews". *Medical Writing* 24(4):230-235.

[18] Goldfarb, Charles F., Mosher, Edward & Lorie, Raymond A. (1969). "An online system for integrated text processing". En: *Proceedings of the 1969 American Society for Information Science Annual Meeting*; 1969; San Francisco. Washington: ASIS. p. 147-150.

[19] Goldfarb, Charles F. (1990). *The SGML Handbook*. Oxford: Oxford University Press.

[20] International Organization for Standardization (1986). *ISO 8879:1986. Information processing: text and office systems: Standard Generalized Markup Language (SGML)*. Ginebra: ISO.

[21] Bray, Tim, Paoli, Jean, Sperberg-McQueen, C. Michael, Maler, Eve & Yergeau, François (eds.) (2008). *Extensible Markup Language (XML) 1.0* [Internet]. 5a ed. Cambridge: W3C. [citado 2024 feb]. Disponible en: [https://www.w3.org/TR/xml/](https://www.w3.org/TR/xml/)

[22] National Information Standards Organization (2019). *ANSI/NISO Z39.96-2019. JATS: Journal Article Tag Suite* [Internet]. Baltimore: NISO. [citado 2024 feb]. Disponible en: [https://www.niso.org/publications/ansiniso-z3996-2019-jats-journal-article-tag-suite](https://www.niso.org/publications/ansiniso-z3996-2019-jats-journal-article-tag-suite)

[23] Knuth, Donald E. (1984). *The TeXbook*. Addison-Wesley.

[24] Lamport, Leslie (1986). *LaTeX: A Document Preparation System*. Addison-Wesley.

[25] Gruber, John (2004). *Markdown* [Internet]. Daring Fireball. [citado 2024 feb]. Disponible en: [https://daringfireball.net/projects/markdown/](https://daringfireball.net/projects/markdown/)

[26] MacFarlane, John, Rosenthal, Albert, Fortin, Nicolas & Krewinkel, Albert (2024). *Pandoc Markdown* [Internet]. En: *Pandoc User's Guide*. [citado 2024 feb]. Disponible en: [https://pandoc.org/MANUAL.html](https://pandoc.org/MANUAL.html)

[27] MacFarlane, John (2024). *Pandoc User's Guide* [Internet]. Berkeley: University of California. [citado 2024 feb]. Disponible en: [https://pandoc.org/MANUAL.html](https://pandoc.org/MANUAL.html)

[28] MacFarlane, John (2024). *A Haskell implementation of Pandoc* [Internet]. GitHub. [citado 2024 feb]. Disponible en: [https://github.com/jgm/pandoc](https://github.com/jgm/pandoc)

[29] Xie, Yihui, Allaire, J.J. & Grolemund, Garrett (2018). *R Markdown: The Definitive Guide*. Boca Raton: CRC Press / Taylor & Francis.

[30] Allaire, J.J., Teague, Charles, Scheidegger, Carlos, Xie, Yihui & Dervieux, Christophe (2022). *Quarto* [Internet]. Boston: Posit. [citado 2024 feb]. Disponible en: [https://quarto.org](https://quarto.org)

[31] JATS4R Working Group (2019). *JATS for Requirements: recommendations* [Internet]. JATS4R. [citado 2024 feb]. Disponible en: [https://jats4r.org/](https://jats4r.org/)

[32] Zelle, M. (2023). *CSL: Citation Style Language specification* [Internet]. GitHub. [citado 2024 feb]. Disponible en: [https://docs.citationstyles.org/](https://docs.citationstyles.org/)

[33] D'Arcus, Bruce & Giasson, Frank (2009). "Bibliographic metadata for the semantic web using the Citation Style Language". *D-Lib Magazine* 15(1/2). DOI: [10.1045/january2009-darcus](https://doi.org/10.1045/january2009-darcus)

[34] Scheidegger, Carlos & Teague, Charles (2023). *Quarto journal templates for JATS* [Internet]. Boston: Posit. [citado 2024 feb]. Disponible en: [https://quarto.org/docs/journals/](https://quarto.org/docs/journals/)

[35] Himmelstein, Daniel S., Romero, Antoine R., Levernier, Jacob G., Munro, Thomas A., McLaughlin, Stephen R., Teber, Ivet et al. (2019). "Manubot: open collaborative writing with Markdown". *Figshare*. DOI: [10.22541/au.153232683.27486273](https://doi.org/10.22541/au.153232683.27486273)

[36] Himmelstein, Daniel S., Romero, Antoine R., Levernier, Jacob G., Munro, Thomas A., McLaughlin, Stephen R., Teber, Ivet et al. (2018). "Sci-Hub provides access to nearly all scholarly literature". *eLife* 7:e32822. DOI: [10.7554/eLife.32822](https://doi.org/10.7554/eLife.32822)

[37] Willighagen, Egon, Ó Broin, Pádraig & Lindemann, C. (2018). "Texture: a visual editor for JATS XML". En: *Proceedings of the 2018 JATS-Con*; 2018 oct; Bethesda. Bethesda: NCBI.

[38] Bentley, Nokome, Buchtala, O. & Hauber, M. [verificar nombre completo] (2018). "Stencila: structured scientific documents with executable code cells". En: *Proceedings of the 2018 JATS-Con*; 2018 oct; Bethesda. Bethesda: NCBI.

[39] Smith, Arfon M., Niemeyer, Kyle E., Katz, Daniel S., Barba, Lorena A., Githinji, George, Gymrek, Melissa et al. (2018). "Journal of Open Source Software (JOSS): design and first-year review". *PeerJ Computer Science* 4:e147. DOI: [10.7717/peerj-cs.147](https://doi.org/10.7717/peerj-cs.147)

[40] Packer, Abel L. (2020). "SciELO Preprints em operação e evolução do fluxo de publicação nos periódicos SciELO". *SciELO Blog* [Internet]. [citado 2024 feb]. Disponible en: [https://blog.scielo.org/](https://blog.scielo.org/)

[41] Spinak, Ernesto (2015). "Errores y tipos de errores en la composición XML de artículos científicos para SciELO". *SciELO en Perspectiva* [Internet]. [citado 2024 feb]. Disponible en: [https://blog.scielo.org/](https://blog.scielo.org/)

[42] Torok, J. (2020). "Production workflows for small scholarly publishers: a practical guide". *Journal of Scholarly Publishing* 51(3):145-162.

[43] Ram, Karthik (2013). "git can facilitate greater reproducibility and increased transparency in science". *Source Code for Biology and Medicine* 8:7. DOI: [10.1186/1751-0473-8-7](https://doi.org/10.1186/1751-0473-8-7)

[44] Rosenthal, David S. (2010). "Format obsolescence: assessing the threat and the defenses". *Library Hi Tech* 28(2):195-210.

[45] Lavoie, Brian & Dempsey, Lorcan (2004). "Thirteen ways of looking at... digital preservation". *D-Lib Magazine* 10(7/8). DOI: [10.1045/july2004-lavoie](https://doi.org/10.1045/july2004-lavoie)

[46] European Commission. Directorate-General for Research and Innovation (2018). *Open Science Policy Platform Recommendations*. Bruselas: Publications Office of the European Union. Disponible en: [https://ec.europa.eu/research/openscience/](https://ec.europa.eu/research/openscience/)

[47] National Institutes of Health (2020). *Final NIH Policy for Data Management and Sharing* [Internet]. Bethesda: NIH. [citado 2024 feb]. Disponible en: [https://sharing.nih.gov/](https://sharing.nih.gov/)

[48] Consejo Nacional de Humanidades, Ciencias y Tecnologías (2022). *Política nacional de acceso abierto a la información científica, tecnológica y de innovación* [Internet]. Ciudad de México: CONAHCYT. [citado 2024 feb]. Disponible en: [https://conahcyt.mx/](https://conahcyt.mx/)

[49] Jupyter Development Team (2023). *Jupyter: a platform for interactive computing in research* [Internet]. Project Jupyter. [citado 2024 feb]. Disponible en: [https://jupyter.org/](https://jupyter.org/)

[50] Katz, Daniel S., Chue Hong, Neil P. & Clark, Tim (eds.) (2016). "Recognizing the value of software: a software citation principles". *PeerJ Computer Science* 2:e86. DOI: [10.7717/peerj-cs.86](https://doi.org/10.7717/peerj-cs.86)

[51] Konkol, Markus, Nüst, Daniel & Goulier, Laura (2020). "Publishing computational research: a review of infrastructures for reproducible and transparent scholarly communications". *Research Integrity and Peer Review* 5:10. DOI: [10.1186/s41073-020-00095-y](https://doi.org/10.1186/s41073-020-00095-y)

[52] Beck, J. (2022). "JATS standing committee: recent updates and future directions". En: *Proceedings of the 2022 JATS-Con*; 2022 oct; Bethesda. Bethesda: NCBI.

[53] Lammey, Rachael (2020). "Solutions for identification problems: a look at the Research Organization Registry". *Science Editing* 7(1):65-69. DOI: [10.6087/kcse.192](https://doi.org/10.6087/kcse.192)

[54] Liebrenz, Michael, Bhugra, Dinesh, Buadze, Anna & Schleifer, Roman (2023). "Generating scholarly content with ChatGPT: ethical challenges for medical publishing". *The Lancet Digital Health* 5(3):e105-e106. DOI: [10.1016/S2589-7500(23)00019-5](https://doi.org/10.1016/S2589-7500(23)00019-5)

[55] Heaven, Will Douglas (2023). "Generative AI is changing the way researchers write". *MIT Technology Review* [Internet]. [citado 2024 feb]. Disponible en: [https://www.technologyreview.com/](https://www.technologyreview.com/)

[56] Nielsen, Jakob (1993). *Usability Engineering*. Boston: Academic Press.

[57] Cooper, Alan, Reimann, Robert, Cronin, David & Noessel, Christopher (2014). *About Face: The Essentials of Interaction Design*. 4a ed. Indianapolis: Wiley.

