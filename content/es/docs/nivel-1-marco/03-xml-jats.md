---
title: "¿Por qué XML-JATS no es opcional?"
weight: 3
description: >
  El presente artículo examina la centralidad del estándar XML-JATS (eXtensible Markup Language - Journal Article Tag Suite) en el ecosistema contemporáneo de publicación científica. A través de un análisis histórico, técnico y pragmático, se demuestra que JATS ha dejado de ser una opción tecnológica para convertirse en un requisito estructural para la circulación, preservación e interoperabilidad del conocimiento científico. El documento explora los orígenes del estándar, su especificidad técnica, y fundamentalmente, cómo se materializa la interoperabilidad en casos de uso concretos que afectan a millones de documentos científicos en todo el mundo.
---

## 1. El rol fundamental de XML-JATS como estándar para la circulación y preservación del conocimiento científico


Durante décadas, la publicación científica se concibió fundamentalmente como un acto tipográfico: el conocimiento se materializaba en páginas impresas cuya fidelidad visual constituía el único requisito de permanencia. Esta lógica tipográfica dominó incluso los primeros años de la transición digital, cuando las revistas científicas simplemente digitalizaban sus procesos sin modificar sustancialmente su concepción del documento académico. El formato PDF, heredero directo de esta mentalidad, se convirtió en el estándar *de facto* de la publicación electrónica porque prometía exactamente aquello que el mundo académico valoraba: la reproducción exacta e inmutable de una página impresa.

Sin embargo, esta concepción está fundamentalmente reñida con las posibilidades y exigencias del entorno digital contemporáneo. Como señala Gil Leyva (2022), el verdadero potencial de la publicación científica en el entorno digital requiere una transición "de la lógica tipográfica del mundo impreso hacia la lógica semántica de la web". Esta no es una transición meramente tecnológica, sino epistemológica: implica reconceptualizar el artículo científico no como una imagen de texto, sino como un conjunto estructurado de datos semánticamente ricos, máquina-legibles e interoperables.

XML-JATS representa precisamente esta transición. Lejos de ser una mera especificación técnica más entre muchas, JATS se ha consolidado como el lenguaje común que permite que el conocimiento científico circule, se preserve y se transforme en el ecosistema digital global. La adopción de JATS por parte de infraestructuras críticas como PubMed Central, SciELO, Redalyc, CrossRef, y los principales repositorios de preservación digital no es coincidencia, sino consecuencia de una necesidad estructural: sin un estándar común, la promesa de una ciencia abierta, interoperable y preservada a largo plazo es simplemente inviable.


## 2. Génesis y evolución histórica de XML-JATS

### Los orígenes: MEDLINE y la necesidad de estructurar el conocimiento biomédico

Para comprender por qué XML-JATS existe y por qué se ha vuelto indispensable, debemos remontarnos a la década de 1960, cuando la Biblioteca Nacional de Medicina de Estados Unidos (National Library of Medicine, NLM) creó MEDLINE, una base de datos de citación de revistas médicas. Este proyecto, revolucionario para su época, representaba un esfuerzo temprano por estructurar y hacer buscable el conocimiento científico más allá de las limitaciones del índice impreso.

En 1996, la NLM lanzó PubMed, un motor de búsqueda de libre acceso a MEDLINE que democratizó significativamente el acceso a la literatura biomédica. Sin embargo, el verdadero punto de inflexión llegaría en el año 2000 con la creación de PubMed Central (PMC), un repositorio digital de texto completo desarrollado por el Centro Nacional para la Información Biotecnológica (National Center for Biotechnology Information, NCBI). PMC no se contentaba con almacenar metadatos o resúmenes: aspiraba a preservar y hacer accesibles artículos académicos completos de las revistas biomédicas y de ciencias biológicas.

Esta ambición planteaba un desafío técnico formidable: ¿cómo almacenar miles, eventualmente millones, de artículos científicos de manera que fueran permanentemente accesibles, buscables y utilizables, independientemente de los cambios tecnológicos futuros? La respuesta de la NLM fue desarrollar lo que inicialmente se conoció como NLM DTD (Document Type Definition), un esquema basado en XML específicamente diseñado para describir la estructura completa de un artículo de revista científica.

### De NLM DTD a JATS: la estandarización comunitaria

Entre 2002 y 2008, la NLM desarrolló y refinó el NLM DTD a través de múltiples versiones (de la 1.0 hasta la 3.0), aprendiendo de la experiencia de procesar decenas de miles de artículos para PMC. Cada versión incorporaba lecciones sobre la complejidad real de los artículos científicos: las múltiples formas en que los autores estructuran sus textos, la diversidad de elementos gráficos y matemáticos, las variaciones en las prácticas de citación, las complejidades de las afiliaciones institucionales en contextos internacionales.

El momento decisivo llegó en 2012, cuando la Organización Nacional de Estándares de Información (National Information Standards Organization, NISO) adoptó formalmente el trabajo de la NLM como un estándar nacional estadounidense bajo la designación ANSI/NISO Z39.96-2012, denominándolo Journal Article Tag Suite (JATS) versión 1.0. Esta estandarización formal no fue un simple cambio de nombre: representaba la transformación de una solución institucional específica en un estándar comunitario abierto, gobernado por un proceso de desarrollo público con participación de múltiples actores.

Como documenta el comité JATS, desde su creación participaron miembros de instituciones diversas: la American Library Association, la American Psychological Association, CrossRef, EBSCO Information Services, la Biblioteca del Congreso de Estados Unidos, ProQuest, Public Library of Science (PLoS), SAGE Publications, OCLC, y Microsoft Corporation, entre otras. Esta diversidad de participantes garantizaba que JATS no respondiera únicamente a los intereses de un actor particular, sino que reflejara las necesidades del ecosistema de publicación científica en su conjunto.

### Adopción global: de estándar técnico a infraestructura crítica

La adopción de JATS por parte de la comunidad científica global ha sido progresiva pero inexorable. En 2013, SciELO inició cambios sustanciales en el proceso de edición de las revistas que indexa, adoptando la especificación SciELO Publishing Schema (SciELO PS) basada en JATS 1.0. Esta decisión representaba un punto de inflexión para la publicación científica latinoamericana: SciELO, con más de 1.500 revistas indexadas y millones de artículos, establecía un nuevo estándar de facto para la región.

En 2014, el modelo de SciELO fue seguido por Redalyc (Red de Revistas Científicas de América Latina y el Caribe, España y Portugal), que en 2015 lanzó Marcalyc, una herramienta de marcación XML-JATS destinada a profesionalizar a los editores y hacer sostenible la transición al nuevo modelo. Al igual que SciELO, Redalyc adoptó JATS no como una opción técnica entre muchas, sino como un componente esencial de su modelo de Acceso Abierto Diamante, comprometido con la publicación científica sin fines de lucro y sin costos para autores ni lectores.

La cronología de adopción es reveladora de una tendencia global:
- **2000**: PubMed Central comienza a operar con precursores de JATS
- **2008**: NLM DTD 3.0, última versión pre-estandarización
- **2012**: NISO formaliza JATS 1.0 como estándar Z39.96
- **2013**: SciELO adopta JATS para todas sus revistas indexadas
- **2015**: Redalyc lanza Marcalyc basado en JATS 1.1
- **2019**: JATS 1.2 amplía soporte para contenido multimedia y accesibilidad
- **2024**: JATS 1.4 incorpora mejoras en metadatos de financiamiento y autoría

Para 2025, JATS se encuentra en uso en más de 25 países, incluyendo Australia, Bélgica, Brasil, Bulgaria, Canadá, Chile, Egipto, Finlandia, Francia, Alemania, Italia, Japón, Noruega, Rusia, Corea del Sur, Suecia, Suiza, Emiratos Árabes Unidos, Reino Unido y Estados Unidos. Los archivos públicos y privados más importantes del mundo requieren o prefieren JATS, incluyendo PubMed Central (tanto en Estados Unidos como en Europa PMC), la Biblioteca Nacional Británica, la Biblioteca Nacional de Australia, la Biblioteca del Congreso de Estados Unidos, CLOCKSS, Portico y LOCKSS.


## 3. La especificidad técnica de JATS: más que un formato XML

### XML como fundamento: separación de contenido y presentación

