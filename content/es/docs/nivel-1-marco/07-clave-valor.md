---
title: "El paradigma clave=valor en los lenguajes de marcas: fundamentos, historia e implementaciones en flujos editoriales científicos"
weight: 7
description: >
  La producción editorial científica contemporánea descansa sobre una infraestructura de metadatos que, en gran medida, permanece invisible para los actores del proceso. Autores, correctores y editores interactúan cotidianamente con formularios, campos de ingreso y plantillas sin percibir que detrás de cada uno de esos elementos opera un principio de organización de la información de notable antigüedad y coherencia formal: el paradigma clave=valor.
---

## 1. Introducción


El paradigma **clave=valor** consiste, en su formulación más elemental, en la asignación de un dato —el valor— a un identificador unívoco —la clave— dentro de un sistema que garantiza la interpretación consistente de esa relación. Su aparente simplicidad es engañosa: sobre esta estructura mínima se construyen los metadatos bibliográficos, los esquemas de configuración de herramientas de composición tipográfica, los atributos de los documentos XML, los encabezados de conversión de Pandoc y los registros de los grandes indexadores internacionales. En todos estos contextos, el principio subyacente es el mismo, aunque su sintaxis, sus convenciones y sus restricciones varíen de forma significativa.

La relevancia de este paradigma para los flujos editoriales científicos no es meramente técnica. Cada vez que un sistema de gestión editorial asigna un DOI, cada vez que un indexador valida la afiliación institucional de un autor, cada vez que un conversor genera un archivo JATS a partir de un documento fuente, está operando sobre estructuras clave=valor. La normalización de esas estructuras —su correcta definición, su coherencia interna y su compatibilidad con los estándares internacionales— determina en buena medida la visibilidad y la recuperabilidad de la producción científica en el ecosistema global de la información.

El presente artículo se propone tres objetivos articulados. En primer lugar, reconstruir la historia del paradigma en el contexto de los lenguajes de marcas y los flujos editoriales, identificando los momentos de inflexión que consolidaron su adopción. En segundo lugar, analizar comparativamente sus implementaciones más relevantes para la producción editorial científica: BibTeX, BibLaTeX, LaTeX, XML/JATS, YAML, TOML, Markdown front matter y JSON. En tercer lugar, examinar el estado actual del paradigma en la cadena de producción editorial y proyectar sus tensiones y tendencias en el contexto de la presión creciente de los indexadores internacionales sobre los flujos de trabajo de las revistas científicas latinoamericanas.

El artículo no se dirige a un lector con formación técnica en informática, sino al editor científico que necesita comprender los fundamentos de las herramientas que usa —o que debería usar— para garantizar la calidad estructural de los documentos que produce. En ese sentido, el análisis técnico está subordinado en todo momento a su pertinencia para la práctica editorial.


## 2. Antecedentes históricos

### El problema previo: la información sin estructura

Antes de que existieran los lenguajes de marcas tal como los conocemos hoy, la información textual circulaba en formatos que no distinguían entre contenido y descripción del contenido. Un documento era, en el mejor de los casos, una secuencia de caracteres con convenciones tipográficas implícitas, legibles para el ojo humano pero opacas para cualquier sistema de procesamiento automático. El problema no era menor: en contextos donde la recuperación de información bibliográfica dependía de fichas físicas y catálogos manuales, la ausencia de estructura formal no representaba un obstáculo insalvable. Pero a medida que los sistemas de cómputo comenzaron a incorporarse a la gestión documental, la necesidad de estructurar la información de manera que las máquinas pudieran interpretarla se volvió urgente.

Esta urgencia se manifestó primero en el ámbito de las bibliotecas y los sistemas de recuperación de información. El formato MARC (*Machine-Readable Cataloging*), desarrollado por la Biblioteca del Congreso de los Estados Unidos a mediados de la década de 1960, fue una de las primeras respuestas sistemáticas a ese problema [1]. MARC organizaba los registros bibliográficos mediante campos etiquetados numéricamente, cada uno con indicadores y subcampos que precisaban el tipo de dato contenido. Aunque su sintaxis difería de la forma canónica clave=valor, el principio subyacente era el mismo: cada dato debía estar asociado a un identificador que permitiera su interpretación unívoca. MARC estableció así un antecedente conceptual fundamental para todo el desarrollo posterior.

### SGML y la formalización del marcado estructural

El siguiente momento de inflexión fue la publicación, en 1986, de la norma ISO 8879, que definía el *Standard Generalized Markup Language* (SGML) [2]. SGML no era un lenguaje en sí mismo sino una metalenguaje: un sistema formal para definir lenguajes de marcas mediante la especificación de tipos de documentos (DTD, *Document Type Definition*). Su contribución al paradigma clave=valor fue doble. Por un lado, formalizó el concepto de atributo como mecanismo para asociar propiedades a los elementos de un documento: en SGML, un elemento podía llevar atributos expresados exactamente en la forma `clave="valor"`. Por otro lado, al separar explícitamente la estructura lógica del documento de su presentación visual, SGML estableció las condiciones para que los metadatos —expresados como atributos o como elementos específicos— tuvieran un rol formal y no meramente decorativo en la arquitectura del documento.

La influencia de SGML fue enorme, aunque su adopción masiva quedó limitada por la complejidad de su implementación. Fue el suelo del que emergieron tanto HTML como XML, y a través de ellos, buena parte de la infraestructura de publicación digital contemporánea.

### Los sistemas Unix y la cultura de los archivos de configuración

En paralelo al desarrollo de SGML, el entorno Unix consolidaba una cultura de configuración basada en archivos de texto plano. Los archivos `.conf`, los registros de variables de entorno y, más tarde, los archivos `.ini` popularizados en el mundo de DOS y Windows, establecieron en la práctica cotidiana de los administradores de sistemas una forma de trabajo directamente basada en el paradigma clave=valor [3]. La sintaxis era variable pero el modelo era invariante: un identificador, un separador (habitualmente `=` o `:`), y un valor. Esta cultura de la configuración textual tuvo consecuencias duraderas: cuando los desarrolladores de herramientas editoriales buscaron formatos para expresar metadatos y opciones de procesamiento, encontraron en el paradigma clave=valor una convención ya establecida y ampliamente comprendida.

### BibTeX y la consolidación del paradigma en la academia

El momento de articulación más significativo entre el paradigma clave=valor y la producción académica fue la aparición de BibTeX, desarrollado por Oren Patashnik en 1985 como complemento del sistema de composición tipográfica TeX de Donald Knuth [4]. BibTeX definió un formato de base de datos bibliográfica basado íntegramente en el paradigma clave=valor. Cada registro correspondía a un tipo de referencia (`@article`, `@book`, `@inproceedings`, etc.) y sus campos eran pares clave=valor que describían los atributos bibliográficos de la obra referenciada:

```bibtex
@article{apellido2024,
  author  = {Apellido, Nombre},
  title   = {Título del artículo},
  journal = {Nombre de la revista},
  year    = {2024},
  volume  = {12},
  number  = {3},
  pages   = {45--67},
  doi     = {10.xxxx/xxxxx}
}
```

La importancia de BibTeX para el paradigma que nos ocupa excede su función como gestor de referencias. Por primera vez, un sector amplio de la comunidad académica —no solo los informáticos— comenzó a trabajar directamente con estructuras clave=valor como parte de su práctica cotidiana de escritura. El formato BibTeX era lo suficientemente legible para el ojo humano como para ser editado manualmente, y lo suficientemente formal como para ser procesado automáticamente. Esta doble legibilidad es una característica que reaparecerá en todos los formatos que el presente artículo analiza, y que constituye uno de los criterios de evaluación más relevantes para los flujos editoriales.

BibTeX presentaba, sin embargo, limitaciones estructurales que se harían más evidentes a medida que las exigencias de la publicación científica crecían en complejidad: soporte deficiente para Unicode, ausencia de tipos de entrada para recursos digitales, dificultades para manejar apellidos compuestos y filiaciones múltiples, y escasa flexibilidad para adaptar los estilos de citación a distintas disciplinas. Estas limitaciones fueron el motor del desarrollo de BibLaTeX, que se abordará en la sección comparativa.

### XML y la madurez del paradigma

La publicación de la especificación XML 1.0 por el W3C en 1998 representó la síntesis más influyente de las tradiciones anteriores [5]. XML simplificó SGML hasta hacerlo implementable de forma generalizada, mantuvo el mecanismo de atributos como forma canónica de expresar pares clave=valor, y añadió la posibilidad de definir vocabularios especializados mediante esquemas. Para la publicación científica, la consecuencia más relevante fue el desarrollo de la familia de estándares JATS (*Journal Article Tag Suite*), que adoptó y extendió el paradigma clave=valor para estructurar no solo los metadatos sino la totalidad del contenido de los artículos científicos. Este desarrollo se analiza en detalle en las secciones siguientes.