Para comprender la especificidad de JATS, primero debemos entender el fundamento sobre el cual está construido: el Lenguaje de Marcado Extensible (XML). XML, desarrollado por el World Wide Web Consortium (W3C) y cuya primera versión data de 1998, es un metalenguaje diseñado para la publicación electrónica y el intercambio de datos estructurados. A diferencia de los lenguajes de marcado específicos como HTML, XML permite crear vocabularios especializados para describir cualquier tipo de información estructurada.

El principio fundamental de XML es la **separación radical entre contenido y presentación**. Un documento XML contiene únicamente la estructura semántica y el contenido informativo, sin ninguna especificación sobre cómo debe verse o imprimirse. Esta separación, que puede parecer una abstracción técnica, tiene implicaciones profundas para la publicación científica:

1. **Independencia de plataforma**: Un artículo en XML-JATS no "pertenece" a ningún software, sistema operativo o dispositivo particular. Puede procesarse, transformarse y visualizarse en cualquier plataforma que entienda XML.

2. **Múltiples presentaciones desde una única fuente**: Un mismo archivo XML-JATS puede transformarse automáticamente en HTML para visualización web, PDF para impresión, ePUB para lectores electrónicos, o formatos especializados para personas con discapacidad visual.

3. **Longevidad informacional**: Mientras que los formatos propietarios o dependientes de presentación se vuelven obsoletos cuando el software que los creó desaparece, XML se mantiene legible porque es fundamentalmente texto plano estructurado según reglas explícitas.

### JATS como vocabulario especializado: tres modelos para tres necesidades

JATS no es un único formato monolítico, sino una familia de tres modelos o "tag sets" diseñados para diferentes casos de uso:

#### JATS Green (Archiving and Interchange Tag Set)

El modelo de archivo es el más permisivo y flexible de los tres. Diseñado específicamente para bibliotecas, archivos y repositorios, permite incorporar prácticamente cualquier estructura o elemento que pueda aparecer en un artículo científico, sin importar cuán heterodoxo o inusual sea. Esta permisividad es deliberada: los archivos deben poder recibir y preservar contenido de múltiples fuentes sin rechazar artículos porque usen convenciones particulares.

El JATS Green garantiza que, independientemente de las particularidades editoriales de cada revista, siempre existirá una manera de representar fielmente su contenido en un formato preservable y intercambiable. Esta flexibilidad lo convierte en el modelo preferido para iniciativas de preservación a largo plazo como CLOCKSS y Portico.

#### JATS Blue (Publishing Tag Set)

El modelo de publicación es más restrictivo y prescriptivo. Diseñado para editores, plataformas de publicación y portales, establece prácticas más específicas sobre cómo debe estructurarse un artículo para su publicación efectiva. Este modelo facilita la generación consistente de diferentes formatos de salida y asegura que los artículos puedan procesarse automáticamente para indexación, búsqueda y visualización.

SciELO y Redalyc, aunque ambos basados en JATS Blue, han desarrollado especificaciones más estrictas (SciELO Publishing Schema y la especificación de Redalyc respectivamente) que añaden requisitos adicionales para metadatos bibliométricos, afiliaciones institucionales detalladas, e identificadores específicos necesarios para sus ecosistemas.

#### JATS Orange (Article Authoring Tag Set)

El modelo de autoría es el más restrictivo de los tres, diseñado para simplificar el proceso de creación de artículos científicos. Limita las opciones disponibles a aquellas más comúnmente necesarias, facilitando que los autores y editores produzcan contenido válido sin necesidad de dominar la especificación completa de JATS.

Esta diferenciación en tres modelos revela una comprensión sofisticada del ecosistema de publicación: diferentes actores tienen diferentes necesidades, y un estándar verdaderamente útil debe acomodar esta diversidad sin fragmentarse en dialectos incompatibles.

### Estructura anatómica de un documento JATS

Todo documento JATS, independientemente del modelo utilizado, se estructura en tres secciones principales que reflejan la organización conceptual de un artículo científico:

#### Front (metadatos y preliminares)

El front contiene toda la información bibliográfica y administrativa del artículo. Aquí residen los metadatos esenciales para la identificación, catalogación e indexación del documento:

- **Identificadores persistentes**: DOI (Digital Object Identifier), identificadores de la revista (ISSN), identificadores institucionales
- **Información de autoría**: nombres completos con alternativas multilingües (por ejemplo, caracteres japoneses y su romanización), múltiples afiliaciones institucionales con estructura completa (universidad, facultad, departamento), roles según la taxonomía CRediT (Contributor Roles Taxonomy)
- **Información editorial**: título del artículo en múltiples idiomas, nombre de la revista, volumen, número, paginación, fechas de recepción, aceptación y publicación
- **Resúmenes y palabras clave**: en todos los idiomas en que estén disponibles
- **Metadatos de financiamiento**: agencias financiadoras, números de proyectos, información esencial para cumplir con requisitos de organismos como NIH o Plan S
- **Licencias y derechos**: especificación de licencias Creative Commons u otras, información de copyright

La riqueza de metadatos en el front no es ornamental: cada elemento permite formas específicas de descubrimiento, análisis y cumplimiento normativo que serían imposibles con metadatos menos estructurados.

#### Body (contenido principal)

El body contiene el contenido narrativo del artículo: párrafos, secciones, subsecciones, listas, ecuaciones, figuras, tablas, y otros elementos que constituyen el argumento científico propiamente dicho. La estructuración semántica del body permite:

- **Búsqueda granular**: Localizar información no solo en el artículo completo, sino en secciones específicas (materiales y métodos, resultados, discusión)
- **Extracción de datos**: Sistemas automatizados pueden identificar y extraer tablas de resultados, ecuaciones, o afirmaciones específicas
- **Navegación inteligente**: Generación automática de tablas de contenido, índices de figuras y tablas, enlaces internos entre secciones
- **Accesibilidad mejorada**: Lectores de pantalla pueden navegar por la estructura lógica del documento, no solo por su presentación lineal

#### Back (material complementario)

El back contiene información que apoya al texto principal pero no es parte de la narrativa central:

- **Referencias bibliográficas**: Crucialmente, JATS permite etiquetar cada componente de una referencia (autores, título, revista, año, volumen, páginas, DOI) de manera que puedan verificarse automáticamente contra bases de datos como CrossRef, facilitando la corrección de errores y la construcción de redes de citación
- **Apéndices**: Material suplementario, datos adicionales, protocolos detallados
- **Glosarios**: Definiciones de términos técnicos
- **Notas**: Aclaraciones, agradecimientos, conflictos de interés

### Elementos distintivos: expresividad semántica

Lo que distingue a JATS de otros esquemas XML es su expresividad semántica específicamente calibrada para la literatura científica. Algunos ejemplos ilustran esta especificidad:

**Fórmulas matemáticas**: JATS incorpora MathML (Mathematical Markup Language) permitiendo que las ecuaciones no sean simples imágenes, sino estructuras semánticamente ricas que pueden ser procesadas, buscadas y reutilizadas.

**Estructuras químicas**: Integración con CML (Chemical Markup Language) para representar moléculas y reacciones químicas de manera estructurada.

**Nomenclatura biológica**: Elementos específicos para marcar nombres científicos de especies, genes, proteínas, siguiendo convenciones taxonómicas.

**Datos geoespaciales**: Elementos para coordenadas geográficas, localidades, que permiten integración con sistemas de información geográfica.

**Multimedia**: Soporte para videos, archivos de audio, datasets, con metadatos que describen su contenido y relación con el texto principal.

Esta expresividad no es meramente descriptiva: cada elemento semánticamente rico es una puerta a nuevas formas de interrogar y utilizar el conocimiento científico.


## 4. ¿Por qué XML-JATS no es opcional?, argumentos estructurales

### La interoperabilidad como imperativo sistémico

En un ecosistema de publicación científica fragmentado entre miles de editoriales, decenas de plataformas de gestión editorial, cientos de repositorios institucionales, y múltiples sistemas de indexación y descubrimiento, la **interoperabilidad** no es un lujo sino una necesidad existencial. Interoperabilidad significa la capacidad de sistemas diferentes de intercambiar información de manera que permanezca útil y significativa en ambos extremos del intercambio.