## 3. Fundamentos conceptuales

### Definición formal del paradigma

El paradigma clave=valor puede definirse formalmente como un modelo de representación de la información en el que cada dato queda unívocamente identificado por un nombre —la clave— y asociado a un contenido —el valor— mediante una relación de asignación explícita. En su expresión más abstracta, el modelo puede representarse como un conjunto de pares ordenados:

```
{ (k₁, v₁), (k₂, v₂), ..., (kₙ, vₙ) }
```

donde cada `kᵢ` es un identificador único dentro del espacio de nombres del sistema, y cada `vᵢ` es el dato asignado a ese identificador. Esta estructura corresponde, en términos de la teoría de conjuntos, a una función parcial: a cada clave le corresponde como máximo un valor, aunque no toda clave necesita tener un valor asignado en un registro dado.

Tres propiedades definen la utilidad del paradigma en contextos de procesamiento de información:

**Univocidad de la clave.** Dentro de un espacio de nombres dado, cada clave identifica un único tipo de dato. Esta propiedad es la que permite al sistema procesador interpretar el valor sin ambigüedad: si la clave es `author`, el valor será tratado como autor con independencia del orden en que aparezca en el registro o del formato en que esté expresado.

**Independencia del orden.** A diferencia de los formatos posicionales —donde el significado de un dato depende de su posición en la secuencia—, en el paradigma clave=valor el orden de los pares es irrelevante para la interpretación. Esta propiedad tiene consecuencias prácticas importantes para los flujos editoriales: permite agregar, omitir o reordenar campos sin alterar la validez del registro.

**Extensibilidad.** El modelo admite la incorporación de nuevas claves sin necesidad de redefinir la estructura completa. Esta propiedad es la que ha permitido que distintos estándares adopten el paradigma y lo extiendan para sus necesidades específicas sin romper la compatibilidad con los sistemas que procesan únicamente el subconjunto de claves que conocen.

### Tipología de valores

No todos los valores son iguales. Una de las fuentes más frecuentes de complejidad —y de errores— en los flujos editoriales es la falta de claridad sobre el tipo de valor que admite cada clave. Es posible establecer una tipología funcional que resulta operativamente útil independientemente del lenguaje o formato considerado.

**Valores escalares.** Son los más simples: una cadena de texto, un número, una fecha, un booleano. La mayoría de los campos bibliográficos básicos son escalares: el título de un artículo, el año de publicación, el número de volumen. Su procesamiento es directo, pero presentan desafíos de normalización que no deben subestimarse: un año puede expresarse como `2024`, `"2024"` o `2024-01-01` según el sistema, y la compatibilidad entre representaciones no está garantizada.

**Valores de lista.** Cuando una clave puede tener múltiples valores del mismo tipo, se requiere una estructura de lista. El caso más frecuente en el contexto editorial es la autoría: un artículo puede tener uno o varios autores, y cada sistema resuelve esta situación de forma diferente. BibTeX usa el separador `and` dentro de la cadena de texto; YAML usa listas nativas con guiones; XML replica el elemento con múltiples instancias. La disparidad en la representación de listas es uno de los puntos de fricción más habituales en la interoperabilidad entre sistemas.

**Valores estructurados.** En algunos casos, el valor de una clave es en sí mismo un conjunto de pares clave=valor. La afiliación institucional de un autor, por ejemplo, puede requerir expresar simultáneamente el nombre de la institución, el país, el identificador ROR (*Research Organization Registry*) y la unidad académica específica. Esta situación genera estructuras anidadas que distintos lenguajes resuelven con diferente grado de elegancia y parsimonia.

**Valores controlados.** Muchos campos bibliográficos no admiten valores libres sino que deben tomarse de un vocabulario controlado: los tipos de contribución según CRediT, los identificadores de licencias Creative Commons, los códigos de idioma ISO 639, las categorías temáticas de los indexadores. La distinción entre valores libres y controlados es crítica para la validación de registros y para la interoperabilidad con los sistemas de los indexadores.

### Atributo, metadato y propiedad: una distinción necesaria

En la literatura técnica y en la práctica editorial, los términos *atributo*, *metadato* y *propiedad* se usan con frecuencia de forma intercambiable, lo que genera confusión conceptual con consecuencias operativas concretas. Una distinción precisa de estos términos es necesaria para comprender el rol que el paradigma clave=valor cumple en cada nivel de la arquitectura documental.

Un **atributo** es un par clave=valor que forma parte de la estructura sintáctica de un lenguaje de marcas y que modifica o complementa el significado del elemento al que está asociado. En XML, los atributos son componentes formales de la gramática del lenguaje: `<article article-type="research-article">` expresa que el atributo `article-type` tiene el valor `research-article` para ese elemento. El atributo existe dentro del documento y no tiene existencia independiente de él.

Un **metadato** es información sobre el documento o sobre uno de sus componentes, con independencia de dónde esté almacenada esa información: puede estar dentro del propio documento, en una base de datos externa, en el encabezado de una solicitud HTTP o en un registro de un sistema de gestión editorial. Los metadatos pueden expresarse mediante atributos XML, pero no se reducen a ellos. La distinción es relevante porque en los flujos editoriales modernos los mismos metadatos deben existir en múltiples representaciones simultáneas: como atributos en el archivo JATS, como campos en la base de datos del sistema de gestión, como parámetros en la solicitud de registro del DOI y como entradas en el índice del indexador.

Una **propiedad** es un par clave=valor que describe una característica de un objeto en el contexto de un modelo de datos formal, con independencia de su representación sintáctica. El término proviene del paradigma de la programación orientada a objetos y de los lenguajes de descripción de recursos como RDF. En el contexto de la publicación científica, el uso de vocabularios de propiedades como Dublin Core o Schema.org implica que los metadatos no solo describen el documento sino que lo sitúan en una red de relaciones semánticas con otros objetos de información.

La distinción entre estos tres niveles —sintáctico, documental y semántico— tiene implicaciones directas para el diseño de flujos editoriales. Un sistema que solo gestiona atributos opera en el nivel sintáctico y produce documentos bien formados pero no necesariamente interoperables. Un sistema que gestiona metadatos en múltiples representaciones opera en el nivel documental y garantiza la compatibilidad con los sistemas externos. Un sistema que gestiona propiedades en el sentido semántico del término contribuye a la recuperabilidad de la producción científica en el ecosistema de los datos enlazados. Estos tres niveles no son excluyentes sino complementarios, y los flujos editoriales de mayor madurez los articulan de forma integrada.

### El paradigma clave=valor como contrato entre sistemas

Una consecuencia práctica de las propiedades formales del paradigma que merece atención específica es su función como protocolo de interoperabilidad. Cuando dos sistemas acuerdan un conjunto de claves y los tipos de valor admitidos para cada una, están estableciendo un contrato que permite el intercambio de información sin que ninguno de los sistemas necesite conocer la arquitectura interna del otro. Este es, precisamente, el principio sobre el que se construyen los estándares de metadatos para la publicación científica: Dublin Core, JATS, DataCite, Crossref Metadata Schema y los esquemas de los principales indexadores son todos, en última instancia, especificaciones de contratos clave=valor entre los productores de contenido científico y los sistemas que lo gestionan, indexan y distribuyen.

Para el editor científico, comprender este principio tiene una consecuencia inmediata: la calidad de los metadatos no es un problema estético ni burocrático, sino estructural. Un valor mal formado en la clave `author` no es solo un error tipográfico: es una violación del contrato que puede impedir la correcta atribución de la autoría en los sistemas de los indexadores, afectar el cómputo de métricas y citas, y comprometer la recuperabilidad del artículo en las búsquedas especializadas.

## 4. Implementaciones en el ecosistema editorial

### BibTeX

BibTeX estableció el modelo de referencia para la representación de datos bibliográficos en el paradigma clave=valor dentro del mundo académico. Su sintaxis define dos elementos estructurales: el tipo de entrada, que determina el conjunto de claves válidas para ese registro, y los campos, que son los pares clave=valor que contienen los datos bibliográficos propiamente dichos.

```bibtex
@article{moyano2024,
  author   = {Moyano, Alberto},
  title    = {Flujos editoriales y metadatos estructurados},
  journal  = {Revista de Edición Científica},
  year     = {2024},
  volume   = {8},
  number   = {2},
  pages    = {12--34},
  doi      = {10.xxxx/xxxxx},
  issn     = {1234-5678}
}
```

BibTeX distingue entre campos obligatorios y opcionales para cada tipo de entrada. Esta distinción opera como una forma primitiva de validación: un procesador BibTeX emitirá advertencias cuando falten campos obligatorios, aunque no impedirá la compilación. Para los flujos editoriales, esta permisividad es una fuente de problemas: registros incompletos que superan la validación formal pero generan referencias mal formadas en el documento final.

Las limitaciones estructurales de BibTeX son bien conocidas y han sido ampliamente documentadas. Las más relevantes para la producción editorial científica contemporánea son tres. Primero, la ausencia de soporte nativo para Unicode obligó durante décadas a los autores a codificar caracteres especiales mediante comandos LaTeX (`{\'e}` en lugar de `é`), lo que hace los archivos `.bib` difícilmente procesables por sistemas que no sean el propio LaTeX. Segundo, el modelo de autoría —una cadena de texto con autores separados por `and`— no distingue entre nombre y apellido de forma estructural, lo que genera ambigüedades en apellidos compuestos, partículas nobiliarias y convenciones de nombre propias de distintas culturas. Tercero, la ausencia de tipos de entrada para recursos digitales, conjuntos de datos, software y otros productos científicos contemporáneos refleja el origen del formato en una época en que el artículo impreso era la unidad casi exclusiva de la comunicación científica.

A pesar de estas limitaciones, BibTeX mantiene una presencia extensa en la producción académica, sostenida por la inercia de décadas de uso y por la compatibilidad que los sistemas de gestión de referencias —Zotero, Mendeley, JabRef— mantienen con el formato.

### BibLaTeX

BibLaTeX, desarrollado por Philipp Lehman a partir de 2006 y actualmente mantenido por un equipo activo de la comunidad LaTeX, no es una versión mejorada de BibTeX sino una reimplementación conceptual del sistema de gestión bibliográfica para LaTeX [6]. Mantiene la sintaxis clave=valor de los archivos `.bib` pero introduce cambios fundamentales en el modelo de datos, el procesamiento y la extensibilidad.

La primera diferencia relevante para los flujos editoriales es el soporte completo para Unicode. Los archivos BibLaTeX pueden contener caracteres de cualquier escritura directamente, sin necesidad de codificación mediante comandos LaTeX. Esta característica, trivial en apariencia, es determinante para la producción editorial en idiomas distintos del inglés y para la correcta representación de nombres de autores de diversas procedencias culturales.

La segunda diferencia es la descomposición estructural de los campos de autoría. BibLaTeX procesa el campo `author` reconociendo componentes: nombre de pila, apellido, prefijo y sufijo, lo que permite una gestión correcta de partículas como *de*, *van*, *von* o *da* y de las convenciones de nombre propias de distintas tradiciones culturales. Para la publicación científica latinoamericana, donde el apellido compuesto es frecuente, esta distinción tiene consecuencias directas sobre la correcta indexación de la autoría.

La tercera diferencia es la incorporación de tipos de entrada que reflejan la diversidad contemporánea de los productos científicos:

```bibtex
@dataset{lopez2024datos,
  author       = {López, María},
  title        = {Conjunto de datos sobre hábitos de lectura},
  year         = {2024},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.xxxxxxx},
  version      = {1.0}
}

@software{garcia2024herramienta,
  author       = {García, Carlos},
  title        = {Herramienta de análisis bibliométrico},
  year         = {2024},
  url          = {https://github.com/usuario/herramienta},
  version      = {2.3.1}
}
```

BibLaTeX incorpora además campos específicos para la publicación científica moderna que BibTeX no contemplaba: `orcid` para el identificador de autor, `eprint` y `eprinttype` para preprints, `urldate` para la fecha de acceso a recursos en línea, y `langid` para el idioma de la obra referenciada. Estos campos reflejan una comprensión más madura de los requisitos de los flujos editoriales contemporáneos.

El procesamiento en BibLaTeX está delegado al motor Biber, que reemplaza al procesador BibTeX clásico. Biber maneja correctamente Unicode, implementa algoritmos de ordenamiento sensibles al idioma y permite la definición de mapas de datos para transformar campos durante el procesamiento, lo que facilita la migración de registros entre distintos esquemas bibliográficos.

### LaTeX y el paquete keyval

Más allá de su rol en la gestión bibliográfica, LaTeX implementa el paradigma clave=valor como mecanismo general de configuración de paquetes y entornos. El paquete `keyval`, desarrollado por David Carlisle, formalizó este mecanismo y estableció la infraestructura sobre la que se construyeron `xkeyval`, `pgfkeys` y otros sistemas de gestión de opciones [7].

En el uso cotidiano, el paradigma clave=valor en LaTeX se manifiesta en la configuración de paquetes mediante opciones en corchetes:

```latex
\usepackage[
  backend   = biber,
  style     = vancouver,
  sorting   = none,
  maxnames  = 6,
  minnames  = 3
]{biblatex}
```

Para los flujos editoriales, la relevancia de este mecanismo está en que los estilos bibliográficos de LaTeX —incluido el estilo Vancouver utilizado en la producción científica biomédica— se configuran enteramente mediante pares clave=valor. La comprensión de esta arquitectura permite al editor técnico diagnosticar y resolver problemas de formato sin necesidad de modificar el código interno de los paquetes.

### XML y JATS

XML es, de todos los lenguajes considerados en este artículo, el que implementa el paradigma clave=valor de forma más rigurosa y con mayor respaldo normativo. Los atributos XML son pares clave=valor con tipado formal definido en el esquema (DTD o XSD), validación obligatoria y espacio de nombres controlado. En el contexto de la publicación científica, la familia de estándares JATS (*Journal Article Tag Suite*, NISO Z39.96) constituye la implementación más relevante.

JATS utiliza atributos XML para expresar metadatos en múltiples niveles del documento. En el elemento raíz del artículo, los atributos definen propiedades fundamentales del documento:

```xml
<article
  xmlns:xlink  = "http://www.w3.org/1999/xlink"
  article-type = "research-article"
  xml:lang     = "es"
  dtd-version  = "1.3">
```

En los elementos de metadatos del encabezado, JATS combina atributos con contenido de texto para expresar datos complejos:

```xml
<contrib contrib-type="author">
  <name>
    <surname>Moyano</surname>
    <given-names>Alberto</given-names>
  </name>
  <contrib-id contrib-id-type="orcid">
    https://orcid.org/0000-0000-0000-0000
  </contrib-id>
  <aff id="aff1">Estudio 2A</aff>
</contrib>
```

La distinción que JATS establece entre el atributo `contrib-type` (que clasifica el tipo de contribución) y el atributo `contrib-id-type` (que especifica el sistema de identificación utilizado) ilustra con precisión la función del paradigma clave=valor en un esquema maduro: las claves no son etiquetas arbitrarias sino términos de un vocabulario controlado cuyo significado está definido en la especificación del estándar.

Para los flujos editoriales, la importancia de JATS radica en que es el formato de intercambio exigido por los principales indexadores internacionales: PubMed Central, SciELO, Redalyc y JATS4R, entre otros. La correcta expresión de los metadatos en atributos JATS no es opcional sino que determina la aceptación o el rechazo del archivo por parte de los sistemas de validación de los indexadores.

### YAML