Sin un estándar común, cada intercambio entre sistemas requiere conversiones *ad hoc*, traducciones manuales, o peor aún, pérdida de información. Consideremos un escenario típico sin JATS:

1. Un editor produce un artículo en un formato propietario de su software editorial
2. Para depositar en un repositorio institucional, debe convertirse manualmente a otro formato
3. Para indexarse en bases de datos disciplinarias, requiere otra conversión
4. Para cumplir con requisitos de acceso abierto de organismos financiadores, necesita depositarse en repositorios específicos en formatos particulares
5. Para preservación a largo plazo, archivos como CLOCKSS requieren formatos específicos

Cada conversión es una oportunidad de error, pérdida de información, y trabajo duplicado. Multiplicado por millones de artículos al año, este modelo es simplemente insostenible.

JATS resuelve este problema estableciendo un formato pivote: los editores producen en JATS (o convierten a JATS), y desde ese formato único pueden alimentar todos los sistemas del ecosistema. PubMed Central, CrossRef, bases de datos disciplinarias, repositorios institucionales, sistemas de preservación, todos pueden consumir JATS, cada uno extrayendo la información que necesita según sus requisitos específicos.

Como documenta la especificación oficial de JATS, este estándar fue construido precisamente para "proporcionar interoperabilidad del contenido del artículo y los metadatos del artículo entre editores y archivos". No es coincidencia que las transformaciones públicas y gratuitas para crear depósitos en CrossRef se basen en JATS, o que PubMed Central requiera JATS para aceptar artículos.

### Mandatos institucionales y requisitos de financiamiento

La transición de JATS de opción a requisito está siendo acelerada por mandatos institucionales y políticas de financiamiento que lo establecen como condición necesaria para el cumplimiento normativo.

Los Institutos Nacionales de Salud de Estados Unidos (NIH) requieren que todos los artículos resultantes de investigación financiada por ellos se depositen en PubMed Central, que acepta primariamente JATS. El Wellcome Trust tiene requisitos similares. La cOAlition S, con su Plan S, requiere publicación inmediata en acceso abierto con metadatos estructurados que faciliten el cumplimiento, algo que JATS simplifica significativamente al permitir especificar información de financiamiento de manera estructurada y verificable.

El Directory of Open Access Journals (DOAJ), estándar de oro para revistas de acceso abierto, ha comenzado a requerir o fuertemente recomendar JATS/XML para la indexación. Esta política refleja un reconocimiento de que la calidad y utilidad de una revista en acceso abierto no se mide únicamente por la disponibilidad del texto, sino por la riqueza de metadatos y la facilidad con que el contenido puede ser descubierto, reutilizado e integrado en el ecosistema de conocimiento global.

Para Latinoamérica, la adopción de JATS por SciELO y Redalyc lo ha convertido efectivamente en requisito para la indexación regional. Una revista que aspire a visibilidad en la región debe, en la práctica, producir sus artículos en JATS.

### Preservación digital: garantizar el futuro del conocimiento

La preservación digital presenta un desafío único: ¿cómo garantizar que documentos creados hoy permanezcan accesibles, legibles y utilizables dentro de 50, 100, o 500 años, cuando los sistemas operativos, software de lectura y formatos de presentación de hoy habrán desaparecido completamente?

Los formatos dependientes de software propietario o de especificaciones de presentación tienen una vida útil limitada. El formato .doc de Microsoft Word de la década de 1990 es ya difícil de abrir correctamente en software moderno. Los PDF, aunque más robustos, dependen de la disponibilidad de lectores PDF y pueden presentar problemas de accesibilidad y extracción de información.

JATS, como formato basado en XML de texto plano con una especificación públicamente documentada, ofrece garantías de longevidad que los formatos propietarios no pueden igualar:

1. **Legibilidad humana**: Un archivo JATS es texto plano. Incluso sin software especializado, puede leerse y entenderse (aunque laboriosamente) con cualquier editor de texto.

2. **Especificación pública y documentada**: Las reglas para interpretar JATS están públicamente disponibles y mantenidas por una organización de estándares. No dependen de la supervivencia de una empresa particular.

3. **Independencia tecnológica**: No requiere ningún software, sistema operativo o hardware particular. Mientras existan computadoras que puedan leer texto, JATS será legible.

4. **Separación de contenido y presentación**: Incluso si las convenciones de visualización cambian, el contenido informativo permanece intacto y puede ser re-presentado según las necesidades futuras.

Las principales iniciativas de preservación digital del mundo científico han convergido en JATS precisamente por estas características. CLOCKSS (Controlled Lots of Copies Keep Stuff Safe), una organización sin fines de lucro gobernada por bibliotecas y editores, acepta y prefiere JATS para el archivo de contenido científico. Su política de desarrollo de colecciones establece explícitamente que para contenido depositado vía FTP, aceptan "JATS, BITS, y cualquier otro XML bien formado".

Portico, el servicio de archivo digital mundial proporcionado por ITHAKA, igualmente ha adoptado JATS como formato preferido para preservación de revistas académicas. LOCKSS (Lots of Copies Keep Stuff Safe), el programa de código abierto desarrollado por la Biblioteca de Stanford, y la red PKP Preservation Network basada en LOCKSS, preservan contenido preferentemente en JATS.

Esta convergencia no es casual: estos sistemas reconocen que preservar PDFs o formatos propietarios es preservar presentaciones, no contenido. JATS preserva la estructura semántica subyacente del conocimiento científico, permitiendo que futuras generaciones no solo lean los artículos, sino que los procesen, analicen y utilicen de maneras que hoy no podemos anticipar.

### Búsqueda, descubrimiento y minería de texto

La explosión de la literatura científica ha hecho imposible que investigadores individuales mantengan el ritmo de la producción en sus campos. PubMed indexa más de 36 millones de citas; Web of Science excede los 100 millones de registros. En este contexto, la búsqueda efectiva no es un complemento sino una condición necesaria para la práctica científica.

JATS habilita formas de búsqueda y descubrimiento imposibles con formatos menos estructurados:

**Búsqueda por estructura**: No solo buscar términos en el texto completo, sino localizar términos en secciones específicas. Por ejemplo, buscar "CRISPR" únicamente en secciones de métodos, o buscar valores específicos únicamente en tablas de resultados.

**Extracción de entidades**: Sistemas automatizados pueden identificar y extraer nombres de genes, proteínas, compuestos químicos, especies biológicas, localizaciones geográficas, porque están marcados semánticamente.

**Construcción de redes de conocimiento**: Las referencias bibliográficas estructuradas permiten construir gráficos de citación masivos, identificar co-citaciones, rastrear la evolución de ideas a través del tiempo.

**Minería de texto a gran escala**: Proyectos como Europe PubMed Central Text Mining permiten analizar millones de artículos para identificar relaciones entre entidades, generar hipótesis, detectar tendencias emergentes. Esto es viable únicamente porque los artículos están en JATS, donde el contenido está estructurado de manera procesable.

**Verificación automática de referencias**: CrossRef puede verificar automáticamente la exactitud de referencias bibliográficas en artículos JATS, corrigiendo errores tipográficos en DOIs, identificando referencias incompletas o incorrectas.

### Accesibilidad universal y cumplimiento legal

Las convenciones internacionales sobre derechos de las personas con discapacidad, y legislaciones nacionales como la Americans with Disabilities Act, establecen requisitos crecientes de accesibilidad para contenidos académicos. Universidades, bibliotecas e instituciones públicas están legalmente obligadas a garantizar que sus materiales sean accesibles para personas con discapacidad visual, auditiva, o de otro tipo.

Los PDFs, especialmente aquellos generados desde documentos de maquetación como InDesign, frecuentemente carecen de la estructura semántica necesaria para que lectores de pantalla naveguen efectivamente el documento. Imágenes sin texto alternativo, tablas sin estructura lógica, fórmulas matemáticas como imágenes incomprensibles para tecnologías asistivas.

JATS, por su naturaleza estructurada, facilita inmensamente la generación de contenido accesible:

- **Navegación estructurada**: Lectores de pantalla pueden saltar entre secciones, navegar por listas, acceder a tablas de contenido
- **Texto alternativo para imágenes**: JATS requiere descripciones textuales de figuras y gráficos
- **Fórmulas accesibles**: MathML dentro de JATS puede ser verbalizado por lectores de pantalla especializados
- **Múltiples formatos desde única fuente**: Desde JATS se pueden generar PDFs accesibles (PDF/UA), HTML con etiquetas ARIA apropiadas, ePUB3 con navegación estructurada

La accesibilidad no es solo una cuestión ética o legal: es una cuestión de justicia epistémica. El conocimiento científico debe estar disponible para todos, independientemente de sus capacidades sensoriales o motoras.


## 5. La interoperabilidad en acción: casos de uso de JATS bien construido

### Flujo de trabajo tipo: del manuscrito al ecosistema global

Para comprender cómo JATS materializa la interoperabilidad en la vida real, consideremos el ciclo de vida completo de un artículo desde su aceptación hasta su integración en el ecosistema de conocimiento global.

**Fase 1: Producción editorial**

Una revista recibe un manuscrito aceptado en formato Word. El equipo editorial tiene varias opciones para generar el XML-JATS:

- **Servicios comerciales especializados**: Empresas como las identificadas en el SciELO Marketplace ofrecen conversión profesional, garantizando marcado de alta calidad
- **Herramientas institucionales**: SciELO proporciona su herramienta Markup; Redalyc ofrece Marcalyc a revistas indexadas
- **Software de gestión editorial**: Open Journal Systems (OJS) incluye plugins para generar JATS
- **Conversión manual con editores especializados**: Herramientas como Texture (aunque en desuso), o JATSeditor.com permiten crear y editar JATS visualmente
- **Sistemas de producción basados en JATS canónico**: Herramientas como gbpublisher implementan un flujo de trabajo que genera primero un archivo JATS canónico (completo, rico en metadatos, estrictamente conforme al estándar) que sirve como fuente única desde la cual se derivan automáticamente las variantes específicas requeridas por diferentes plataformas (SciELO PS, especificación Redalyc, JATS4R, etc.). Este enfoque resuelve el problema de tener que mantener múltiples versiones incompatibles del mismo artículo.

El resultado es un archivo XML-JATS que codifica completamente el artículo: metadatos, estructura, contenido textual, referencias, ecuaciones, metadatos de figuras y tablas.

**Fase 2: Validación y control de calidad**

El archivo JATS debe validarse contra la DTD (Document Type Definition) o XSD (XML Schema Definition) correspondiente. Esta validación verifica que el archivo cumple las reglas sintácticas del estándar. Sin embargo, como documenta Mark Gross en la conferencia JATS-Con 2025, "válido no siempre significa funcional o bueno". Un archivo puede ser válido sintácticamente pero contener errores semánticos que causarán problemas downstream:

- Un DOI que contenga un guion em (—, Unicode U+2014) en lugar del guion ASCII estándar (-, Unicode U+002D) será **sintácticamente válido en XML, pero fallará al resolverse**. Aunque ambos caracteres son visualmente similares, son códigos Unicode distintos. Dado que el DOI es una cadena literal que debe coincidir exactamente con el identificador registrado, cualquier sustitución tipográfica altera la secuencia de caracteres y provoca que el resolvedor no encuentre el recurso. Este tipo de error es frecuente cuando el texto ha sido redactado o editado en procesadores como Microsoft Word, que aplican automáticamente reglas de sustitución tipográfica (por ejemplo, reemplazando ciertos guiones por rayas tipográficas). En textos narrativos esto mejora la presentación, pero en identificadores técnicos puede introducir caracteres distintos al guion ASCII requerido.
- Referencias con etiquetado insuficiente validarán pero no permitirán verificación automática
- Afiliaciones con estructura incorrecta pasarán validación pero no permitirán extracción correcta de datos institucionales

Por ello, sistemas de calidad avanzados implementan validaciones adicionales más allá de la DTD, verificando consistencia semántica, completitud de metadatos esenciales, y conformidad con mejores prácticas documentadas por JATS4R (JATS for Reuse), un esfuerzo comunitario para establecer convenciones de etiquetado sensatas.

**Fase 3: Publicación y generación de formatos derivados**

Desde el archivo JATS maestro, la revista genera automáticamente múltiples formatos de presentación:

- **HTML5 interactivo**: Con navegación mejorada, enlaces internos automáticos, visualización responsiva que se adapta a diferentes dispositivos
- **PDF para impresión**: Aplicando hojas de estilo específicas que respetan el diseño visual de la revista
- **ePUB3 para lectores electrónicos**: Con tabla de contenidos interactiva, soporte multimedia
- **Versiones accesibles**: PDF/UA, HTML con ARIA tags

Estas transformaciones son automáticas porque están basadas en la estructura semántica del JATS, no requieren trabajo manual adicional.

**Fase 4: Depósito en repositorios y registro de DOI**

El artículo debe depositarse en múltiples sistemas:

**CrossRef**: Para registrar el DOI y hacer el artículo localizable. CrossRef acepta depósitos en su propio formato XML, pero proporciona transformaciones XSLT (eXtensible Stylesheet Language Transformations) para convertir JATS a formato CrossRef. El depósito exitoso en CrossRef significa que el artículo es ahora parte de la infraestructura global de citación, sus metadatos están disponibles para servicios de descubrimiento, y el DOI puede resolverse a la ubicación del artículo.

**PubMed Central** (si aplica): Para artículos biomédicos, especialmente aquellos financiados por NIH, el depósito en PMC es frecuentemente obligatorio. PMC requiere JATS; de hecho, PMC fue instrumental en el desarrollo del estándar. El depósito en PMC hace el artículo parte del archivo público de literatura biomédica más grande del mundo, accesible gratuitamente a investigadores globalmente.

**Europe PMC**: La contraparte europea de PMC, igualmente basada en JATS, garantizando cumplimiento con políticas europeas de acceso abierto.

**Repositorio institucional**: La universidad de los autores puede requerir depósito en su repositorio institucional. Si el repositorio acepta JATS, el depósito es directo. Si requiere otro formato, la conversión desde JATS es técnicamente sencilla porque toda la información está estructurada.

**Fase 5: Indexación en bases de datos**

El artículo debe indexarse en bases de datos disciplinarias y multidisciplinarias:

**Web of Science, Scopus**: Sistemas de indexación comerciales que alimentan métricas como el Factor de Impacto. Aunque estos sistemas no requieren necesariamente JATS, la disponibilidad del artículo en JATS facilita la extracción automática de metadatos completos y correctos.

**SciELO, Redalyc**: Para revistas latinoamericanas, la indexación en estos metaeditores regionales requiere JATS. Una vez indexado, el artículo se beneficia de la infraestructura de difusión, métricas e interoperabilidad de estos sistemas.

**DOAJ**: El directorio de revistas de acceso abierto está incrementando sus requisitos de JATS, reconociendo que es indicador de calidad editorial y compromiso con estándares.

**Bases de datos disciplinarias**: Dependiendo del campo (PsycINFO para psicología, MathSciNet para matemáticas, etc.), diferentes bases de datos especializadas indexan el artículo. JATS facilita que estas bases extraigan los metadatos que necesitan sin conversiones manuales.

**Fase 6: Preservación a largo plazo**

El archivo JATS debe depositarse en sistemas de preservación digital:

**CLOCKSS**: Un "archivo oscuro" (dark archive) que solo libera contenido si la fuente original deja de estar disponible (por ejemplo, si la editorial quiebra). CLOCKSS distribuye copias del contenido en múltiples nodos geográficos, garantizando redundancia física.

**Portico**: Servicio de preservación que mantiene copias de contenido académico, accesible a bibliotecas participantes si el acceso original se interrumpe.

**LOCKSS/PKP PN**: Redes descentralizadas de preservación donde múltiples bibliotecas mantienen copias redundantes, verificándose mutuamente para detectar y corregir corrupción de archivos.

El depósito en estos sistemas garantiza que, independientemente de lo que suceda con la revista o editorial, el conocimiento científico permanece preservado y accesible para futuras generaciones.

### Caso de estudio: SciELO y el modelo latinoamericano

SciELO (Scientific Electronic Library Online) representa uno de los casos de adopción más masiva y exitosa de JATS en el mundo, y merece análisis detallado como modelo de cómo un ecosistema regional entero puede transformarse mediante la adopción coordinada de estándares.

**Contexto y decisión estratégica**