YAML (*YAML Ain't Markup Language*) es un lenguaje de serialización de datos diseñado con énfasis en la legibilidad humana [8]. Su adopción en los flujos editoriales se produjo principalmente a través de dos vías: como formato de configuración de herramientas —Hugo, Jekyll, MkDocs, Pandoc— y como formato de metadatos en el encabezado de documentos Markdown.

La sintaxis YAML para pares clave=valor es la más cercana al lenguaje natural de todas las consideradas en este artículo:

```yaml
title: "El paradigma clave=valor en los lenguajes de marcas"
author:
  - name: "Moyano, Alberto"
    orcid: "0000-0000-0000-0000"
    affiliation: "Estudio 2A"
date: "2024-06-01"
lang: es
bibliography: referencias.bib
csl: vancouver.csl
```

YAML admite valores escalares, listas y estructuras anidadas con una sintaxis uniforme y sin necesidad de delimitadores explícitos de apertura y cierre. Esta característica lo hace especialmente adecuado para la expresión de metadatos bibliográficos complejos, como la autoría múltiple con afiliaciones institucionales diferenciadas.

Su relevancia para los flujos editoriales que utilizan Pandoc es central: el encabezado YAML de un documento Markdown es la fuente de metadatos que Pandoc utiliza para poblar los archivos de salida, incluyendo los documentos JATS. La correcta estructuración de este encabezado determina la calidad de todos los formatos generados en la cadena de conversión.

YAML presenta, sin embargo, una trampa de complejidad que no debe subestimarse. Su diseño admite un conjunto de características avanzadas —anclajes, alias, tipos explícitos, documentos múltiples— que pueden generar comportamientos inesperados si no se conocen con precisión. En particular, ciertos valores escalares son interpretados automáticamente como tipos no textuales: `yes` y `no` pueden interpretarse como booleanos, y valores numéricos con ceros iniciales pueden interpretarse como octales. Para los flujos editoriales, la recomendación práctica es usar comillas en todos los valores que puedan generar ambigüedad.

### TOML

TOML (*Tom's Obvious, Minimal Language*) fue diseñado por Tom Preston-Werner en 2013 con el objetivo explícito de ser un formato de configuración más estricto y predecible que YAML [9]. Su adopción en flujos editoriales es más reciente y más acotada, pero su presencia en herramientas relevantes como Hugo —que acepta tanto YAML como TOML para la configuración del sitio y los encabezados de páginas— lo hace pertinente en este análisis.

```toml
title = "El paradigma clave=valor en los lenguajes de marcas"
date = 2024-06-01
lang = "es"

[[author]]
name = "Moyano, Alberto"
orcid = "0000-0000-0000-0000"
affiliation = "Estudio 2A"
```

La diferencia más relevante entre TOML y YAML para los flujos editoriales es el tipado explícito y sin ambigüedades: en TOML, una cadena de texto siempre está delimitada por comillas, una fecha siempre sigue el formato ISO 8601 sin delimitadores, y los booleanos se expresan exclusivamente como `true` o `false`. Esta predictibilidad reduce la probabilidad de errores de interpretación en la cadena de procesamiento.

### Markdown front matter

El *front matter* de Markdown —convencionalmente expresado en YAML y delimitado por líneas de tres guiones— es la implementación del paradigma clave=valor más directamente relevante para los flujos editoriales que utilizan Pandoc como motor de conversión. Merece un análisis específico porque opera en la intersección entre el documento de autor y el sistema de producción.

```markdown
---
title: "El paradigma clave=valor en los lenguajes de marcas"
subtitle: "Historia, modelos e implementaciones"
author:
  - name: "Moyano, Alberto"
    orcid: "0000-0000-0000-0000"
    email: "alberto@estudio2a.com"
    affiliation: "Estudio 2A"
    corresponding: true
abstract: |
  El paradigma clave=valor constituye la infraestructura
  invisible de los flujos editoriales científicos modernos.
keywords:
  - lenguajes de marcas
  - metadatos
  - publicación científica
bibliography: referencias.bib
csl: vancouver.csl
---
```

La función del front matter en un flujo editorial maduro va más allá de la simple descripción del documento: es el punto de entrada de metadatos que alimentan simultáneamente la generación del PDF, el HTML, el XML-JATS y cualquier otro formato de salida. Cualquier error en la estructuración de este encabezado se propaga a todos los formatos generados, lo que lo convierte en un componente crítico de la cadena de producción.

### JSON

JSON (*JavaScript Object Notation*) implementa el paradigma clave=valor como su estructura de datos fundamental [10]. Su presencia en los flujos editoriales científicos es predominantemente en el nivel de las APIs y los sistemas de intercambio de metadatos: Crossref, DataCite, ORCID y la mayoría de los indexadores internacionales exponen y consumen metadatos en formato JSON.

```json
{
  "title": "El paradigma clave=valor en los lenguajes de marcas",
  "author": [
    {
      "family": "Moyano",
      "given": "Alberto",
      "ORCID": "https://orcid.org/0000-0000-0000-0000",
      "affiliation": [{"name": "Estudio 2A"}]
    }
  ],
  "DOI": "10.xxxx/xxxxx",
  "type": "journal-article",
  "language": "es",
  "issued": {"date-parts": [[2024, 6, 1]]}
}
```

Para el editor científico, JSON es raramente un formato de trabajo directo: no está diseñado para la edición manual y su legibilidad es inferior a la de YAML o BibLaTeX. Su importancia está en que es el idioma en que los sistemas externos —los indexadores, los sistemas de registro de DOI, las plataformas de gestión de identidad de autor— leen y devuelven información. Comprender la estructura JSON de los metadatos es necesario para diagnosticar problemas de interoperabilidad entre el sistema editorial y los servicios externos.

### Síntesis comparativa

La tabla siguiente resume las características más relevantes de cada implementación desde la perspectiva de los flujos editoriales:

| Formato | Ámbito principal | Legibilidad humana | Tipado | Validación formal | Soporte Unicode | Uso en flujo editorial |
|---|---|---|---|---|---|---|
| BibTeX | Referencias bibliográficas | Alta | Implícito | Parcial | Limitado | Amplio (TeX/LaTeX) |
| BibLaTeX | Referencias bibliográficas | Alta | Implícito | Parcial | Completo | Creciente (LaTeX moderno) |
| LaTeX/keyval | Configuración de paquetes | Media | Implícito | Por paquete | Completo | Especializado |
| XML/JATS | Documentos estructurados | Media | Explícito (esquema) | Completo | Completo | Indexadores internacionales |
| YAML | Metadatos y configuración | Muy alta | Implícito | Opcional | Completo | Pandoc, generadores estáticos |
| TOML | Configuración | Alta | Explícito | Opcional | Completo | Hugo, herramientas modernas |
| Markdown front matter | Metadatos de documento | Muy alta | Implícito (YAML) | Opcional | Completo | Flujos con Pandoc |
| JSON | Intercambio entre sistemas | Baja | Implícito | Opcional (JSON Schema) | Completo | APIs, indexadores |

## 5. El paradigma clave=valor en la cadena de producción editorial científica

### La cadena de producción como sistema de transformaciones

Una cadena de producción editorial científica puede describirse, desde la perspectiva que nos ocupa, como una secuencia de transformaciones sobre conjuntos de pares clave=valor. El artículo comienza su trayectoria como un documento de autor —con metadatos implícitos o mínimamente estructurados— y debe llegar a los sistemas de los indexadores como un registro exhaustivamente estructurado, validado y compatible con múltiples esquemas simultáneos. Entre estos dos extremos, los metadatos son capturados, normalizados, enriquecidos, transformados y exportados en distintos formatos por distintos actores del proceso.

La calidad del resultado final depende, en medida determinante, de dos factores: la completitud y la corrección de los metadatos en cada etapa, y la coherencia de las transformaciones que los llevan de un formato a otro. Ambos factores están directamente relacionados con la comprensión y la correcta implementación del paradigma clave=valor en cada punto de la cadena.

### Dublin Core: el mínimo común denominador

Dublin Core es el vocabulario de metadatos de menor granularidad que ha alcanzado adopción generalizada en el ecosistema de la publicación científica [11]. Desarrollado originalmente en 1995 en un taller celebrado en Dublin, Ohio, define quince elementos básicos para la descripción de recursos digitales: `title`, `creator`, `subject`, `description`, `publisher`, `contributor`, `date`, `type`, `format`, `identifier`, `source`, `language`, `relation`, `coverage` y `rights`.

Su función en los flujos editoriales contemporáneos no es la de un formato de trabajo sino la de un denominador común que garantiza la interoperabilidad mínima entre sistemas heterogéneos. El protocolo OAI-PMH (*Open Archives Initiative Protocol for Metadata Harvesting*), utilizado por repositorios institucionales y sistemas de agregación de contenido científico, utiliza Dublin Core como esquema de metadatos obligatorio [12]. Esto significa que cualquier revista que desee participar en redes de diseminación basadas en OAI-PMH debe ser capaz de expresar sus metadatos en términos de los quince elementos Dublin Core, independientemente del formato interno que utilice para la gestión editorial.

Para los flujos editoriales, Dublin Core opera como una capa de abstracción: los quince elementos son suficientemente genéricos como para recibir los metadatos de cualquier tipo de recurso, pero esa misma generalidad los hace insuficientes para expresar la especificidad de un artículo científico con múltiples autores, afiliaciones diferenciadas, financiamiento declarado y datos de revisión por pares. La transición desde Dublin Core hacia esquemas más específicos como JATS es, en este sentido, una transición desde la interoperabilidad mínima hacia la descripción exhaustiva.

### Crossref y el registro del DOI

El registro de un DOI (*Digital Object Identifier*) ante Crossref es, para la mayoría de las revistas científicas, el primer punto de contacto formal entre los metadatos del artículo y un sistema externo con capacidad de validación y rechazo. Crossref acepta los metadatos en formato XML con su propio esquema —el Crossref Metadata Schema— y en formato JSON a través de su API REST [13].

El esquema de Crossref es, en términos del paradigma que nos ocupa, un contrato clave=valor con obligaciones asimétricas: algunos campos son obligatorios para el registro del DOI, otros son opcionales pero influyen en la calidad del perfil del artículo en los sistemas de métricas y citación, y otros son recomendados por la comunidad aunque no verificados automáticamente. Los campos obligatorios mínimos son el título, al menos un autor con apellido, el nombre de la revista, el ISSN, el año de publicación y el DOI solicitado.

La calidad del registro Crossref tiene consecuencias que van más allá de la asignación del identificador. Crossref alimenta los sistemas de citación de Web of Science, Scopus y Google Scholar, y es la fuente de metadatos que utilizan los gestores de referencias para importar automáticamente los datos bibliográficos. Un registro Crossref incompleto o mal formado genera referencias incorrectas en los trabajos que citan al artículo, lo que compromete tanto la atribución de la autoría como el cómputo de métricas de impacto.

### ORCID y la identificación de la autoría

El sistema ORCID (*Open Researcher and Contributor ID*) introduce en los flujos editoriales una clave de identificación persistente para las personas: el identificador ORCID, expresado como una URI del tipo `https://orcid.org/0000-0000-0000-0000` [14]. Su integración en los metadatos del artículo resuelve un problema estructural del paradigma clave=valor aplicado a la autoría: el nombre del autor como clave no es unívoco. Distintos autores pueden compartir el mismo nombre, y el mismo autor puede firmar sus trabajos de formas diferentes a lo largo de su trayectoria. El identificador ORCID convierte un valor potencialmente ambiguo —el nombre— en una clave unívoca y persistente.

La integración de ORCID en los flujos editoriales implica que el sistema de gestión debe ser capaz de verificar que el identificador declarado corresponde efectivamente al autor que se está registrando. Esta verificación —que puede realizarse consultando la API pública de ORCID— detecta lo que puede denominarse concurrencia de identificadores: la asignación del mismo ORCID a dos autores distintos en el mismo artículo, o la reutilización de un ORCID de un artículo anterior para un autor diferente. Un sistema de producción editorial robusto implementa esta verificación como parte del flujo de validación de metadatos.

### SciELO, Redalyc y los requisitos de los indexadores latinoamericanos

Los dos principales indexadores latinoamericanos —SciELO y Redalyc— tienen requisitos técnicos específicos sobre la estructura de los metadatos que las revistas deben suministrar, y ambos utilizan el paradigma clave=valor como base de esos requisitos, aunque con vocabularios y restricciones propias.

SciELO utiliza su propio perfil de aplicación de JATS, denominado SciELO PS (*Publishing Schema*), que extiende el estándar base con elementos y atributos específicos para el contexto latinoamericano [15]. Entre las extensiones más relevantes están el soporte para artículos en múltiples idiomas simultáneos —con elementos `<trans-title-group>` y `<trans-abstract>` para cada idioma adicional— y la obligatoriedad de incluir el texto completo del artículo en el archivo XML, no solo los metadatos. Esta última exigencia distingue a SciELO de otros sistemas que aceptan metadatos separados del contenido: en SciELO, el archivo JATS es el artículo completo, estructurado y marcado, lo que representa el nivel más exigente de implementación del paradigma en el contexto editorial.

Redalyc, por su parte, ha desarrollado su propia infraestructura de producción —Marcalyc— orientada a apoyar a las revistas en la generación de archivos XML compatibles con sus requisitos [16]. La propuesta de Redalyc introduce una distinción relevante para los flujos editoriales latinoamericanos: el objetivo no es solo que las revistas produzcan XML correcto, sino que lo produzcan sin transferir los costos técnicos de esa producción a las instituciones editoras. Esta distinción conecta directamente con el problema cultural y profesional que subyace al desarrollo de herramientas de producción editorial en la región.

### JATS4R y la normalización de las prácticas de marcado

JATS4R (*JATS for Reuse*) es una iniciativa de la comunidad que produce recomendaciones sobre cómo usar el estándar JATS de manera que maximice la reutilización de los datos por parte de sistemas automáticos [17]. Sus recomendaciones son específicas: indican, para cada elemento y atributo del estándar, cuáles valores son preferidos, cuáles son aceptables y cuáles deben evitarse.

Desde la perspectiva del paradigma clave=valor, JATS4R opera como un nivel adicional de constricción sobre el contrato que JATS establece. Si JATS define las claves válidas y los tipos de valor admisibles, JATS4R precisa cuáles de esos valores producen documentos óptimamente procesables por los sistemas que consumen el XML. Un ejemplo concreto: JATS admite expresar el tipo de referencia bibliográfica mediante el atributo `publication-type` con un valor de texto libre; JATS4R recomienda usar un vocabulario controlado específico (`journal`, `book`, `data`, `software`, etc.) para garantizar que los sistemas de gestión de referencias puedan clasificar correctamente cada cita.

### gbpublisher como implementación concreta

gbpublisher aborda el problema que las secciones anteriores describen desde un ángulo específico: el de la brecha entre las exigencias técnicas de los indexadores internacionales y las competencias reales de los equipos editoriales de las revistas científicas latinoamericanas. Esta brecha no es fundamentalmente técnica sino cultural y profesional: el campo editorial nunca incorporó al programador como actor central de la cadena de producción, y los editores científicos —que poseen las competencias disciplinarias necesarias para producir publicaciones de calidad— carecen en general de formación en XML, JATS o en los lenguajes de marcas que los indexadores exigen.

La respuesta arquitectónica de gbpublisher a este problema es la separación entre el nivel de interacción —donde opera el editor con sus competencias disciplinarias— y el nivel de generación de formatos —donde opera la herramienta con sus competencias técnicas. Esta separación se implementa mediante una base de datos MySQL relacional como repositorio canónico de metadatos, y formularios de ingreso como interfaz exclusiva de interacción con el operador.

En términos del paradigma que nos ocupa, la base de datos de gbpublisher es una representación interna del conjunto de pares clave=valor que describe cada artículo. Cada campo de la base de datos corresponde a una clave del sistema; el valor ingresado por el operador a través del formulario es el dato que ese campo almacena. La generación de los distintos formatos de salida —HTML, JATS para SciELO PS, JATS para Redalyc, JATS para JATS4R— consiste en transformaciones que mapean las claves internas del sistema a los vocabularios de cada esquema de destino.

Este diseño tiene una consecuencia operativa fundamental: el operador ingresa cada dato una sola vez, en el formulario de la herramienta, con independencia de cuántos formatos de salida deban generarse. La proliferación de formatos —que en un flujo manual implicaría mantener múltiples versiones del mismo artículo en distintos esquemas— queda reducida a un problema de transformación que gbpublisher resuelve automáticamente. El operador no necesita conocer la diferencia entre un atributo JATS para SciELO y uno para JATS4R; la herramienta aplica las restricciones de cada esquema durante la generación.

El sistema de validación de gbpublisher opera en dos niveles que corresponden a los dos tipos de contrato clave=valor identificados en la sección anterior. La validación interna verifica la coherencia de los datos dentro del sistema: detecta, por ejemplo, la asignación incorrecta de un identificador ORCID a más de un autor en el mismo artículo. La validación externa contrasta los datos ingresados con las APIs de los servicios de identificación —ORCID, Crossref, ROR— para verificar que los valores declarados corresponden a registros existentes y correctos. Esta doble validación implementa, en términos operativos, el principio de que los metadatos son un contrato con sistemas externos, y que la violación de ese contrato tiene consecuencias sobre la visibilidad e indexación de los artículos.

## 6. Estado del arte

### El ecosistema actual de herramientas

El ecosistema de herramientas que implementan el paradigma clave=valor en flujos editoriales científicos puede organizarse, en el momento de redacción de este artículo, en tres capas funcionales: las herramientas de autoría y gestión de referencias, los motores de conversión y transformación, y los sistemas de validación y distribución. Estas capas no operan de forma aislada sino que están articuladas por flujos de datos en los que los metadatos atraviesan múltiples transformaciones de formato.

En la capa de autoría y gestión de referencias, los gestores bibliográficos de uso más extendido en la comunidad académica hispanohablante son Zotero y Mendeley. Ambos exportan en formato BibTeX y BibLaTeX, pero también en formatos más modernos como CSL-JSON —el formato nativo del *Citation Style Language*— y RIS. Zotero ha adoptado CSL-JSON como su formato interno de representación, lo que refleja una tendencia más amplia: la migración desde los formatos bibliográficos ligados a LaTeX hacia formatos de intercambio de propósito general basados en JSON [18]. JabRef, el gestor de referencias de código abierto orientado específicamente a usuarios de LaTeX y BibLaTeX, mantiene soporte completo para el modelo de datos extendido de BibLaTeX y permite la integración con ORCID y con bases de datos bibliográficas como CrossRef y PubMed mediante sus APIs.

En la capa de conversión y transformación, Pandoc ocupa una posición central e irreemplazable. Su capacidad para leer metadatos desde el front matter YAML de un documento Markdown y utilizarlos para poblar plantillas de salida en múltiples formatos —incluyendo JATS, HTML, LaTeX y PDF— lo convierte en el motor de conversión de referencia para los flujos editoriales que trabajan con texto plano como formato de autor [19]. La versión actual de Pandoc implementa el esquema de metadatos CSL para la gestión de citas y referencias, lo que garantiza la compatibilidad con los principales gestores bibliográficos y con el repositorio de estilos CSL, que contiene en la actualidad más de diez mil estilos de citación validados para distintas disciplinas e instituciones.

Las hojas de estilo XSLT desarrolladas por NLM y posteriormente por NCBI para la transformación de documentos JATS constituyen otro componente central del ecosistema. Estas hojas permiten generar HTML de presentación, PDF mediante XSL-FO y otros formatos de salida a partir de un archivo JATS canónico, implementando en la práctica el principio de fuente única que subyace al diseño de los flujos editoriales modernos. Su uso está extendido en los sistemas de publicación de PubMed Central y en las plataformas de SciELO.

### El estándar CSL y la portabilidad de los estilos de citación

El *Citation Style Language* (CSL) merece atención específica porque representa la solución más exitosa al problema de la portabilidad de los estilos de citación entre sistemas [20]. CSL define los estilos de citación mediante archivos XML que especifican, en términos de pares clave=valor, las reglas de formateo para cada tipo de referencia y cada posición de la cita —en el texto y en la lista de referencias.

La relevancia de CSL para los flujos editoriales latinoamericanos es creciente. El repositorio oficial de estilos CSL incluye implementaciones de los principales estilos utilizados en la región —Vancouver, APA, ISO 690— y permite a cualquier editor crear o adaptar un estilo sin necesidad de modificar el código del procesador. Esta separación entre la lógica de procesamiento y la definición del estilo es, en términos del paradigma que nos ocupa, una aplicación del principio de independencia entre claves y valores: el procesador conoce las claves (autor, título, año, volumen, etc.) y el estilo define los valores de presentación (orden, puntuación, formato tipográfico) para cada combinación de clave y contexto.

La adopción de CSL como formato de definición de estilos está consolidada en Zotero, Mendeley, JabRef, Pandoc y en los principales sistemas de gestión editorial de código abierto. En el contexto de BibLaTeX, la situación es diferente: los estilos de citación se definen mediante el propio lenguaje de macros de LaTeX, lo que ofrece mayor flexibilidad tipográfica pero menor portabilidad hacia sistemas no basados en LaTeX.

### Tensiones entre estándares: el caso de los metadatos de autoría

Una de las tensiones más visibles en el ecosistema actual es la falta de uniformidad en la representación de los metadatos de autoría entre los distintos estándares y sistemas. El problema no es de vocabulario —todas las implementaciones tienen una clave equivalente a `author`— sino de granularidad y estructura del valor.

BibTeX representa la autoría como una cadena de texto con separadores convencionales. BibLaTeX la descompone en componentes pero mantiene el campo como unidad única. JATS la expresa mediante elementos XML anidados con atributos de clasificación. CSL-JSON la estructura como un array de objetos con campos `family`, `given`, `dropping-particle` y `non-dropping-particle`. ORCID la gestiona como un registro independiente con su propio modelo de datos. Crossref la recibe en su propio esquema XML con convenciones específicas para nombres secuenciados y nombres corporativos.

Esta heterogeneidad tiene consecuencias directas para los flujos editoriales: cada transformación entre formatos es una oportunidad para la pérdida o deformación de información. Un apellido compuesto que BibLaTeX representa correctamente puede perder su partícula al ser convertido a CSL-JSON por un gestor bibliográfico que no implementa el mapeo completo. Un nombre corporativo que JATS expresa mediante el elemento `<institution-wrap>` puede colapsarse en una cadena de texto plano al ser exportado a BibTeX. La gestión correcta de estas transformaciones requiere que el sistema editorial conozca no solo el vocabulario de cada formato sino las convenciones específicas de cada implementación.

### La presión de los indexadores sobre los flujos editoriales

Los indexadores internacionales —Web of Science, Scopus, PubMed, SciELO, Redalyc— ejercen sobre las revistas científicas una presión técnica creciente que se manifiesta en forma de requisitos cada vez más precisos sobre la estructura y la completitud de los metadatos. Esta presión tiene una lógica institucional clara: cuanto más ricos y correctamente estructurados sean los metadatos que los indexadores reciben, más eficientes son sus sistemas de procesamiento, mayor es la calidad de sus índices y más valiosos resultan sus servicios para la comunidad científica.

Para las revistas latinoamericanas de tamaño pequeño o mediano —que representan la gran mayoría de las revistas de la región— esta presión genera una tensión que puede describirse con precisión en términos del paradigma clave=valor: los indexadores exigen contratos con un número creciente de claves obligatorias y restricciones cada vez más estrictas sobre los valores admisibles, mientras que los equipos editoriales disponen de recursos limitados para cumplir esas exigencias de forma sistemática y sostenida.

La respuesta histórica de muchas revistas a esta tensión fue la tercerización de la producción XML a empresas especializadas o la adopción de plataformas de gestión editorial que incluyen la generación de metadatos como servicio. Ambas estrategias resuelven el problema técnico pero a un costo que no es solo económico: implican la externalización del control sobre un componente crítico del proceso editorial, con las dependencias y vulnerabilidades que eso conlleva.

### El rol de los formatos de texto plano en los flujos modernos

Una tendencia significativa en el ecosistema actual es la consolidación de los formatos de texto plano —Markdown, AsciiDoc, reStructuredText— como formatos de autor en flujos editoriales científicos que antes utilizaban exclusivamente procesadores de texto como Microsoft Word. Esta tendencia está impulsada por varias razones convergentes: la compatibilidad de los formatos de texto plano con los sistemas de control de versiones, la separación nítida entre contenido y presentación, la facilidad de procesamiento automático y la independencia respecto de plataformas comerciales.

Para el paradigma clave=valor, la relevancia de esta tendencia está en que los formatos de texto plano con front matter YAML integran la captura de metadatos en el propio documento de autor, en lugar de gestionarlos en sistemas separados. Esto reduce la probabilidad de divergencia entre los metadatos del documento y los metadatos del sistema de gestión, pero exige que el autor —o el editor que prepara el documento— comprenda la estructura del front matter y sea capaz de completarlo correctamente.

Esta exigencia conecta con un problema más amplio que el presente artículo ha identificado desde su introducción: la comprensión del paradigma clave=valor no puede limitarse a los técnicos que diseñan los sistemas. Debe alcanzar, en alguna medida, a todos los actores del flujo editorial, incluyendo los autores. La adopción de formatos de texto plano en flujos editoriales científicos es, en este sentido, tanto una oportunidad para mejorar la calidad estructural de los documentos como un desafío para la formación de los actores del proceso.

### Iniciativas de armonización y metadatos enriquecidos

El ecosistema actual muestra también iniciativas activas de armonización entre estándares que merecen atención. La iniciativa *Metadata 2020*, impulsada por Crossref y otras organizaciones del ecosistema de la publicación científica, promueve la adopción de prácticas de metadatos enriquecidos que van más allá de los mínimos obligatorios de cada sistema [21]. Sus recomendaciones incluyen la declaración sistemática de los identificadores ORCID de todos los autores, la inclusión de los identificadores ROR de las instituciones de afiliación, la declaración explícita de las licencias de acceso abierto y la estructuración de las listas de referencias de forma que permita el enlace automático entre documentos.

Schema.org, el vocabulario de propiedades semánticas promovido por Google, Bing y otros motores de búsqueda, ha desarrollado extensiones específicas para la descripción de artículos científicos que permiten la indexación semántica de los metadatos en los motores de búsqueda de propósito general [22]. La adopción de Schema.org en las páginas HTML de las revistas científicas —mediante marcado JSON-LD incrustado en el encabezado de cada página de artículo— representa una forma de ampliar el alcance de los metadatos más allá del ecosistema especializado de la publicación científica hacia el ecosistema general de la web.

## 7. Perspectivas y tendencias futuras

### La convergencia hacia identificadores persistentes

La tendencia más consistente y con mayor proyección en el ecosistema de la publicación científica es la adopción sistemática de identificadores persistentes —PID, *Persistent Identifiers*— para todos los actores y objetos del proceso editorial. DOI para los artículos y conjuntos de datos, ORCID para los investigadores, ROR para las instituciones, ISSN para las revistas, RRid para los recursos de investigación: cada uno de estos sistemas es, en términos del paradigma que nos ocupa, la formalización de una clave con garantía de persistencia y univocidad global.

La convergencia hacia identificadores persistentes tiene una consecuencia estructural sobre los flujos editoriales: desplaza progresivamente la carga de la identificación desde el valor —el nombre del autor, el nombre de la institución, el título de la revista— hacia la clave —el identificador que señala unívocamente al objeto referenciado. En un sistema maduro de identificadores persistentes, el nombre del autor en los metadatos del artículo no es la fuente de verdad sobre la identidad del autor: es el ORCID el que cumple esa función, y el nombre es un valor derivado que el sistema obtiene consultando el registro ORCID en el momento en que lo necesita.

Esta reconfiguración del paradigma —de un sistema donde el valor textual es el dato primario a uno donde el identificador es la clave y el valor textual es derivado— tiene implicaciones profundas para el diseño de los flujos editoriales. Los sistemas de producción que no estén preparados para gestionar identificadores persistentes como claves primarias quedarán progresivamente desconectados de un ecosistema que los da por supuestos. La integración de ORCID, ROR y Crossref en los flujos de validación de metadatos no es, en este horizonte, una característica avanzada sino un requisito de base.

### Los datos enlazados y la web semántica

El paradigma de los datos enlazados (*Linked Data*) representa la extensión más ambiciosa del modelo clave=valor hacia un sistema de representación del conocimiento de alcance global [23]. En el modelo de datos enlazados, cada clave es una URI que identifica unívocamente una propiedad en el espacio global de la web, y cada valor puede ser a su vez una URI que identifica otro recurso. La relación entre los metadatos de un artículo y el conjunto global del conocimiento científico queda así expresada no como una colección de cadenas de texto sino como un grafo de relaciones entre entidades identificadas de forma persistente.

El lenguaje RDF (*Resource Description Framework*), base técnica de los datos enlazados, puede verse como una generalización del paradigma clave=valor: cada afirmación sobre un recurso es una tripleta sujeto-predicado-objeto, donde el predicado es la clave y el objeto es el valor. Los vocabularios Dublin Core, Schema.org y BIBO (*Bibliographic Ontology*) definen predicados específicos para la descripción de recursos bibliográficos en el espacio RDF, lo que permite que los metadatos de un artículo científico sean consumidos no solo por los sistemas especializados de los indexadores sino por cualquier sistema capaz de procesar RDF.

Para los flujos editoriales científicos, la adopción de datos enlazados es un horizonte de mediano y largo plazo cuya implementación práctica enfrenta obstáculos significativos. El principal es la curva de adopción: los vocabularios RDF requieren una comprensión conceptual del modelo de datos enlazados que va más allá de las competencias actuales de la mayoría de los equipos editoriales. El segundo es la fragmentación: existen múltiples vocabularios para la descripción de recursos bibliográficos en RDF, con superposiciones y contradicciones que dificultan la elección del vocabulario apropiado para cada contexto.

Sin embargo, la presión en esta dirección es real y creciente. Los principales motores de búsqueda utilizan ya datos enlazados para enriquecer sus resultados con información estructurada sobre artículos, autores e instituciones. Los indexadores más avanzados están desarrollando capacidades para consumir y producir metadatos en formatos RDF. Y las iniciativas de ciencia abierta —que promueven no solo el acceso libre a los artículos sino la reutilización de los datos de investigación— requieren formas de descripción de recursos que el modelo clave=valor clásico, sin la dimensión semántica de los datos enlazados, no puede satisfacer plenamente.

### La presión creciente de los indexadores y sus consecuencias para las revistas latinoamericanas

La evolución de los requisitos técnicos de los indexadores en los últimos años describe una trayectoria clara: más campos obligatorios, restricciones más estrictas sobre los valores admisibles y plazos más cortos para la adopción de nuevas versiones de los estándares. Esta trayectoria no muestra señales de moderación, y su proyección hacia el futuro inmediato indica que las exigencias seguirán creciendo en complejidad y precisión.

Para las revistas científicas latinoamericanas, esta trayectoria plantea un desafío estructural que no puede resolverse únicamente con capacitación técnica de los equipos editoriales. El problema de fondo es que el modelo de producción editorial predominante en la región —basado en editores con competencias disciplinarias pero sin formación técnica en XML o en los estándares de los indexadores— no es compatible con las exigencias crecientes de un ecosistema que da por supuesto un nivel de sofisticación técnica que la mayoría de los equipos editoriales no posee ni está en condiciones de adquirir en el corto plazo.

La respuesta sostenible a este desafío no es elevar el nivel de exigencia técnica de los editores científicos —una estrategia que confunde la competencia disciplinaria con la competencia técnica y subestima la especificidad de ambas— sino diseñar herramientas que absorban la complejidad técnica y la vuelvan invisible para el operador. Este principio de diseño, que puede formularse como la separación entre la interfaz de trabajo del editor y la arquitectura técnica del sistema de producción, es el que orienta el desarrollo de las herramientas de producción editorial de nueva generación para el contexto latinoamericano.

### La inteligencia artificial como agente en los flujos editoriales

La incorporación de sistemas de procesamiento de lenguaje natural e inteligencia artificial en los flujos editoriales científicos es una realidad emergente con implicaciones directas para el paradigma clave=valor. En su aplicación más directa, estos sistemas pueden asistir en la extracción automática de metadatos desde documentos no estructurados: identificar el título, los autores, las afiliaciones y las referencias de un artículo recibido en formato PDF y generar automáticamente el conjunto de pares clave=valor correspondiente para poblar el sistema de gestión editorial.

Esta capacidad de extracción automática no elimina la necesidad de validación humana —los sistemas de extracción cometen errores, especialmente con nombres propios, afiliaciones complejas y referencias mal formateadas— pero puede reducir significativamente la carga de trabajo de ingreso manual de datos, que es uno de los cuellos de botella más frecuentes en los flujos editoriales de revistas con recursos limitados.

Una segunda aplicación emergente es la validación asistida de metadatos: sistemas que verifican la coherencia interna de un conjunto de pares clave=valor, identifican valores que probablemente estén mal formados o incompletos, y sugieren correcciones basadas en el contexto del artículo y en los registros de los sistemas de identificación externos. Esta función de validación asistida no reemplaza la validación formal contra los esquemas de los indexadores, pero puede anticipar errores antes de que el artículo llegue a la etapa de generación de XML, reduciendo los ciclos de corrección.

Es importante, sin embargo, situar estas posibilidades en sus límites reales. Los sistemas de inteligencia artificial actuales no tienen acceso fiable a las especificaciones actualizadas de los estándares de los indexadores, no pueden verificar la existencia de un identificador ORCID o ROR en tiempo real, y no pueden garantizar la conformidad de un archivo XML con un esquema específico. Su función en los flujos editoriales es de asistencia y de primera aproximación, no de validación definitiva.

### La sostenibilidad del modelo de producción editorial abierto

Una tendencia de fondo que atraviesa todas las anteriores es la consolidación del modelo de publicación científica en acceso abierto como el marco dominante en el que operarán los flujos editoriales del futuro próximo. Este modelo tiene consecuencias específicas para el paradigma clave=valor: la declaración explícita de la licencia de uso, la identificación de las fuentes de financiamiento y la disponibilidad de los datos de investigación asociados al artículo son campos que los sistemas de acceso abierto exigen y que muchos flujos editoriales actuales no gestionan de forma estructurada.

La declaración de la licencia Creative Commons, por ejemplo, no es en los sistemas modernos una nota al pie del artículo sino un par clave=valor en los metadatos: `license-type="open-access"` y `href="https://creativecommons.org/licenses/by/4.0/"` en la nomenclatura JATS. La declaración del financiamiento sigue el mismo principio: no es un párrafo de agradecimientos sino un conjunto estructurado de pares que identifican la agencia financiadora mediante su identificador en Crossref Funder Registry, el número de contrato y el tipo de financiamiento.

La adopción sistemática de estas prácticas —que los indexadores y las plataformas de ciencia abierta están comenzando a exigir— implica una expansión del contrato clave=valor que los flujos editoriales deben satisfacer. Los sistemas de producción que no anticipen esta expansión y la incorporen en su arquitectura desde el diseño tendrán que afrontar costosas adaptaciones en el momento en que la exigencia se vuelva obligatoria.

### El horizonte de la interoperabilidad total

El horizonte que dibujan las tendencias anteriores —identificadores persistentes generalizados, datos enlazados, inteligencia artificial asistiva, acceso abierto universal— puede describirse como el de la interoperabilidad total: un ecosistema en el que los metadatos de cualquier artículo científico son accesibles, verificables y reutilizables por cualquier sistema autorizado, en el formato que ese sistema requiera, sin fricción de conversión ni pérdida de información.

Este horizonte es, por supuesto, una aproximación asintótica: la heterogeneidad de los sistemas, la diversidad de los contextos institucionales y la velocidad desigual de adopción de los estándares garantizan que la fricción nunca será cero. Pero la dirección del movimiento es clara, y las decisiones de diseño que los desarrolladores de herramientas editoriales tomen hoy determinarán en qué medida las revistas que las usen podrán participar en ese ecosistema futuro.

Para el paradigma clave=valor, este horizonte implica una exigencia creciente de precisión semántica: no bastará con que los metadatos estén presentes y bien formados en términos sintácticos; deberán ser semánticamente correctos, es decir, deberán expresar con exactitud las relaciones que describen en el espacio conceptual compartido por todos los sistemas del ecosistema. Esta exigencia de precisión semántica es, en última instancia, la que distingue a un flujo editorial maduro de uno que simplemente cumple con los mínimos formales de los indexadores.

## 8. Conclusiones

El recorrido que este artículo ha trazado —desde los archivos de catalogación de la Biblioteca del Congreso y los primeros sistemas de composición tipográfica digital hasta los datos enlazados y los identificadores persistentes globales— permite afirmar que el paradigma clave=valor no es una convención técnica entre otras sino el principio organizador fundamental de la información en los flujos editoriales científicos modernos. Su persistencia a través de décadas de transformación tecnológica, su capacidad para manifestarse en sintaxis radicalmente distintas manteniendo invariante su lógica de funcionamiento, y su presencia simultánea en todos los niveles de la cadena de producción —desde el archivo de referencias del autor hasta las APIs de los indexadores internacionales— lo caracterizan como una estructura de conocimiento con solidez conceptual propia, independiente de cualquier implementación particular.

El análisis comparado de las implementaciones reveló que la diversidad de formatos no es redundancia sino especialización funcional. BibTeX y BibLaTeX resuelven el problema de la gestión bibliográfica en entornos de composición tipográfica con exigencias de precisión tipográfica que ningún otro formato satisface con la misma madurez. YAML y el front matter de Markdown resuelven el problema de la legibilidad y la integración de metadatos en el documento de autor. XML y JATS resuelven el problema de la validación formal y la interoperabilidad con los sistemas de los indexadores. JSON resuelve el problema del intercambio entre sistemas a través de APIs. Ninguno de estos formatos es universalmente superior; cada uno es óptimo para el problema que fue diseñado para resolver. La competencia del editor técnico no consiste en dominar todos estos formatos en profundidad sino en comprender sus funciones, sus límites y las transformaciones que los articulan en la cadena de producción.

El análisis de la cadena de producción editorial científica confirmó que los problemas de calidad de metadatos que afectan a las revistas latinoamericanas no son consecuencia de negligencia o de falta de compromiso de los equipos editoriales, sino de una brecha estructural entre las exigencias técnicas de un ecosistema de indexación diseñado en contextos con mayor disponibilidad de recursos técnicos especializados, y las condiciones reales de producción de la mayoría de las revistas de la región. Esta brecha no puede cerrarse únicamente mediante la formación técnica de los editores científicos, porque la competencia técnica en XML, JATS y en los estándares de los indexadores es en sí misma una especialización que requiere tiempo y recursos de formación que los equipos editoriales no siempre pueden destinar.

La respuesta arquitectónica adecuada a esta brecha —y que gbpublisher implementa de forma concreta— es el diseño de herramientas que absorban la complejidad técnica del paradigma clave=valor y la vuelvan invisible para el operador, preservando simultáneamente toda su potencia para los sistemas que consumen los formatos de salida. Cuando un editor ingresa el nombre de un autor en un formulario, no está operando sobre una cadena de texto: está definiendo el valor de una clave que, a través de las transformaciones que la herramienta ejecuta automáticamente, alimentará el registro JATS del artículo, el depósito de metadatos en Crossref, la validación del identificador ORCID y el encabezado HTML de la página del artículo en la plataforma de publicación. La invisibilidad de esa cadena de transformaciones no es una limitación del sistema sino su logro central.

El estado del arte y las perspectivas futuras confirman que la dirección del ecosistema de la publicación científica es hacia una mayor exigencia de precisión semántica y de completitud de metadatos, impulsada por la consolidación de los identificadores persistentes, la expansión de los datos enlazados y la presión creciente de los indexadores sobre los flujos de producción. Para las revistas latinoamericanas, este horizonte plantea tanto un riesgo como una oportunidad. El riesgo es la exclusión progresiva de aquellas revistas cuyos flujos de producción no puedan adaptarse a la velocidad que el ecosistema demanda. La oportunidad es la adopción temprana de herramientas y prácticas que conviertan el cumplimiento de los estándares técnicos en un resultado natural del proceso editorial, en lugar de una carga adicional sobre equipos ya sobrecargados.

El paradigma clave=valor, en definitiva, no es un problema técnico que los editores científicos deban resolver: es la infraestructura conceptual sobre la que descansa la visibilidad, la recuperabilidad y la interoperabilidad de la producción científica en el ecosistema global de la información. Comprender sus fundamentos, reconocer sus implementaciones y entender las transformaciones que articulan sus distintas manifestaciones es, para el editor científico contemporáneo, una forma de conocimiento tan necesaria como el dominio de las convenciones de su disciplina. No porque el editor deba escribir XML o configurar procesadores BibLaTeX, sino porque sin esa comprensión no puede evaluar críticamente las herramientas que usa, diagnosticar los problemas que encuentra ni participar con autonomía en las decisiones sobre los flujos de producción de su revista.

## Referencias

[1] Library of Congress. *MARC 21 Format for Bibliographic Data*. Washington: Library of Congress, 1999.

[2] International Organization for Standardization. *ISO 8879:1986. Information processing — Text and office systems — Standard Generalized Markup Language (SGML)*. Ginebra: ISO, 1986.

[3] Raymond ES. *The Art of Unix Programming*. Boston: Addison-Wesley, 2003.

[4] Patashnik O. *BibTeXing* [documento técnico]. Stanford: Stanford University, 1988.

[5] World Wide Web Consortium. *Extensible Markup Language (XML) 1.0*. W3C Recommendation, 10 de febrero de 1998.

[6] Lehman P, Kime P, Boruvka A, Wright J. *The biblatex package: Sophisticated Bibliographies in LaTeX*. CTAN, 2023.

[7] Carlisle D, Rahtz S. *The keyval package*. CTAN, 1999.

[8] Ben-Kiki O, Evans C, döt Net I. *YAML Ain't Markup Language (YAML) Version 1.2*. yaml.org, 2021.

[9] Preston-Werner T. *TOML: Tom's Obvious, Minimal Language*. Version 1.0.0. toml.io, 2021.

[10] Ecma International. *ECMA-404: The JSON Data Interchange Syntax*. 2ª ed. Ginebra: Ecma International, 2017.


[11] Dublin Core Metadata Initiative. *Dublin Core Metadata Element Set, Version 1.1*. DCMI, 2012.

[12] Open Archives Initiative. *Protocol for Metadata Harvesting. Version 2.0*. OAI, 2002.

[13] Crossref. *Crossref Metadata Schema Documentation*. Crossref, 2023.

[14] ORCID. *ORCID API v3.0 Documentation*. ORCID, 2023.

[15] SciELO. *SciELO Publishing Schema 1.9*. São Paulo: SciELO, 2023.

[16] Redalyc. *Marcalyc: metodología para la generación de XML-JATS*. Toluca: Universidad Autónoma del Estado de México, 2022.

[17] JATS4R. *JATS for Reuse Recommendations, Version 1.3*. JATS4R, 2022.

[18] Zotero. *Zotero Documentation: CSL*. Roy Rosenzweig Center for History and New Media, George Mason University, 2023.

[19] MacFarlane J. *Pandoc: A Universal Document Converter*. Version 3.x. pandoc.org, 2024.

[20] Zelle M, et al. *Citation Style Language 1.0 Specification*. citationstyles.org, 2012.

[21] Crossref. *Metadata 2020: Richer, Better, More Connected Metadata*. metadata2020.org, 2023.

[22] Schema.org. *ScholarlyArticle — schema.org*. schema.org/ScholarlyArticle, 2024.

[23] Berners-Lee T, Hendler J, Lassila O. The Semantic Web. *Scientific American*. 2001;284(5):34-43.