En 2013, SciELO tomó la decisión estratégica de migrar completamente a XML-JATS, estableciendo la especificación SciELO Publishing Schema (SciELO PS) basada en JATS 1.0. Esta no fue una decisión meramente técnica: representaba una reconceptualización completa del modelo de publicación científica regional.

Antes de JATS, SciELO operaba con un modelo basado en PDF y HTML generados desde archivos de procesador de textos. Este modelo, aunque funcional, limitaba severamente las posibilidades de procesamiento automático, extracción de datos, e interoperabilidad con sistemas internacionales.

La adopción de JATS perseguía objetivos explícitos:

1. **Interoperabilidad global**: Permitir que la ciencia latinoamericana se integre plenamente en infraestructuras globales (PubMed, CrossRef, bases de datos internacionales)
2. **Profesionalización editorial**: Elevar los estándares de producción editorial regional mediante la adopción de mejores prácticas internacionales
3. **Generación de métricas avanzadas**: Habilitar indicadores bibliométricos sofisticados basados en análisis de citaciones, colaboraciones, financiamiento
4. **Sostenibilidad a largo plazo**: Garantizar preservación digital del patrimonio científico regional

**Implementación: Markup y el ecosistema de herramientas**

SciELO desarrolló Markup, un conjunto de herramientas que facilitan la producción de XML-JATS conforme a SciELO PS. Markup no es una herramienta única sino un flujo de trabajo completo que incluye:

- **Validadores**: Que verifican no solo sintaxis XML sino cumplimiento con requisitos específicos de SciELO PS
- **Generadores de PDF**: Que producen PDFs con el diseño editorial de cada revista desde el XML maestro
- **Conversores HTML**: Que generan páginas web interactivas con navegación enriquecida
- **Empaquetadores**: Que preparan paquetes de archivos para depósito en repositorios y preservación

Crucialmente, SciELO adoptó un modelo de capacitación intensiva: en lugar de simplemente ofrecer herramientas, creó programas de formación para editores, diseñados para desarrollar competencias internas en las revistas. El objetivo era que las revistas pudieran producir JATS de manera autónoma y sostenible, no que dependieran indefinidamente de servicios externos.

**Impacto y resultados**

Al 2025, más de 1.500 revistas en la red SciELO (que incluye colecciones nacionales en 16 países de América Latina, España, Portugal y Sudáfrica) publican en JATS. Esto representa decenas de millones de artículos estructurados, buscables, interoperables y preservados.

Los resultados son medibles en múltiples dimensiones:

**Visibilidad internacional**: Artículos de revistas SciELO aparecen en PubMed Central International, son indexados correctamente en Web of Science y Scopus, y son descubiertos más fácilmente por investigadores globales porque sus metadatos están completos y estructurados.

**Métricas de uso mejoradas**: SciELO puede ahora reportar no solo cuántas veces se descarga un artículo, sino cómo se usa: qué secciones se leen más, cómo navegan los lectores entre artículos relacionados, qué figuras generan más interés.

**Citación más efectiva**: La estructuración completa de referencias bibliográficas permite verificar automáticamente citaciones, corregir errores, y construir redes de citación que revelan patrones de influencia e impacto.

**Preservación garantizada**: Los artículos SciELO en JATS están depositados en CLOCKSS y Portico, garantizando su permanencia independientemente de la viabilidad financiera de revistas o instituciones individuales.

### Caso de estudio: Redalyc y el modelo de acceso abierto diamante

Redalyc (Red de Revistas Científicas de América Latina y el Caribe, España y Portugal) adoptó JATS en 2015, pero con una filosofía distintiva centrada en el acceso abierto diamante: publicación sin costos para autores (no APCs - Article Processing Charges) y sin costos para lectores, sostenida mediante apoyo institucional público.

**Marcalyc: diseño para la profesionalización del editor**

Marcalyc, la herramienta de marcación desarrollada por Redalyc, incorpora inteligencia artificial y algoritmos de procesamiento de lenguaje natural para automatizar parcialmente el proceso de etiquetado. El sistema puede:

- Identificar automáticamente autores, afiliaciones, resúmenes y palabras clave
- Estructurar automáticamente secciones del artículo (introducción, métodos, resultados, discusión)
- Reconocer y estructurar referencias bibliográficas con alto nivel de precisión
- Procesar ecuaciones y fórmulas, convertirlas a MathML

El editor humano supervisa y corrige lo inferido automáticamente, pero el proceso es significativamente más eficiente que el marcado completamente manual.

**Formatos de salida múltiples**

Desde el XML-JATS producido con Marcalyc, se generan automáticamente:

- **PDF personalizado**: Con el diseño específico de cada revista
- **HTML5 responsivo**: Optimizado para lectura en diferentes dispositivos
- **ePUB3**: Para lectores electrónicos y tabletas
- **Visor inteligente**: Una interfaz de lectura enriquecida que permite navegación contextual, visualización de métricas, acceso a materiales suplementarios
- **Visor móvil**: Optimizado específicamente para smartphones

**Sustentabilidad y profesionalización**

El modelo de Redalyc descansa en la premisa de que la producción de conocimiento científico es una función pública que debe sostenerse con recursos públicos, no mediante mercantilización del acceso o traslado de costos a autores. La adopción de JATS es parte integral de este modelo porque:

1. **Reduce costos a largo plazo**: Aunque requiere inversión inicial en capacitación, la producción interna de JATS es más sostenible que depender indefinidamente de servicios comerciales
2. **Retorna control a editores**: Las revistas mantienen el archivo maestro de sus artículos en un formato estándar abierto, no dependiente de software propietario
3. **Garantiza preservación**: JATS asegura que el patrimonio científico regional permanezca accesible independientemente de cambios tecnológicos futuros

Al 2023, más de 1.080 revistas indexadas en Redalyc habían transitado a XML-JATS, representando una transformación masiva del ecosistema editorial latinoamericano.

### Desafíos de interoperabilidad y la solución del JATS canónico

A pesar de que tanto SciELO como Redalyc adoptaron JATS, las diferencias en sus especificaciones específicas (SciELO PS vs. especificación Redalyc) han generado problemas de interoperabilidad que merecen atención como lección sobre los límites de la estandarización y, crucialmente, sobre cómo resolverlos.

#### El problema: fragmentación del estándar

En 2017, dos años después de la adopción de JATS por Redalyc, se hizo pública una controversia sobre la incompatibilidad entre los archivos JATS producidos según cada especificación. Una revista indexada en ambos metaeditores se veía forzada a producir dos versiones JATS diferentes, duplicando trabajo y costo.

La controversia revela una tensión fundamental: ¿hasta qué punto un estándar debe ser flexible para acomodar necesidades locales, y en qué punto esa flexibilidad fragmenta el ecosistema que el estándar pretendía unificar?

SciELO y Redalyc desarrollaron sus variantes de JATS para satisfacer necesidades específicas de sus ecosistemas: SciELO requiere metadatos particulares para sus indicadores bibliométricos; Redalyc necesita estructuras específicas para su modelo de visualización. Ambas necesidades son legítimas, pero resultaron en dialectos mutuamente incompatibles.

#### La solución: JATS canónico como fuente única

La respuesta técnica a este problema de fragmentación es el concepto de **JATS canónico**: un archivo JATS maestro que contiene *todos* los metadatos y estructuras que cualquier plataforma podría requerir, desde el cual se derivan automáticamente las variantes específicas de cada plataforma mediante transformaciones XSLT.

Este enfoque invierte el problema: en lugar de producir múltiples versiones incompatibles, se produce **una única versión rica y completa** (el JATS canónico) que sirve como fuente de verdad, y se generan automáticamente las variantes específicas según las necesidades de cada sistema de indexación.

Herramientas como **gbpublisher** (en desarrollo activo en el ecosistema latinoamericano) implementan precisamente este modelo de trabajo:

1. **Entrada única**: El editor marca el artículo una sola vez, produciendo un JATS canónico que cumple estrictamente con el estándar NISO y contiene todos los metadatos posibles
2. **Enriquecimiento**: El JATS canónico se enriquece con metadatos adicionales que diferentes plataformas puedan necesitar (indicadores bibliométricos para SciELO, estructuras de visualización para Redalyc, metadatos de financiamiento para Plan S, etc.)
3. **Derivación automática**: Mediante transformaciones XSLT específicamente diseñadas para cada plataforma, se generan automáticamente:
   - JATS conforme a SciELO PS
   - JATS conforme a especificación Redalyc
   - JATS conforme a JATS4R
   - XML de depósito para CrossRef
   - XML de depósito para PubMed Central
   - Y cualquier otra variante requerida

Este modelo ofrece ventajas significativas:

**Para editores**: Marcación única, sin duplicación de trabajo. Si un artículo necesita corrección, se corrige una vez en el canónico y todas las derivadas se regeneran automáticamente.

**Para plataformas**: Pueden especificar exactamente qué necesitan sin forzar convergencia prematura con otros sistemas. Las transformaciones pueden evolucionar independientemente.

**Para preservación**: El JATS canónico sirve como archivo maestro de preservación, conteniendo la máxima información posible. Las variantes pueden regenerarse en el futuro si los requisitos cambian.

**Para interoperabilidad**: Paradójicamente, aceptar la diversidad de necesidades (y por tanto de variantes) mediante un proceso sistemático de derivación mejora la interoperabilidad real más que forzar una única especificación que nadie cumple completamente.

#### Lecciones y convergencia comunitaria

Los intentos de reconciliación bilateral, como LuXMeL (hacia la interoperabilidad Redalyc/AmeliCA-SciELO), buscan establecer puentes técnicos que permitan convertir entre especificaciones. Sin embargo, el enfoque más robusto es el del JATS canónico, que no intenta hacer compatibles las variantes existentes sino que las trata como productos derivados de una única fuente rica.

Esta lección es importante: la comunidad global JATS debe equilibrar flexibilidad con rigor. JATS4R (JATS for Reuse) representa un esfuerzo comunitario precisamente para este fin: documentar mejores prácticas de etiquetado que, sin requerir modificaciones al estándar, establecen convenciones que facilitan intercambio e interpretación consistente.

El futuro de la interoperabilidad JATS probablemente no pasa por lograr que todos produzcan exactamente el mismo JATS, sino por establecer:
1. Un conjunto nuclear de metadatos absolutamente esenciales que *deben* estar presentes
2. Transformaciones bien documentadas y públicamente disponibles entre variantes
3. Validadores que verifiquen no solo sintaxis sino utilidad semántica
4. Flujos de trabajo (como el de JATS canónico) que hagan técnicamente simple mantener múltiples variantes sincronizadas

### Interoperabilidad con CrossRef: el ecosistema de citación

CrossRef, la organización sin fines de lucro que administra el sistema de DOIs más grande del mundo académico, ejemplifica cómo JATS habilita interoperabilidad en el nivel más fundamental: la identificación y citación persistente.

**Depósito de metadatos**

Cuando una revista registra un DOI para un artículo en CrossRef, debe depositar metadatos: información sobre autores, título, revista, volumen, número, páginas, referencias bibliográficas. CrossRef tiene su propio esquema XML para estos depósitos, pero proporciona transformaciones XSLT para convertir JATS al formato CrossRef.

Crucialmente, las referencias bibliográficas en JATS están estructuradas componente por componente. CrossRef puede tomar estas referencias estructuradas y, mediante su servicio de matching, verificarlas contra su base de datos:

- ¿El DOI citado existe y corresponde al artículo descrito?
- ¿El título, autores y año coinciden con los registrados en CrossRef?
- ¿Hay errores tipográficos en el DOI que puedan corregirse automáticamente?

Este proceso de verificación mejora masivamente la calidad de los datos de citación globales, reduciendo errores que, multiplicados por millones de artículos, distorsionan seriamente métricas de impacto y análisis bibliométricos.

**Servicios derivados**

Una vez que los metadatos están en CrossRef, habilitan múltiples servicios:

**Crossref Metadata Search**: Permite a investigadores buscar artículos por múltiples criterios, encontrar DOIs, acceder a metadatos completos.

**Crossref Event Data**: Rastrea menciones de artículos en redes sociales, blogs, repositorios de datos, noticias, generando altmetrics (métricas alternativas) que complementan citas tradicionales.

**Cited-by**: CrossRef registra las relaciones de citación entre artículos, permitiendo a los lectores ver automáticamente qué artículos posteriores han citado el que están leyendo.

Todos estos servicios dependen de la calidad y estructuración de los metadatos depositados, que JATS garantiza de manera que formatos menos estructurados no pueden.

## 6. Preservación digital: JATS como formato de archivo

### El desafío de la permanencia digital

La preservación digital presenta una paradoja: los objetos digitales son simultáneamente más fáciles de copiar (perfectamente, sin degradación) que los objetos físicos, pero también incomparablemente más frágiles ante la obsolescencia tecnológica. Un libro impreso del siglo XV permanece legible con la tecnología más simple (ojos humanos). Un disco de 5.25 pulgadas de la década de 1980 es prácticamente inaccesible hoy porque las unidades de lectura ya no existen.

La literatura científica digital enfrenta este desafío magnificado: no solo debe preservarse el texto, sino su estructura, contexto, y relaciones con otros documentos. Un artículo científico no es un objeto aislado sino un nodo en una red de conocimiento; su valor depende parcialmente de estas relaciones.

### JATS como formato de preservación: ventajas estructurales

JATS fue diseñado considerando explícitamente requisitos de preservación a largo plazo:

**Independencia de plataforma**: No requiere software, sistema operativo o hardware específico. Cualquier sistema que pueda procesar texto plano y entender reglas XML puede leer JATS.

**Especificación pública**: Las reglas de JATS están documentadas públicamente por NISO, no controladas por una entidad comercial. Incluso si NISO desapareciera, la especificación permanece disponible para implementar parsers y transformadores.

**Texto plano**: A diferencia de formatos binarios, JATS es texto legible. En el escenario apocalíptico donde todo software XML se perdiera, un humano con paciencia podría aún extraer el contenido de un archivo JATS.

**Separación de contenido y presentación**: Los detalles de cómo debe verse un artículo (tipografía, colores, márgenes) cambian con las modas y tecnologías. JATS preserva el contenido y estructura semántica, permitiendo re-presentación según necesidades futuras.

**Riqueza de metadatos**: JATS preserva no solo el texto del artículo sino todos los metadatos necesarios para contextualizar, atribuir y entender el documento: autores, afiliaciones, financiamiento, licencias, historia de publicación.

### Iniciativas globales de preservación basadas en JATS

Las principales infraestructuras de preservación digital del mundo científico han convergido en JATS como formato preferido:

#### CLOCKSS (Controlled LOTS of Copies Keep Stuff Safe)

CLOCKSS opera bajo el principio de "muchas copias distribuidas mantienen las cosas seguras". Mantiene múltiples copias de contenido en nodos geográficamente dispersos (actualmente 12 nodos en diferentes continentes), administrados por bibliotecas de investigación de prestigio.

El contenido se mantiene en "archivo oscuro": no es públicamente accesible mientras la fuente original (la editorial) permanezca operativa. Solo se "activa" (hace públicamente accesible) si la fuente falla, por ejemplo, si la editorial quiebra o deja de mantener el contenido en línea.

CLOCKSS acepta múltiples formatos, pero JATS es preferido porque garantiza que el contenido puede ser efectivamente preservado y representado en el futuro. Su política de desarrollo de colecciones establece que para material depositado vía FTP, aceptan "JATS, BITS [Book Interchange Tag Suite, el equivalente de JATS para libros], y cualquier otro XML bien formado".

#### Portico

Portico, operado por ITHAKA (la organización detrás de JSTOR), es un servicio de preservación digital al que las bibliotecas se suscriben. Garantiza acceso continuo a contenido académico si los editores originales no pueden mantenerlo disponible.

Portico migra contenido a formatos normalizados para preservación, y JATS es el formato preferido para revistas académicas. Esta normalización es crucial: permite a Portico mantener contenido de miles de editores diferentes en formatos consistentes que facilitan preservación a largo plazo.

#### LOCKSS y PKP Preservation Network

LOCKSS (Lots of Copies Keep Stuff Safe) es un programa de código abierto desarrollado por la Biblioteca de Stanford que permite a bibliotecas crear redes descentralizadas de preservación. Múltiples instituciones mantienen copias del mismo contenido, verificándose mutuamente periódicamente para detectar y corregir corrupción de archivos.

El PKP Preservation Network, basado en LOCKSS, está específicamente diseñado para revistas publicadas con Open Journal Systems (OJS), la plataforma de gestión editorial de código abierto más usada en el mundo. Revistas que usan OJS pueden unirse automáticamente a la red, depositando su contenido JATS para preservación distribuida.

### Estrategias de preservación: migración vs. emulación

La preservación digital generalmente se aborda mediante dos estrategias: **migración** (convertir contenido a nuevos formatos según tecnologías evolucionan) o **emulación** (mantener el formato original y crear emuladores de tecnologías obsoletas).

JATS facilita la migración porque es XML bien formado con especificación pública. Cuando futuras tecnologías de presentación emerjan (¿realidad aumentada? ¿interfaces neurales?), el contenido JATS puede migrarse a nuevos formatos de presentación sin pérdida de información porque la estructura semántica está explícita.

Los formatos dependientes de presentación (PDF) o software propietario requieren emulación: mantener funcionando software antiguo para leer formatos antiguos, tarea que se vuelve exponencialmente más difícil con el tiempo.

### Preservación como acto político: soberanía del conocimiento

Para regiones como Latinoamérica, la preservación digital del conocimiento científico en formatos abiertos y estándares públicos tiene dimensiones de soberanía epistemológica.

Si el conocimiento científico producido en la región depende de formatos propietarios controlados por corporaciones del Norte Global, la permanencia de ese conocimiento depende de decisiones comerciales sobre las cuales la región no tiene control. Si un formato propietario se descontinúa, el conocimiento codificado en ese formato puede volverse inaccesible.

JATS, como estándar público mantenido por una organización de estándares sin fines de lucro, con especificación abierta e implementaciones de software libre disponibles, representa una infraestructura de conocimiento que no puede ser arbitrariamente clausurada o monetizada por actores comerciales.

La adopción masiva de JATS por SciELO y Redalyc debe entenderse en este contexto: no es solo una decisión técnica, sino una afirmación de que el conocimiento científico latinoamericano debe preservarse en formatos que garanticen su accesibilidad independientemente de dinámicas comerciales globales.


## 7. Desafíos, limitaciones y futuro de JATS

### Curva de aprendizaje y recursos necesarios

La adopción de JATS no es trivial. Representa una transformación significativa en los flujos de trabajo editoriales que requiere:

**Capacitación técnica**: Editores, correctores y personal de producción deben entender conceptos de marcado semántico, estructuración XML, validación de esquemas. Estas competencias no son tradicionalmente parte de la formación de editores.

**Inversión de tiempo**: El proceso de marcación, especialmente cuando se realiza manualmente o con supervisión humana de marcación automática, es significativamente más largo que la simple generación de PDFs. Esta inversión debe justificarse mostrando beneficios a largo plazo.

Para revistas pequeñas, especialmente en humanidades y ciencias sociales, con equipos editoriales reducidos y presupuestos limitados, estos requisitos pueden parecer prohibitivos. **Este es el desafío real de gbpublisher**.

### Tensión entre estándares globales y necesidades locales

Como evidencia la controversia SciELO-Redalyc, la adopción de un estándar global no elimina automáticamente heterogeneidad. Diferentes actores tienen necesidades legítimamente diferentes que pueden requerir extensiones o especializaciones del estándar.

JATS permite extensibilidad: comunidades pueden añadir elementos y atributos específicos a sus necesidades. Esta flexibilidad es necesaria para que el estándar sea útil en contextos diversos. Sin embargo, excesiva flexibilidad fragmenta el ecosistema: si cada implementación de JATS es sustancialmente diferente, la interoperabilidad prometida se erosiona.

El equilibrio es delicado y requiere gobernanza comunitaria activa. JATS4R (JATS for Reuse) representa un esfuerzo importante en esta dirección, estableciendo consensos sobre mejores prácticas sin requerir modificaciones al estándar formal.

### Calidad del marcado: validez sintáctica vs. utilidad semántica

Un desafío técnico significativo es que la validación automática contra DTD o XSD verifica únicamente sintaxis, no semántica. Como documenta el análisis de errores en artículos JATS publicados, existen archivos sintácticamente válidos pero semánticamente problemáticos:

- Referencias con componentes mal identificados (autores etiquetados como títulos, etc.)
- Afiliaciones institucionales con estructura incorrecta que impide extracción automática
- Metadatos de idioma incorrectos o inconsistentes
- Uso de elementos obsoletos de versiones antiguas del estándar

Estos errores pasan la validación sintáctica pero degradan la utilidad de JATS para búsquedas, descubrimiento, e interoperabilidad. Detectarlos requiere validaciones semánticas más sofisticadas.

La comunidad debe desarrollar herramientas más robustas de control de calidad que vayan más allá de validación sintáctica, verificando utilidad práctica del marcado.

### Contenido no textual: multimedia, datos, software

JATS fue diseñado principalmente para artículos textuales con elementos gráficos estáticos (figuras, tablas). La ciencia contemporánea produce crecientemente contenidos que desafían este modelo:

**Videos y multimedia interactiva**: Experimentos grabados, visualizaciones 3D, simulaciones interactivas. JATS puede referenciar estos elementos pero su capacidad para describirlos semánticamente es limitada.

**Datasets**: Muchos artículos ahora se acompañan de grandes conjuntos de datos. JATS puede enlazar a estos datos pero no describirlos internamente.

**Software y código**: Artículos sobre métodos computacionales incluyen código fuente. ¿Cómo se preserva y estructura código dentro de JATS?

El futuro de JATS debe abordar estos desafíos, posiblemente mediante mayor integración con estándares complementarios: DataCite para datasets, CodeMeta para software, estándares de video para multimedia.

### Inteligencia artificial y automatización del marcado

La producción manual de JATS es laboriosa. Herramientas como Marcalyc incorporan automatización basada en IA, pero la tecnología continúa evolucionando rápidamente.

Los modelos de lenguaje de gran escala (Large Language Models, LLMs) contemporáneos muestran una capacidad impresionante para entender estructura de documentos y extraer información semántica. ¿Podría la próxima generación de herramientas JATS usar IA para marcado casi completamente automático, requiriendo solo supervisión humana mínima?

Esta posibilidad es prometedora pero requiere precaución: los LLMs pueden "alucinar" información que no existe o malinterpretar estructuras ambiguas. La validación humana permanecerá esencial, al menos por el futuro previsible.

### Convergencia con iniciativas de ciencia abierta

JATS existe dentro de un ecosistema más amplio de iniciativas de ciencia abierta: preregistro de estudios, datos abiertos, revisión por pares abierta, credenciales digitales persistentes (ORCID), taxonomías de contribución (CRediT).

La integración efectiva de JATS con estas iniciativas requiere coordinación:

- **ORCID**: JATS debe incorporar identificadores ORCID para todos los autores, permitiendo desambiguación de nombres y construcción de perfiles de investigador completos
- **CRediT**: Especificar roles de cada autor según la taxonomía CRediT (conceptualización, metodología, análisis, redacción, etc.)
- **Datos abiertos**: Enlazar artículos JATS con datasets en repositorios como Zenodo, Dryad, Figshare, con metadatos que describen la relación
- **Preprints**: Conectar artículos publicados con sus versiones preprint en servidores como arXiv, bioRxiv, permitiendo rastrear evolución del documento

Estas integraciones no son opcionales sino necesarias para realizar plenamente la visión de ciencia abierta.


## 8. Conclusiones: JATS como infraestructura epistémica

XML-JATS ha trascendido su origen como especificación técnica para convertirse en infraestructura crítica del ecosistema global de conocimiento científico. **No es opcional** porque el conocimiento científico contemporáneo existe fundamentalmente como red distribuida, interconectada y en constante evolución. Esta red requiere estándares comunes para funcionar; sin ellos, la promesa de ciencia abierta, accesible y preservada colapsa en fragmentación y aislamiento.

Las razones por las cuales JATS se ha vuelto indispensable son estructurales, no meramente tecnológicas:

**Interoperabilidad sistémica**: En un ecosistema con miles de revistas, decenas de plataformas, cientos de repositorios y múltiples sistemas de descubrimiento, la única alternativa a un estándar común es el caos informacional. JATS proporciona el lenguaje común que permite que estos sistemas heterogéneos se comuniquen sin pérdida de significado.

**Preservación garantizada**: La obsolescencia tecnológica amenaza constantemente la accesibilidad del conocimiento digital. JATS, como formato abierto, basado en texto, con especificación pública, ofrece las mejores garantías disponibles de que el conocimiento científico de hoy permanecerá accesible para investigadores del futuro.

**Mandatos institucionales**: Organismos financiadores, instituciones académicas y políticas de ciencia abierta crecientemente requieren o fuertemente prefieren contenido en formatos estructurados y estándares. JATS satisface estos requisitos de manera que formatos menos estructurados no pueden.

**Búsqueda y descubrimiento enriquecidos**: La estructuración semántica de contenido en JATS habilita formas de búsqueda, análisis y extracción de conocimiento imposibles con formatos orientados a presentación. Esto no es lujo sino necesidad en un contexto de explosión informacional donde la capacidad de encontrar, filtrar y sintetizar conocimiento relevante es crítica.

**Accesibilidad universal**: La estructura semántica de JATS facilita la generación de contenido accesible para personas con discapacidad, cumpliendo tanto imperativos éticos como legales.

Sin embargo, reconocer la importancia de JATS no debe cegarnos a sus desafíos. La curva de aprendizaje es real, especialmente para revistas pequeñas con recursos limitados. Los costos de transición no son triviales. La tensión entre estandarización y flexibilidad requiere gobernanza cuidadosa. La calidad del marcado no está garantizada por la mera adopción del estándar.

Abordar estos desafíos requiere esfuerzo comunitario sostenido:

- **Herramientas mejoradas**: Invertir en desarrollo de software de código abierto que simplifique producción y validación de JATS de alta calidad
- **Capacitación accesible**: Desarrollar recursos educativos multilingües, adaptados a diferentes niveles de sofisticación técnica
- **Soporte institucional**: Reconocer que la transición a JATS requiere recursos y proporcionar apoyo financiero y técnico a revistas, especialmente aquellas en regiones con menos recursos
- **Gobernanza participativa**: Asegurar que la evolución del estándar incorpore voces del Sur Global, humanidades, ciencias sociales, no solo ciencias biomédicas del Norte Global
- **Estándares de calidad**: Desarrollar y mantener especificaciones de mejores prácticas (como JATS4R) que vayan más allá de validación sintáctica

Para Latinoamérica específicamente, la adopción masiva de JATS por SciELO y Redalyc representa una oportunidad histórica de establecer infraestructura epistémica regional que sea simultáneamente:

- **Globalmente interoperable**: Conectada con sistemas internacionales de descubrimiento y preservación
- **Regionalmente soberana**: No dependiente de infraestructuras comerciales propietarias
- **Comprometida con acceso abierto**: Estructurada para facilitar acceso sin barreras económicas
- **Sostenible a largo plazo**: Basada en estándares abiertos y software libre que pueden mantenerse con recursos regionales

Esta combinación de integración global y soberanía regional es precisamente lo que hacen posible los estándares abiertos como JATS.

En última instancia, XML-JATS no es opcional porque representa algo más fundamental que una especificación técnica: representa un compromiso colectivo de la comunidad científica global de mantener el conocimiento científico como bien común accesible, preservado e interoperable. En un mundo donde el conocimiento está crecientemente mercantilizado y fragmentado, este compromiso no es meramente valioso sino esencial para la viabilidad misma de la empresa científica como proyecto humano compartido.

El conocimiento científico ha sobrevivido milenios porque cada generación ha asumido la responsabilidad de preservarlo y transmitirlo. En la era digital, esa responsabilidad incluye adoptar estándares que garanticen que nuestras contribuciones al conocimiento permanezcan accesibles y útiles mucho después de que las tecnologías particulares de hoy hayan desaparecido. XML-JATS es nuestra mejor respuesta actual a esa responsabilidad milenaria.


## Referencias

- Aguado-López, E., Becerril-García, A., & Chávez-Ávila, S. (2016). Conectando al Sur con la ciencia global: El nuevo modelo de publicación en América Latina y el Caribe, no comercial, colaborativo y sustentable. *XML JATS Redalyc*. Recuperado de https://xmljatsredalyc.org/

- Aguado-López, E., Becerril-García, A., & Leonardo-Valentín, E. (2024). Manual de usuario Marcalyc versión 4.0. Sistema de Información Científica Redalyc.

- Beagrie, N. (2013). *Preservación, fiabilidad y acceso continuado a las revistas digitales*. Digital Preservation Coalition Technology Watch Report.

- Becerril-García, A., Aguado-López, E., & Sánchez Pereyra, A. (2023). La edición científica marcada por el XML JATS: des(encuentros) entre Markup y Marcalyc. *Palabra Clave (La Plata)*, 12(2), e179.

- Cristiani-Sienra, A. (2016). *Journal Article Tag Suite (JATS): situación actual y análisis de implantación del estándar promovido por NISO para revistas científicas basado en XML* [Trabajo de fin de máster]. Universidad Carlos III de Madrid.

- CrossRef. (2020). *Using JATS XML*. Recuperado de https://www.crossref.org/documentation/register-maintain-records/direct-deposit-xml/jats-xml/

- García Boyé, J. L. (2020). Las ventajas de utilizar XML-JATS en revistas científicas. *Aula Magna 2.0*. Recuperado de https://cuedespyd.hypotheses.org/8881

- Gil Leyva, I. (2022). La edición digital y la lógica semántica de la web. En *Prácticas editoriales en el siglo XXI*. México: Universidad Nacional Autónoma de México.

- Gross, M. (2025). From Valid XML to Valuable XML: When "Good" Matters More Than "Valid". En *Journal Article Tag Suite Conference (JATS-Con) Proceedings 2025*. Bethesda (MD): National Center for Biotechnology Information.

- Guzmán-Useche, M. F., & Rodríguez-Contreras, L. (2016). Análisis comparativo de herramientas de marcación XML-JATS para revistas científicas. *Revista Interamericana de Bibliotecología*, 39(2), 103-116.

- JATS4R Group. (2018). *JATS for Reuse: Best practices for JATS tagging*. Recuperado de https://jats4r.org/

- McKnight, C. (1997). Electronic journals: What do users think of them? En *Proceedings of International Symposium on Research, Development and Practice in Digital Libraries*.

- National Center for Biotechnology Information [NCBI]. (2012). *JATS: Journal Article Tag Suite, version 1.0*. Recuperado de https://jats.nlm.nih.gov/

- National Information Standards Organization [NISO]. (2024). *ANSI/NISO Z39.96-2024: JATS: Journal Article Tag Suite, version 1.4*.

- Packer, A. L. (2014). Los criterios de indexación de SciELO se alinean con la comunicación en la investigación de vanguardia. *SciELO en Perspectiva*. Recuperado de https://blog.scielo.org/es/

- Packer, A. L., & Gómes, N. (2023). SciELO Marketplace: Una interfaz para servicios editoriales. *SciELO en Perspectiva*.

- Rozemblum, C. (2021). Desafíos y oportunidades en la adopción de XML-JATS en revistas científicas de América Latina. *Palabra Clave (La Plata)*, 10(2), e098.

- Sánchez-Pereyra, A. (2017). SciELO: 20 años de acceso abierto en América Latina. En *Historia de la ciencia abierta en América Latina*. Buenos Aires: CLACSO.

- W3C (World Wide Web Consortium). (2016). *Extensible Markup Language (XML) 1.0 (Fifth Edition)*. Recuperado de https://www.w3.org/TR/xml/

- Zetter Patiño, E. (2018). *El desarrollo de JATS y su implementación global* [Tesis de maestría]. Universidad Nacional Autónoma de México.

**Nota sobre fuentes**: Este artículo se basa en documentación oficial de NISO, NCBI, SciELO, Redalyc, CrossRef, CLOCKSS y otras instituciones del ecosistema de publicación científica, complementada con literatura académica sobre edición científica, preservación digital e infraestructuras de conocimiento. Todas las afirmaciones técnicas sobre JATS están verificadas contra la especificación oficial ANSI/NISO Z39.96-2024.

