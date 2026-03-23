---
title: "Bases de datos en la producción editorial científica"
weight: 6
description: >
  Las bases de datos han pasado desapercibidas durante décadas en la formación de los equipos editoriales de revistas científicas. La tradición editorial —construida alrededor de documentos, estilos tipográficos y flujos de corrección— no incluía, hasta hace muy poco, reflexión alguna sobre cómo se almacenan, relacionan y recuperan los datos que sostienen ese trabajo. Hoy esa omisión ya no es sostenible. Un editor que trabaja con XML-JATS, identificadores persistentes, metadatos estructurados y flujos automatizados de producción está, necesariamente, trabajando con lógica de bases de datos, aunque no lo sepa con ese nombre.
---

Este artículo no pretende convertir a los editores en administradores de bases de datos. Su objetivo es más modesto y, en muchos sentidos, más urgente: proporcionar el vocabulario, la historia y los conceptos fundamentales que permiten comprender qué es una base de datos, cómo llegó a ser lo que es hoy, y por qué su integración en los flujos editoriales no es una novedad tecnológica sino una consecuencia lógica de la maduración del campo. Comprender estas ideas no exige formación técnica previa; sí exige disposición para ver el proceso editorial desde un ángulo nuevo.

## 1. ¿Qué es una base de datos?

Una base de datos es un conjunto organizado de información almacenada de manera que pueda ser recuperada, actualizada y relacionada eficientemente. La palabra clave es **organizado**: no cualquier colección de datos constituye una base de datos. Un archivo de Word con una lista de autores y sus correos electrónicos contiene datos, pero no es una base de datos en el sentido técnico del término. Lo que distingue a una base de datos de una simple colección es la existencia de una **estructura** explícita que define cómo los datos se almacenan y cómo se relacionan entre sí.

Esta distinción entre datos y estructura es fundamental. Los datos son los hechos concretos: el nombre de un autor, el ISSN de una revista, el año de publicación de un artículo. La estructura define cómo esos hechos se organizan: que un autor puede tener varias afiliaciones, que un artículo pertenece a exactamente un número de una revista, que un número puede contener muchos artículos. La estructura impone disciplina sobre los datos; sin ella, la información se vuelve inconsistente, redundante y difícilmente recuperable a medida que crece.

En el contexto editorial, esta distinción tiene consecuencias prácticas inmediatas. Cuando una revista mantiene los datos de sus autores en una hoja de cálculo, cada vez que el mismo autor aparece en un nuevo artículo hay que volver a ingresar su nombre, su correo, su ORCID, su afiliación. Si el autor cambia de institución, hay que localizar todas las filas donde aparece y actualizarlas manualmente. Una base de datos resuelve este problema con un concepto fundamental: la **normalización**. En lugar de repetir los datos del autor en cada artículo, los datos del autor se almacenan una sola vez en una tabla de autores, y los artículos simplemente **referencian** ese registro. Si el autor cambia de institución, se actualiza un único registro y todos los artículos que lo referencian reflejan automáticamente el cambio.

Este principio —almacenar cada hecho exactamente una vez y referenciar ese almacenamiento donde sea necesario— es la base del modelo relacional que domina la industria desde hace más de cincuenta años. Entender este principio es entender por qué las bases de datos existen y por qué importan.

## 2. Historia de las bases de datos: de los archivos planos a los sistemas modernos

### Los precursores: archivos y ficheros (décadas de 1950 y 1960)

La historia de las bases de datos comienza mucho antes de que el término existiera. En los primeros años de la computación comercial, los datos se almacenaban en **archivos planos**: secuencias de registros con estructura fija escritas en cintas magnéticas o tarjetas perforadas. Cada programa que necesitaba ciertos datos los leía directamente de su propio archivo. No había concepto de compartir datos entre aplicaciones; no había forma estándar de definir qué significaba cada campo; no había mecanismo para relacionar datos de diferentes archivos.

Este modelo funcionaba razonablemente bien cuando los sistemas eran simples y los volúmenes de datos pequeños. Pero a medida que las organizaciones acumulaban más datos y más aplicaciones, las limitaciones se volvieron insoportables. Los mismos datos se duplicaban en docenas de archivos. Las inconsistencias proliferaban: el nombre de un cliente escrito de una manera en el sistema de facturación y de otra en el sistema de inventario. Actualizar un dato requería localizar y modificar todos los archivos que lo contenían, proceso propenso a errores y omisiones. Y dado que cada archivo tenía su propio formato, escrito para un programa específico, era prácticamente imposible hacer consultas que cruzaran información de múltiples fuentes.

Hacia mediados de la década de 1960, la insatisfacción con este modelo era generalizada entre los grandes usuarios corporativos de computadoras (principalmente bancos, aerolíneas y el gobierno de Estados Unidos). La necesidad de un enfoque radicalmente diferente era obvia; lo que no era evidente era qué forma debería tomar ese enfoque.

### Los primeros sistemas de gestión de bases de datos (finales de la década de 1960)

La primera respuesta sistemática al problema fue el desarrollo de los primeros Sistemas de Gestión de Bases de Datos (SGBD), dos modelos que emergieron casi simultáneamente a finales de la década de 1960: el modelo **jerárquico** y el modelo **en red**.

El modelo jerárquico, cuya implementación más influyente fue IMS (Information Management System) de IBM, desarrollado en 1968 para el programa espacial Apollo, organizaba los datos en estructuras de árbol: cada registro tenía un único registro padre y podía tener múltiples registros hijos. Esto era intuitivo para ciertos tipos de datos (una empresa tiene departamentos, cada departamento tiene empleados), pero fallaba al intentar representar relaciones más complejas. Un empleado que perteneciera a dos departamentos, o un artículo que tuviera varios autores cada uno con varias afiliaciones, rompían la lógica de árbol.

El modelo en red (network model), formalizado por el comité CODASYL (Conference on Data Systems Languages) en 1969, intentaba resolver esta limitación permitiendo que los registros tuvieran múltiples padres. Representaba los datos como un grafo donde cualquier nodo podía conectarse con cualquier otro. Era más flexible que el modelo jerárquico, pero la complejidad de navegar ese grafo recaía completamente sobre el programador: para recuperar información, era necesario escribir código que recorriera manualmente los caminos entre los nodos, sin ningún lenguaje de consulta de alto nivel.

Estos sistemas resolvieron algunos de los problemas de los archivos planos (especialmente la duplicación de datos), pero introdujeron nuevas complejidades. El programador debía conocer en detalle la estructura física de la base de datos para escribir consultas eficientes. Cambiar la estructura de los datos implicaba reescribir los programas que los usaban. Y la falta de independencia entre la lógica de los datos y la lógica de las aplicaciones seguía siendo un obstáculo fundamental.

### La revolución relacional: Edgar Codd y el modelo matemático (1970)

En 1970, un matemático inglés que trabajaba para IBM en San José, California, publicó un artículo que cambiaría fundamentalmente la forma en que la humanidad almacena y gestiona información. Edgar Frank Codd, en su artículo "A Relational Model of Data for Large Shared Data Banks" [1], propuso un modelo radicalmente diferente, fundamentado en la teoría matemática de conjuntos y la lógica de predicados de primer orden.

La propuesta de Codd era elegante en su simplicidad: los datos debían representarse exclusivamente como **tablas** (que él llamó **relaciones** en el sentido matemático), donde cada fila representaba un hecho único y cada columna representaba un atributo. Las relaciones entre diferentes conjuntos de datos se expresaban mediante **valores compartidos** (claves foráneas), no mediante punteros físicos en memoria. Y la recuperación de datos debería hacerse mediante un lenguaje de alto nivel declarativo (que describe **qué** se quiere, no **cómo** obtenerlo) basado en el álgebra relacional.

Las implicaciones de este modelo eran revolucionarias en tres dimensiones:

**Independencia física**: El programador no necesitaba saber cómo los datos estaban físicamente almacenados en disco para consultarlos. El sistema de gestión se encargaba de encontrar la manera más eficiente de satisfacer una consulta.

**Independencia lógica**: Se podían añadir nuevas columnas a una tabla, o nuevas tablas, sin necesidad de modificar los programas existentes que usaban esa base de datos.

**Integridad declarativa**: Las reglas que los datos debían cumplir (un artículo debe tener al menos un autor; un autor no puede pertenecer a una revista que no existe en el sistema) podían expresarse como restricciones en la propia definición de la base de datos, no en cada programa que la usaba.

IBM, sorprendentemente, tardó años en implementar el modelo de Codd en un producto comercial; sus ingenieros de IMS veían la propuesta con escepticismo. Fue un equipo de investigadores de IBM (Chamberlin y Boyce) quienes en 1974 desarrollaron Structured English Query Language (SEQUEL), más tarde renombrado Structured Query Language (SQL) [2], el lenguaje que materializaría las ideas de Codd en algo practicable. Y fue una empresa externa, Relational Software Inc. (más tarde renombrada Oracle), la que llevó el primer sistema relacional comercial al mercado en 1979, un año antes que el propio IBM.

### La consolidación relacional (décadas de 1980 y 1990)

La década de 1980 vio la consolidación del modelo relacional como paradigma dominante. IBM lanzó DB2 en 1983. Oracle, Sybase, Informix e Ingres competían en el mercado corporativo. Y en 1985, ANSI estandarizó SQL, asegurando que al menos los conceptos fundamentales del lenguaje fueran portables entre sistemas.

Para el mundo académico y científico, este período es relevante por el surgimiento de dos tendencias paralelas. Por un lado, las grandes instituciones de investigación comenzaron a usar bases de datos relacionales para gestionar sus propias actividades administrativas. Por otro, emergieron los primeros sistemas orientados específicamente a la gestión de información bibliográfica: bases de datos que almacenaban no solo los metadatos de las publicaciones sino que empezaban a incorporar texto completo.

MEDLINE, la base de datos bibliográfica de la National Library of Medicine de Estados Unidos que ya mencionamos en el artículo sobre XML-JATS, ejemplifica esta transición. Lo que comenzó como un sistema de tarjetas perforadas e índices impresos se transformó progresivamente en una base de datos relacional que permitía consultas complejas sobre millones de registros bibliográficos. La lógica que haría posible JATS —estructurar el conocimiento científico de forma que sea recuperable, relacionable e interoperable— tiene raíces directas en la revolución relacional de estas décadas.

### El surgimiento de los sistemas de código abierto (finales de la década de 1990)

Un hito decisivo para la adopción masiva de bases de datos fuera del entorno corporativo fue el surgimiento de sistemas de gestión de bases de datos de código abierto en la segunda mitad de la década de 1990. MySQL (1995) y PostgreSQL (cuyas raíces académicas en la Universidad de California, Berkeley se remontan al proyecto Ingres de 1973 y a su sucesor Postgres de 1986, pero cuya versión open source se lanzó en 1996) [3] democratizaron el acceso a la tecnología relacional.

Antes de estos proyectos, implementar una base de datos requería licencias costosas de Oracle, IBM o Microsoft, inaccesibles para proyectos académicos, iniciativas sin fines de lucro o desarrolladores independientes. MySQL y PostgreSQL rompieron esa barrera: cualquiera con una computadora conectada a internet podía ahora implementar un sistema de gestión de bases de datos relacional completo sin costo alguno.

Las consecuencias para el ecosistema de publicación académica fueron directas. Open Journal Systems (OJS), la plataforma de gestión editorial de código abierto desarrollada por el Public Knowledge Project (PKP) a partir de 2001 [4], se construyó sobre MySQL. El propio SciELO construyó sus infraestructuras de indexación sobre bases de datos de código abierto. Y herramientas como gbpublisher, diseñadas específicamente para el contexto latinoamericano, utilizan bases de datos relacionales de código abierto como fundamento de su arquitectura.

Este proceso de democratización no fue solo económico. Fue también epistemológico: al hacer el código fuente de los sistemas de bases de datos disponible para su estudio y modificación, los proyectos de código abierto permitieron que comunidades de desarrolladores en todo el mundo entendieran profundamente cómo funcionaban estos sistemas, los adaptaran a sus necesidades específicas, y construyeran sobre ellos sin depender de decisiones comerciales ajenas.

## 3. Modelos de bases de datos: una taxonomía para el editor

El modelo relacional, que había sido el paradigma dominante durante décadas, comenzó a enfrentar a partir de la primera mitad de los años 2000 tipos de datos y patrones de uso para los que no había sido diseñado. La respuesta de la industria fue diversificar: surgieron nuevos modelos de bases de datos, cada uno optimizado para resolver un conjunto específico de problemas. Comprender esa diversidad —sin necesidad de dominar sus detalles técnicos— ayuda al editor a entender qué tipo de sistema está usando cuando trabaja con diferentes herramientas, y por qué cada una toma las decisiones de diseño que toma.

### El modelo relacional

Ya hemos descrito los fundamentos del modelo relacional en la sección anterior. Vale la pena resumir sus características esenciales desde la perspectiva del usuario:

Los datos se organizan en **tablas** (también llamadas relaciones). Cada tabla tiene un esquema fijo: un conjunto predefinido de columnas con tipos de datos específicos (texto, número entero, fecha, booleano). Cada fila de la tabla representa un registro único. Las relaciones entre tablas se expresan mediante **claves**: una clave primaria identifica unívocamente cada fila dentro de una tabla; una clave foránea en otra tabla referencia esa clave primaria, estableciendo así la relación.

La consulta de datos se realiza mediante **SQL** (Structured Query Language), un lenguaje declarativo que permite expresar preguntas complejas sobre los datos sin especificar cómo el sistema debe responderlas. Una consulta SQL puede combinar datos de múltiples tablas (operación llamada *join*), filtrar registros según condiciones, agrupar y agregar datos, ordenar resultados.

Las bases de datos relacionales también implementan el concepto de **transacciones** y las propiedades ACID (Atomicidad, Consistencia, Aislamiento, Durabilidad). Una transacción es un conjunto de operaciones que debe ejecutarse completamente o no ejecutarse en absoluto: si se interrumpe a mitad, el sistema garantiza que los datos vuelvan al estado anterior. Esto es crucial en contextos donde la integridad de los datos es crítica.

Para el trabajo editorial, el modelo relacional es el más apropiado en la mayoría de los casos: los datos de una revista (artículos, autores, afiliaciones, números, referencias) son naturalmente tabulares, tienen estructura predecible, y las relaciones entre ellos son exactamente el tipo de relaciones que el modelo relacional gestiona mejor. Por eso herramientas como OJS, Janeway, y gbpublisher usan bases de datos relacionales como núcleo de su almacenamiento.

Los sistemas relacionales más relevantes para el ecosistema editorial son:

**MySQL / MariaDB**: MySQL es uno de los sistemas relacionales de código abierto más utilizados en el mundo, especialmente en combinación con PHP (el lenguaje en que está escrito OJS). MariaDB es un fork comunitario de MySQL creado en 2009 tras la adquisición de MySQL por Oracle, mantenido por muchos de los desarrolladores originales. Ambos son opciones sólidas y ampliamente soportadas.

**PostgreSQL**: Sistema de código abierto considerado el más robusto y completo de los sistemas libres. Soporta tipos de datos avanzados (incluyendo JSON nativo, arrays, tipos geométricos), extensiones, y cumplimiento estricto con el estándar SQL. Es una opción frecuente para instalaciones de producción de OJS y otros sistemas editoriales de alto tráfico.

**SQLite**: A diferencia de PostgreSQL y MySQL, SQLite no es un servidor: es una biblioteca que se integra directamente en la aplicación. La base de datos completa reside en un único archivo en disco. Esto la hace ideal para aplicaciones de escritorio, herramientas de desarrollo, y sistemas embebidos donde la simplicidad de instalación y mantenimiento supera la necesidad de escalabilidad concurrente. gbpublisher utiliza MySQL como motor principal de su base de datos editorial, y SQLite en una variante cifrada para la gestión de autenticación del administrador del sistema: una separación que permite proteger las credenciales de acceso con un mayor nivel de seguridad sin complejizar la arquitectura general.

### El modelo documental

A medida que la web creció, surgió la necesidad de almacenar y recuperar datos cuya estructura no era fija ni predecible de antemano. Considérese el caso de perfiles de usuario en una red social: algunos usuarios tienen una dirección, otros no; algunos tienen un número de teléfono, otros tienen varios; algunos tienen datos de educación, otros no. Intentar representar toda esta variabilidad en un esquema relacional rígido resulta en tablas llenas de columnas vacías o en diseños extremadamente complejos.

Los sistemas de bases de datos documentales resuelven este problema almacenando los datos como **documentos** (habitualmente en formato JSON o BSON) en lugar de filas en tablas. Cada documento puede tener su propia estructura interna, diferente a la de cualquier otro documento en la misma colección. No hay un esquema fijo que todos los documentos deban cumplir.

Esta flexibilidad tiene un precio: las operaciones que en una base de datos relacional son simples y eficientes (como un *join* entre dos tablas) son más complejas en bases de datos documentales, porque los documentos no fueron diseñados para relacionarse entre sí de esa manera. Los sistemas documentales son potentes para almacenar y recuperar objetos complejos de manera individualizada, pero menos adecuados para consultas que cruzan múltiples colecciones de manera sistemática.

**MongoDB** es el sistema documental más conocido. **CouchDB** es otra alternativa relevante por su modelo de replicación y su orientación hacia aplicaciones desconectadas o con conectividad intermitente.

En el ecosistema editorial, los sistemas documentales son relevantes principalmente en el contexto de APIs y servicios que exponen datos de artículos en formato JSON: muchos sistemas de descubrimiento y repositorios usan almacenamiento documental para sus índices de búsqueda, complementando una base de datos relacional subyacente.

### El modelo de grafos

Algunas relaciones entre datos son tan complejas y densas que ni el modelo relacional ni el documental las representan bien. Considérese el problema de modelar las redes de co-autoría en la ciencia: qué autores han colaborado entre sí, cómo se conectan esas redes, cuáles son los nodos de mayor influencia, cómo fluye la citación entre comunidades de investigadores. En un modelo relacional, este tipo de consultas requiere *joins* múltiples sobre tablas grandes, con un costo computacional que crece rápidamente.

Las bases de datos de grafos representan los datos como nodos (entidades) y aristas (relaciones entre entidades), y están optimizadas para navegar eficientemente esas redes de relaciones. La consulta "encuentra todos los investigadores que están a dos grados de separación del autor X en la red de co-autoría"» es trivial en una base de datos de grafos y extraordinariamente costosa en una base de datos relacional.

**Neo4j** es el sistema de grafos más conocido y usado. En el mundo de la investigación científica, sistemas como **OpenAlex** y algunas infraestructuras de análisis bibliométrico utilizan representaciones de grafo para modelar las redes de citación y colaboración de la literatura científica global.

Para el editor de una revista individual, las bases de datos de grafos son tecnología de infraestructura que opera en capas más profundas del ecosistema:

> los sistemas de descubrimiento y análisis bibliométrico las usan internamente, pero el editor raramente interactúa con ellas directamente.

### El modelo columnar

Las bases de datos columnares almacenan los datos organizados por columnas en lugar de por filas. En una base de datos relacional tradicional (orientada a filas), todos los datos de una fila se almacenan físicamente juntos en disco. En una base de datos columnar, todos los valores de una columna se almacenan juntos.

Esta diferencia, que parece un detalle de implementación, tiene consecuencias profundas para ciertos tipos de consultas. Si se necesita calcular el promedio de vistas de todos los artículos publicados en 2024, una base de datos orientada a filas debe leer cada fila completa (incluyendo título, autores, texto, etc.) para extraer el campo de vistas. Una base de datos columnar puede leer únicamente la columna de vistas y la columna de fecha de publicación, ignorando el resto de los datos: esto puede ser órdenes de magnitud más rápido cuando las tablas tienen millones de filas y cientos de columnas.

Los sistemas columnares (como Apache Cassandra, ClickHouse, o Amazon Redshift) son la tecnología subyacente de muchos sistemas de análisis y reportes a gran escala. En el ecosistema editorial, aparecen en los sistemas de métricas y estadísticas de uso que plataformas como SciELO o los grandes publishers comerciales usan para analizar el comportamiento de millones de lectores sobre millones de artículos.

### El modelo clave-valor y los sistemas en memoria

El modelo más simple de todos es el de clave-valor: un almacén donde cada pieza de información se guarda bajo una clave única, y se recupera proporcionando esa clave. No hay estructura relacional, no hay esquema, no hay lenguaje de consulta complejo: solo un diccionario a escala.

Esta simplicidad permite implementaciones extremadamente rápidas, especialmente cuando los datos se mantienen en memoria RAM en lugar de en disco. Redis es el sistema clave-valor más popular, utilizado masivamente como caché: en lugar de consultar la base de datos relacional para obtener los metadatos de un artículo muy visitado, el sistema guarda esos metadatos en Redis y los sirve directamente desde memoria, reduciendo la latencia de milisegundos a microsegundos.

Para el editor de una revista, Redis y sistemas similares son infraestructura invisible: operan en las capas de rendimiento de las plataformas de publicación, pero no interactúan con ellos directamente.

### NoSQL: el término y sus malentendidos

El término NoSQL (originalmente "Not Only SQL", aunque a menudo interpretado como "No SQL") se popularizó alrededor de 2009 para describir colectivamente los sistemas de bases de datos documentales, de grafos, columnares y clave-valor [5]. El término es más un marcador de época que una categoría técnica precisa: agrupa tecnologías muy diferentes bajo una etiqueta que principalmente significa **no es el modelo relacional tradicional**.

Un malentendido común es que NoSQL implica falta de transacciones o garantías de consistencia. Esto fue cierto para algunos sistemas NoSQL de primera generación, que sacrificaban garantías ACID en favor de escala y velocidad. Esta distinción, que fue cierta para algunos sistemas NoSQL de primera generación que sacrificaban garantías ACID en favor de escala y velocidad, se ha matizado considerablemente: en muchos casos, los sistemas más modernos han incorporado garantías de consistencia robustas para sus operaciones principales.

Más relevante aún es que la distinción "relacional vs. NoSQL" se ha vuelto menos útil a medida que los sistemas convergen. PostgreSQL, un sistema relacional, incorpora desde hace años soporte nativo para documentos JSON, arrays, y tipos de datos semiestructurados que eran dominio exclusivo de los sistemas NoSQL. MongoDB, un sistema documental, añadió soporte para transacciones multi-documento. Los límites entre categorías se han difuminado.

Para el editor, la lección práctica es esta: la elección entre modelos de bases de datos es una decisión de ingeniería que debe hacerse en función de las características específicas de los datos y las consultas que se necesitan realizar. No existe un modelo universalmente superior; existen modelos más o menos apropiados para contextos específicos.

## 4. Estado del arte: sistemas de bases de datos en el ecosistema editorial académico

### La arquitectura típica de una plataforma editorial moderna

Una plataforma editorial académica moderna raramente usa un único tipo de base de datos. La arquitectura típica es heterogénea: diferentes componentes del sistema usan el tipo de almacenamiento más apropiado para sus necesidades específicas.

En el núcleo del sistema se encuentra habitualmente una **base de datos relacional** que almacena los datos estructurados: usuarios, revistas, artículos, números, flujos de revisión, roles y permisos. Esta base de datos es la fuente de verdad del sistema: todo lo demás se deriva o sincroniza desde ella.

Complementando la base de datos relacional puede existir un **índice de búsqueda**, optimizado para búsquedas de texto completo. Las bases de datos relacionales pueden buscar texto, pero sus índices no están optimizados para las consultas complejas de relevancia, sinónimos y búsquedas semánticas que los usuarios esperan de un buscador moderno. Elasticsearch, por ejemplo, es la tecnología de búsqueda detrás de muchas implementaciones de OJS a escala.

En sistemas de alto tráfico, una capa de **caché** (Redis o Memcached) sirve contenido frecuentemente solicitado directamente desde memoria. Y en plataformas con capacidades analíticas, puede existir un **almacén de datos columnar** que consolida información histórica para reportes y métricas.

Esta arquitectura por capas es invisible para el editor que trabaja con la interfaz de OJS o gbpublisher, pero explica por qué estas plataformas tienen los comportamientos que tienen: por qué la búsqueda de texto completo se siente diferente a navegar por la tabla de contenidos de un número, o por qué las estadísticas de uso suelen tener cierto retardo respecto a los accesos en tiempo real.

### Open Journal Systems y su modelo de datos

Open Journal Systems (OJS), desarrollado y mantenido por el Public Knowledge Project (PKP), es la plataforma de gestión editorial de código abierto más usada en el mundo, con decenas de miles de revistas activas en todo el planeta [6]. Su arquitectura de base de datos refleja dos décadas de evolución y es instructiva para entender cómo una plataforma editorial organiza su modelo de datos.

El esquema de OJS 3.x (la versión actual) usa aproximadamente 80 tablas en su base de datos relacional, organizadas alrededor de entidades principales: journals (revistas), issues (números), submissions (envíos, que incluyen artículos en proceso de revisión y artículos publicados), users (usuarios con sus roles), y review_assignments (asignaciones de revisión). Esta estructura refleja el flujo de trabajo editorial: un envío pasa por etapas (revisión, edición, producción, publicación) que se registran en la base de datos, permitiendo rastrear el historial completo de cada artículo desde su recepción hasta su publicación.

Un aspecto particularmente relevante del modelo de datos de OJS es su manejo de los metadatos multilingüe. La tabla de traducciones (locale strings) permite que los títulos, resúmenes y palabras clave se almacenen en múltiples idiomas, reflejando la realidad de las revistas latinoamericanas que publican contenido en español, inglés y portugués simultáneamente. Esta decisión de diseño tiene implicaciones directas para la generación de XML-JATS: los metadatos multilingüe almacenados en la base de datos de OJS pueden exportarse directamente a los elementos correspondientes de JATS (`<title-group>` con `<trans-title>`, `<abstract>` con `<trans-abstract>`, etc.).

### gbpublisher y el modelo de base de datos para producción JATS

gbpublisher adopta un enfoque diferente al de OJS: mientras OJS es una plataforma de gestión editorial integral (que incluye la recepción de envíos, el proceso de revisión por pares, la comunicación con autores y revisores, y la publicación), gbpublisher se centra específicamente en la producción editorial: la transformación de manuscritos aceptados en publicaciones XML-JATS de alta calidad.

Esta diferencia de alcance se refleja en su modelo de datos. La base de datos de gbpublisher organiza la información alrededor de las entidades que un editor de producción necesita manejar: el artículo y sus metadatos completos, los autores con sus afiliaciones y ORCID, las referencias bibliográficas estructuradas componente a componente, los números de la revista, y los metadatos de la revista misma.

Un principio de diseño que gbpublisher aplica consistentemente es inferir estados a partir de la presencia o ausencia de datos, en lugar de mantener campos de estado redundantes. En lugar de un campo `estado_marcacion` que puede tener valores como "pendiente", "en proceso" o "completado", el sistema puede determinar el estado de marcación verificando si los campos obligatorios del artículo están completos. Este enfoque reduce la posibilidad de inconsistencias entre el estado declarado y el estado real de los datos.

Las referencias bibliográficas merecen mención especial en el modelo de datos de gbpublisher. En lugar de almacenar cada referencia como una cadena de texto (como haría un procesador de textos), gbpublisher las descompone en sus elementos constitutivos: autores, año, título del artículo, título de la revista o libro, volumen, número, páginas, DOI, etc. Esta descomposición es lo que permite generar referencias formateadas según diferentes estilos (Vancouver, APA, IEEE, etc.) mediante transformaciones XSLT, sin necesidad de almacenar múltiples versiones de la misma referencia. Y es lo que permite, a nivel de JATS, etiquetar cada componente de la referencia de manera que sistemas como CrossRef puedan verificarla automáticamente.

### Infraestructuras de indexación: SciELO, Redalyc y las bases de datos de la ciencia regional

SciELO y Redalyc no son solo repositorios de PDFs y XMLs: son infraestructuras de datos sofisticadas que integran información de miles de revistas para construir servicios de descubrimiento, análisis bibliométrico y visualización de la ciencia latinoamericana.

El SciELO Analytics [7], por ejemplo, proporciona, entre otras cosas, indicadores sobre el desempeño de las revistas de la red: distribución geográfica de autores, tendencias en colaboración internacional, perfiles de citas, adopción de buenas prácticas editoriales. Algunas de estas capacidades están disponibles en la interfaz pública de la plataforma; otras operan en la infraestructura interna de procesamiento de datos de la red. Estos indicadores son posibles porque SciELO no solo almacena los artículos como archivos XML: extrae los datos estructurados de esos XMLs y los ingesta en bases de datos analíticas que permiten consultas agregadas sobre el conjunto completo de la red. Esta arquitectura revela una lección importante:

> el valor del XML-JATS no se agota en la presentación de artículos individuales. El XML estructurado es una fuente de datos que, ingresada masivamente en infraestructuras analíticas, permite preguntas sobre la ciencia que serían imposibles de responder sobre colecciones de PDFs. ¿Cuántos artículos de la red SciELO incluyen datos de financiamiento declarados? ¿En qué proporción de los artículos hay al menos un autor con ORCID? ¿Cómo ha evolucionado la colaboración internacional entre revistas de diferentes países de la red? Estas preguntas son respondibles en minutos cuando los datos están en XML-JATS correctamente estructurado e ingresados en una base de datos analítica.

OpenAlex [8], el índice abierto de la producción científica global lanzado en 2022 como sucesor de Microsoft Academic Graph, es una de las infraestructuras más avanzadas actualmente disponibles para el análisis de la ciencia a escala global.

## 5. Bases de datos en el flujo editorial: dónde intervienen y cómo

Comprender en abstracto qué es una base de datos y cuáles son sus modelos es útil, pero insuficiente para el editor que necesita tomar decisiones prácticas sobre sus procesos. Esta sección recorre el flujo editorial de una revista científica —desde la recepción del manuscrito hasta la preservación del artículo publicado— identificando en cada etapa cómo intervienen las bases de datos, qué datos se almacenan, y qué consecuencias tiene la calidad de ese almacenamiento para el resultado final.

### Recepción y gestión de envíos

El primer contacto entre un manuscrito y una base de datos ocurre en el momento en que el
autor lo envía a través del sistema de gestión editorial. En OJS, ese momento genera múltiples
registros simultáneos: se crea una entrada en la tabla de submissions con los metadatos
declarados por el autor (título, resumen, palabras clave, idioma); se registran los autores del
envío con sus datos de contacto y afiliaciones; se almacena el archivo del manuscrito con una
referencia a su ubicación en el sistema de archivos; se asigna el envío al editor de sección
correspondiente; y se registra la fecha y hora del envío.

Este conjunto de operaciones, que desde la perspectiva del autor es simplemente "enviar el
artículo", desde la perspectiva de la base de datos es una transacción que debe completarse
íntegramente o revertirse: si alguno de los registros falla (por ejemplo, si hay un problema al
guardar el archivo), el sistema debe asegurarse de que no queden registros huérfanos en la
base de datos.

La calidad de los metadatos ingresados en esta etapa tiene consecuencias que se propagarán a
lo largo de todo el flujo. Si el autor escribe su afiliación de manera inconsistente
(Universidad de Buenos Aires, UBA o U. de Buenos Aires), esa inconsistencia se
almacenará en la base de datos y deberá corregirse manualmente más adelante. Si omite su
ORCID, el editor de producción tendrá que solicitarlo antes de generar el XML-JATS. Los
sistemas bien diseñados implementan validaciones en el formulario de envío que reducen estos
problemas, pero nunca los eliminan completamente: la calidad de los datos de entrada depende
en última instancia de la atención del autor y del rigor del sistema de recepción.

gbpublisher opera en una etapa diferente del flujo: no recibe envíos de autores sino que toma
como punto de partida los manuscritos ya aceptados por el sistema editorial de la revista. Su
equivalente al formulario de envío es el **formulario de ABM de artículos** (Alta, Baja,
Modificación), que constituye la puerta de entrada obligatoria a todo el proceso de producción:
un artículo no puede comenzar a editarse hasta que sus metadatos esenciales hayan sido
registrados en ese formulario y almacenados en la base de datos. Este requisito no es
burocrático sino estructural: la generación del XML-JATS, la aplicación de estilos de cita, la
construcción del `<front>` y del `<back>` del documento dependen de que los datos estén en la
base de datos antes de que empiece cualquier transformación.

Lo que distingue al formulario de ABM de un simple formulario de ingreso es que permanece
**activo durante todo el proceso de edición**, no solo al inicio. A medida que el trabajo
avanza —se confirman afiliaciones, se verifica el ORCID de un autor, se completa un DOI que
faltaba, se corrige la estructura de una referencia— el editor actualiza los datos en el
formulario y la base de datos los refleja de inmediato en todas las transformaciones
posteriores. Este comportamiento materializa el principio de fuente única de verdad discutido
más adelante en este artículo: el formulario de ABM es el lugar canónico donde viven los
metadatos del artículo.

Para acompañar este ciclo de vida extendido, gbpublisher implementa dos tipos de alertas
sobre el estado de los datos del formulario. Las **alertas informativas** señalan campos
incompletos o valores que podrían mejorarse (por ejemplo, la ausencia de ORCID en un autor,
o una afiliación sin identificador ROR), sin impedir que el proceso continúe: el editor es
notificado pero puede avanzar si decide que la información no está disponible en ese momento.
Las **alertas de bloqueo** señalan condiciones que hacen imposible generar un XML-JATS válido
(por ejemplo, la ausencia de título, de al menos un autor, o del ISSN de la revista), y
detienen el proceso hasta que se resuelvan. Esta distinción entre alerta informativa y alerta
de bloqueo refleja una decisión de diseño deliberada: no todos los metadatos tienen el mismo
peso para la validez del documento, y un sistema que bloquea el proceso por cualquier
imperfección sería más obstáculo que herramienta.

Finalmente, el formulario de ABM incorpora mecanismos de **reutilización de datos** para las
dos entidades que con mayor frecuencia se repiten a lo largo de la producción de una revista:
la autoría y las referencias bibliográficas. Un autor que ha participado en artículos anteriores
de la misma revista puede recuperarse desde la base de datos con sus datos completos
(nombre, ORCID, afiliación), sin necesidad de ingresarlos nuevamente. Una referencia
bibliográfica que aparece citada en múltiples artículos del mismo número —situación frecuente
en dossiers temáticos y números especiales— puede igualmente reutilizarse desde el registro
ya existente en la base de datos. Esta capacidad de reutilización no es solo una comodidad
operacional: es un mecanismo activo de normalización que reduce inconsistencias, porque el
mismo autor o la misma referencia aparecerán con exactamente los mismos datos en todos los
artículos que los utilicen.

### El proceso de revisión por pares como flujo de datos

El proceso de revisión por pares es, desde la perspectiva de la base de datos, un flujo de estados con actores, fechas límite y documentos adjuntos. OJS representa este flujo mediante la tabla review_assignments, donde cada asignación de revisión registra el revisor asignado, la fecha de invitación, la fecha de aceptación o rechazo, la fecha límite para entregar la revisión, la fecha efectiva de entrega, y la recomendación del revisor.

Esta representación permite al sistema generar recordatorios automáticos cuando los plazos se acercan, calcular tiempos promedio de revisión para los informes de desempeño de la revista, y rastrear la carga de revisión de cada revisor en el tiempo. Ninguna de estas funcionalidades requiere código especialmente sofisticado; todas dependen de que los datos del proceso se almacenen de manera estructurada y consistente en la base de datos.

Un aspecto que frecuentemente sorprende a los editores que reflexionan sobre esto por primera vez es que la decisión editorial —aceptar, rechazar, solicitar revisiones mayores o menores— también es un dato estructurado almacenado en la base de datos. El sistema puede entonces calcular automáticamente tasas de aceptación, distribución de decisiones por área temática, o tiempos promedio desde el envío hasta la decisión. Datos que en el modelo pre-digital requerirían revisar manualmente años de correspondencia editorial se vuelven consultables en segundos.

### La etapa de producción: donde la base de datos se convierte en XML-JATS

La etapa de producción es, para los propósitos de este manual, la más relevante de todas: es donde los datos almacenados en la base de datos del sistema editorial se transforman en XML-JATS. Este proceso de transformación merece examinarse con detalle porque revela de manera muy concreta la relación entre la base de datos y el estándar.

En el flujo de gbpublisher, la producción comienza con la importación de los metadatos del artículo aceptado. El editor ingresa o confirma en la interfaz de la herramienta los datos que formarán el elemento `<front>` del documento JATS: los datos de la revista (título, ISSN, editorial, URI), los datos del número (volumen, número, año, mes), y los datos del artículo propiamente dicho (título, resumen en todos los idiomas disponibles, palabras clave, tipo de artículo, sección, fechas de recepción y aceptación, DOI, licencia).

Cada uno de estos datos se almacena en la base de datos de gbpublisher en campos específicos con tipos de datos definidos. El título del artículo no es simplemente "un texto": es un campo de texto con un idioma asociado, porque JATS requiere declarar explícitamente el idioma de cada elemento textual. El DOI no es simplemente "una cadena": el sistema puede validar que tenga el formato correcto (10.XXXX/...) antes de almacenarlo, previniendo el tipo de errores que documentamos en el artículo sobre XML-JATS.

Los autores se almacenan en una tabla separada, vinculada al artículo mediante una tabla de relación que incluye el orden de aparición (primer autor, segundo autor, etc.) y el rol según la taxonomía CRediT. Cada autor tiene su propio registro con nombre, apellido, ORCID, y una o más afiliaciones. Las afiliaciones, a su vez, se almacenan descompuestas: institución, departamento, ciudad, país, con el identificador ROR (Research Organization Registry) cuando está disponible. Esta descomposición es exactamente la que requiere el XML-JATS para el elemento `<aff>` estructurado.

Las referencias bibliográficas siguen el mismo principio. En lugar de almacenar "García, J. (2020). Título del artículo. Revista X, 5(2), 100-115. https://doi.org/10.xxxx/xxx" como una cadena de texto, gbpublisher almacena cada componente en su campo correspondiente: apellido del primer autor, iniciales, año, título del artículo, título de la revista, volumen, número, primera página, última página, DOI. Cuando el editor necesita generar el XML-JATS, la transformación XSLT toma esos campos individuales y construye tanto el elemento `<element-citation>` estructurado (para procesamiento automático por CrossRef y otros sistemas) como la cadena formateada `<mixed-citation>` (para presentación visual al lector).

Este proceso revela una verdad fundamental sobre la relación entre bases de datos y XML-JATS: **el XML-JATS no es el origen de los datos sino su expresión**. Los datos viven en la base de datos, estructurados y relacionados según las reglas del modelo relacional. El XML-JATS es una serialización de esos datos en un formato estándar para su intercambio e interoperabilidad. Generar XML-JATS de calidad no es cuestión de aprender a escribir etiquetas XML: es cuestión de tener datos bien estructurados en la base de datos.

### Publicación y generación de formatos derivados

Una vez que el artículo está completo en la base de datos de producción, el sistema puede generar todos los formatos de salida necesarios. Esta generación es posible porque la base de datos contiene datos estructurados, no representaciones de presentación. El proceso es análogo a la separación entre contenido y presentación que describimos en el artículo sobre XML-JATS, pero aplicado a la capa de datos: la base de datos contiene el significado, y las transformaciones de salida (XSLT para XML, plantillas para PDF, hojas de estilo para HTML) convierten ese significado en presentaciones específicas.

En la práctica, esto significa que un cambio en los datos —la corrección de un error tipográfico en el nombre de un autor, la actualización de un DOI, la adición de una palabra clave omitida— puede propagarse automáticamente a todos los formatos de salida regenerando las transformaciones desde la base de datos. No hay que actualizar el PDF manualmente, luego el HTML manualmente, luego el XML-JATS manualmente: se actualiza el dato en la base de datos y se regeneran todos los formatos.

Este principio es especialmente importante en el contexto de las correcciones post-publicación, una práctica cada vez más común en la comunicación científica contemporánea. Cuando un artículo publicado requiere una corrección (una errata, una aclaración, una actualización de datos de autoría), el flujo basado en base de datos permite realizar esa corrección de manera controlada y consistente.

### Interacción con sistemas externos: APIs y sincronización de datos

Los sistemas editoriales modernos no son islas: necesitan intercambiar datos con infraestructuras externas. CrossRef para el registro de DOIs, ORCID para la verificación de identidad de autores, ROR para la identificación de instituciones, Sherpa Romeo para las políticas de autoarchivo, DOAJ para la verificación de estado de acceso abierto. Cada una de estas interacciones involucra bases de datos externas accedidas mediante APIs.

Una API (Application Programming Interface) es un mecanismo que permite a un sistema acceder a los datos de otro sistema de manera programática, sin intervención humana. Cuando OJS verifica en tiempo real si un ORCID ingresado por un autor es válido, está consultando la base de datos de ORCID a través de su API. Cuando gbpublisher registra el DOI de un artículo recién producido, está enviando datos a la base de datos de CrossRef a través de su API.

Estas interacciones tienen implicaciones prácticas para el editor. La calidad de los datos que se envían a APIs externas determina la calidad de los datos que esos sistemas tendrán sobre la revista. Un DOI mal formado enviado a CrossRef generará un registro defectuoso en la infraestructura global de citación. Un nombre de autor ingresado inconsistentemente (con y sin tilde, con y sin segundo apellido) en diferentes artículos dificultará la desambiguación automática de autoría en sistemas como OpenAlex.

La sincronización de datos entre sistemas es también una fuente frecuente de problemas que los editores experimentan sin siempre entender su origen. Cuando un artículo publicado en OJS no aparece inmediatamente en el buscador de la plataforma, frecuentemente es porque el índice de búsqueda (que puede ser un sistema separado como Elasticsearch) no se ha sincronizado aún con la base de datos principal de OJS. Cuando las estadísticas de uso muestran números ligeramente diferentes en distintas partes de la plataforma, puede ser porque diferentes vistas están consultando diferentes bases de datos (la principal y un almacén analítico) que se sincronizan con cierta latencia.

### Preservación: el archivo como base de datos a largo plazo

La preservación digital, que abordamos en el artículo sobre XML-JATS desde la perspectiva del formato, tiene también una dimensión de bases de datos que merece atención.

Los sistemas de preservación como CLOCKSS y Portico no solo almacenan archivos XML: mantienen bases de datos que registran qué contenido ha sido depositado, cuándo, en qué versión, y cuál es su estado de integridad. Cuando CLOCKSS verifica periódicamente que sus copias del contenido no se han corrompido, está ejecutando consultas sobre su base de datos de gestión de colecciones y comparando checksums (huellas digitales de los archivos) almacenados en esa base de datos con los valores calculados sobre los archivos actuales.

Para el editor, esta dimensión se traduce en una responsabilidad práctica: el depósito en sistemas de preservación no es un acto único sino un proceso continuo de sincronización. Cada nuevo número publicado debe depositarse; cada corrección debe propagarse. Los sistemas bien integrados automatizan este proceso mediante plugins que conectan la base de datos del sistema editorial directamente con las APIs de los sistemas de preservación.

## 6. Desafíos de integración entre bases de datos y datos estructurados XML

La relación entre bases de datos y XML no es solo técnica: es también conceptual, y los desafíos que plantea revelan tensiones fundamentales entre dos paradigmas de organización de la información que tienen filosofías diferentes y, en ciertos aspectos, incompatibles.

### El problema del impedance mismatch

En informática, el término *impedance mismatch* (desajuste de impedancia, tomado analógicamente de la ingeniería eléctrica) describe la fricción conceptual que surge cuando se intenta mapear datos entre dos modelos de representación que tienen estructuras fundamentalmente diferentes [9].

El caso más conocido es el impedance mismatch entre el modelo relacional y los modelos de objetos de la programación orientada a objetos: un objeto en un lenguaje como Python o Java puede tener jerarquías de herencia, referencias circulares, y estructuras anidadas que no tienen mapeo natural a tablas relacionales. Los ORM (Object-Relational Mappers) son herramientas que intentan resolver este problema, con éxito parcial y costos propios.

En el contexto editorial, existe un impedance mismatch análogo entre el modelo relacional y XML. XML es un modelo jerárquico (documentos anidados) mientras que el modelo relacional es plano (tablas con filas). Un artículo científico en XML-JATS tiene una estructura profundamente jerárquica: el documento contiene secciones, las secciones contienen párrafos, los párrafos contienen texto con marcado en línea (cursivas, negritas, notas al pie, referencias cruzadas), y cualquier nivel puede contener figuras, tablas, ecuaciones. Representar esta jerarquía en tablas relacionales requiere tomar decisiones de diseño que inevitablemente simplifican o distorsionan la estructura original.

La solución que herramientas como gbpublisher adoptan es pragmática: almacenar en la base de datos relacional los metadatos estructurados (los datos del `<front>` y los componentes discretos del `<back>`) y manejar el contenido narrativo del `<body>` como texto con marcado ligero (Markdown) que se transforma a XML en el momento de la generación del JATS. Esta partición entre **metadatos relacionales** y **contenido narrativo** resuelve el *impedance mismatch* al precio de no estructurar semánticamente el cuerpo del artículo en la base de datos, lo que es una limitación aceptable en el contexto de una herramienta de producción editorial.

### Consistencia entre la base de datos y el archivo XML

Un desafío operacional frecuente es mantener la consistencia entre los datos almacenados en la base de datos y los archivos XML generados a partir de ellos. Si el editor corrige un dato en la base de datos (por ejemplo, el ORCID de un autor) pero no regenera el XML, el archivo XML queda desactualizado respecto a la base de datos. Si el editor edita directamente el archivo XML (por ejemplo, para corregir una errata tipográfica en el texto del artículo) sin actualizar la base de datos correspondiente, ocurre la situación inversa.

Este problema se conoce en ingeniería de software como el problema de la **fuente única de verdad** (*single source of truth*): en un sistema bien diseñado, cada dato tiene exactamente un lugar canónico donde reside, y todas las demás representaciones se derivan de ese lugar. Cuando hay múltiples representaciones que pueden modificarse independientemente, la consistencia se vuelve responsabilidad del usuario, y los errores son inevitables.

La respuesta arquitectónica a este problema es clara: la base de datos debe ser la fuente única de verdad, y el XML debe ser siempre un artefacto derivado, regenerable en cualquier momento desde los datos de la base de datos. Los flujos de trabajo que permiten editar el XML directamente —fuera de la base de datos— crean inevitablemente situaciones de inconsistencia. Esto no significa que la edición directa de XML sea siempre incorrecta (hay casos, especialmente en la marcación del cuerpo del artículo, donde la edición XML es la herramienta más precisa disponible), pero sí que debe gestionarse con cuidado, documentando claramente cuándo el XML es la fuente y cuándo lo es la base de datos.

### El problema de la granularidad: cuánto estructurar

Una pregunta que toda implementación de base de datos para producción JATS debe responder es cuánta granularidad imponer en la estructuración de los datos. En un extremo, se podría almacenar cada artículo completo como un único campo de texto (o directamente como un archivo XML en el sistema de archivos), usando la base de datos solo como índice. En el otro extremo, se podría intentar almacenar en campos separados cada elemento semántico del artículo: cada párrafo, cada sección, cada elemento de marcado en línea.

El primer extremo hace la base de datos trivial pero elimina sus ventajas: no es posible hacer consultas sobre metadatos específicos, ni generar formatos de salida alternativos, ni verificar completitud o integridad de los datos. El segundo extremo ofrece máxima flexibilidad pero impone una complejidad de implementación y uso que puede ser prohibitiva, especialmente para equipos editoriales pequeños.

La práctica de los sistemas exitosos converge en una solución intermedia pragmática, que podríamos llamar **estructuración suficiente**: se estructuran en campos discretos todos los metadatos que serán usados para búsqueda, filtrado, generación de formatos o interoperabilidad con sistemas externos; el contenido narrativo que no tiene esas funciones se almacena como texto con marcado ligero. Esta es exactamente la filosofía de gbpublisher: máxima estructuración para metadatos (autores, afiliaciones, referencias, identificadores) y marcado de texto para el cuerpo narrativo.

### Migración de datos: el desafío de los legados

Toda revista con historia tiene un legado de datos almacenados en formatos anteriores: PDFs escaneados de números viejos, artículos en Word que nunca se convirtieron a XML, bases de datos de OJS de versiones anteriores que no se actualizaron, hojas de cálculo con metadatos parciales de años de producción. La integración de estos datos legados en un sistema moderno basado en bases de datos y XML-JATS es uno de los desafíos más complejos que enfrenta una revista en proceso de modernización.

El problema de la migración de datos no es solo técnico: es también editorial. Los datos legados frecuentemente contienen inconsistencias, omisiones y errores que fueron aceptables en el contexto en que se crearon pero que no cumplen los requisitos del sistema moderno. El proceso de migración obliga a tomar decisiones sobre cómo tratar esos casos: ¿se normalizan los nombres de autores inconsistentes? ¿Se añaden DOIs retroactivos a artículos viejos que no los tenían? ¿Se estructuran las referencias de artículos históricos componente a componente, o se preservan como cadenas de texto?

No hay una respuesta universalmente correcta a estas preguntas; dependen de los recursos disponibles, los objetivos de la revista y el uso que se pretende hacer de los datos históricos. Pero lo que sí es claro es que la migración de datos legados requiere una estrategia explícita, no puede hacerse *ad hoc*. Y que el costo de esa migración es una de las razones por las que la modernización editorial hacia XML-JATS es un proceso que lleva años, no meses.

### Integridad referencial y la cadena de identificadores

El modelo relacional implementa un mecanismo llamado **integridad referencial**: si una tabla B
tiene una clave foránea que apunta a la tabla A, el sistema garantiza que no puede existir un
registro en B que apunte a un registro inexistente en A. Esto previene un tipo de
inconsistencia particularmente dañino: datos huérfanos que referencian algo que no existe.

En el contexto editorial, la integridad referencial tiene un equivalente conceptual que va más
allá de la base de datos local: la cadena de identificadores persistentes. Un artículo tiene un
DOI que lo identifica en CrossRef. Ese DOI referencia metadatos en CrossRef que incluyen el
ISSN de la revista, que a su vez referencia registros en las bases de datos de ISSN
internacional. Los autores tienen ORCIDs que los identifican en la base de datos de ORCID.
Las instituciones tienen RORs que las identifican en el Research Organization Registry.

Esta cadena de identificadores es una forma de integridad referencial distribuida, global y
federada: la validez de los metadatos de un artículo depende no solo de la consistencia interna
de la base de datos local sino de la consistencia con todos estos sistemas externos. Un artículo
que declara un ORCID de autor que no existe en la base de datos de ORCID tiene un problema
de integridad referencial, aunque ese problema no sea detectable por el sistema de gestión de
la base de datos local.

Esta dimensión distribuida de la integridad referencial es relativamente nueva en el ecosistema
editorial y todavía no está completamente resuelta en la mayoría de los sistemas. gbpublisher
aborda el problema mediante una **doble validación** implementada directamente en el
formulario de ABM. El primer nivel es una validación interna: antes de aceptar un identificador,
el sistema verifica que no esté ya registrado en la base de datos local con una asignación
incorrecta, por ejemplo un ORCID asociado a un autor diferente al que se está ingresando, o un
ROR asignado a una institución distinta de la que corresponde. Este tipo de error —un
identificador correcto en su forma pero mal asignado en la base de datos local— es más difícil
de detectar que un identificador malformado, porque supera cualquier validación de formato y
solo se revela al cruzar el valor con el registro ya existente.

El segundo nivel es una validación externa: gbpublisher consulta las APIs de los servicios
correspondientes (ORCID, ROR, CrossRef) para verificar que el identificador ingresado existe
y corresponde a la entidad declarada. Esta verificación convierte una operación que en la
mayoría de los sistemas queda delegada al criterio del editor en un proceso con confirmación
automática.

La búsqueda de ORCID en gbpublisher incorpora además el tratamiento de un problema
específico y frecuente en la práctica: las **concurrencias de ORCID**. Un mismo investigador
puede tener registrados más de un ORCID, situación que ocurre cuando el autor se registró en
la plataforma en diferentes momentos sin advertir que ya tenía una cuenta activa, o cuando
registros duplicados fueron creados por terceros. Cuando la búsqueda por nombre de autor
devuelve múltiples ORCIDs que corresponden a la misma persona, gbpublisher los presenta al
editor para que seleccione el identificador canónico, que habitualmente es el más antiguo o el
que tiene el perfil más completo. Esta detección de concurrencias no es trivial: requiere que el
sistema confronte el nombre del autor contra los registros de la API de ORCID y evalúe los
resultados, en lugar de simplemente validar que un identificador proporcionado manualmente
tiene el formato correcto. La diferencia es significativa: un sistema que solo valida formato
acepta cualquier ORCID bien formado aunque sea el incorrecto; un sistema que busca y
detecta concurrencias ayuda al editor a identificar cuál de los múltiples identificadores
asociados a un autor es el que debe usarse.

Los sistemas más avanzados del ecosistema implementan verificaciones automáticas similares
contra APIs externas en el momento del ingreso de datos. Pero muchos sistemas, especialmente
los más simples, no lo hacen, delegando esa responsabilidad enteramente al editor. La doble
validación de gbpublisher —interna contra la base de datos local, externa contra los servicios
de identificadores— representa una respuesta concreta al problema de mantener integridad
referencial en un ecosistema distribuido donde los datos de la revista local deben ser
consistentes no solo consigo mismos sino con infraestructuras globales que ningún sistema
editorial controla de manera unilateral.

### El rendimiento como variable de diseño

Un aspecto que los editores raramente consideran explícitamente es el rendimiento de la base de datos: cuánto tiempo tarda el sistema en responder a las consultas. Para revistas pequeñas con pocos miles de registros, el rendimiento raramente es un problema visible. Para plataformas que gestionan decenas de miles de artículos y miles de usuarios concurrentes (como las instalaciones de OJS de las redes SciELO y Redalyc), el rendimiento es una variable de diseño crítica.

Las herramientas principales para optimizar el rendimiento de bases de datos relacionales son los **índices**: estructuras adicionales que el sistema mantiene para acelerar consultas frecuentes. Un índice sobre el campo DOI de la tabla de artículos permite encontrar un artículo por su DOI en tiempo constante en lugar de escanear toda la tabla. Un índice sobre el campo de fecha de publicación permite ordenar artículos por fecha sin necesidad de reordenar todos los registros en cada consulta.

Sin embargo, los índices tienen un costo: consumen espacio en disco y ralentizan las operaciones de escritura (porque cada vez que se inserta o actualiza un registro, todos los índices relevantes deben actualizarse). El diseño de índices apropiados para una aplicación específica requiere conocimiento tanto del modelo de datos como de los patrones de uso: qué consultas se realizan con más frecuencia, cuál es la proporción entre lecturas y escrituras, qué tamaño tendrá la base de datos a largo plazo.

Para el editor que no es administrador de bases de datos, la lección práctica es esta:

> si el sistema editorial parece lento y la causa no es evidente, el problema puede estar en la falta de índices apropiados en la base de datos o en un mal diseño de la misma.

## 7. Desafíos actuales y perspectivas

### La apertura de los datos de investigación: de los artículos a los datasets

Durante décadas, la unidad fundamental de la comunicación científica fue el artículo. Los datos sobre los que ese artículo se basaba —las mediciones, las observaciones, las encuestas, los registros clínicos— permanecían en los archivos del laboratorio o, en el mejor de los casos, en apéndices publicados junto al texto. Esta situación comenzó a cambiar significativamente en la década de 2010, cuando las políticas de ciencia abierta de organismos financiadores y revistas empezaron a exigir o recomendar enfáticamente que los datos de investigación se publicaran de manera abierta y reutilizable [10].

El movimiento de datos abiertos de investigación (open research data) plantea desafíos específicos para las bases de datos editoriales. Un artículo que antes era una unidad relativamente autónoma ahora puede tener asociados decenas de datasets almacenados en repositorios especializados (Zenodo, Dryad, Figshare, OSF, repositorios institucionales), cada uno con sus propios metadatos, identificadores (DOIs de datos), y formatos. La base de datos editorial necesita no solo registrar la existencia de estos datasets sino mantener vínculos persistentes y verificables entre el artículo y sus datos de soporte.

XML-JATS incorpora elementos específicos para registrar estos vínculos (`<supplementary-material>`, `<data-availability>`), pero la gestión de esa información en la base de datos editorial sigue siendo un área en desarrollo. Los sistemas más avanzados comienzan a implementar la verificación automática de que los DOIs de datasets declarados en un artículo son válidos y resolubles, de la misma manera que ya verifican los DOIs de referencias bibliográficas. La integración completa entre la base de datos del sistema editorial, los repositorios de datos y las infraestructuras de metadatos de datos (DataCite [11], que gestiona el registro de DOIs para datasets de la misma manera que CrossRef lo hace para artículos) es una de las fronteras activas del ecosistema.

Para el editor latinoamericano, esta tendencia tiene una dimensión práctica inmediata: las políticas editoriales de muchas revistas indexadas en SciELO y Redalyc ya exigen o recomiendan que los autores depositen sus datos en repositorios abiertos y declaren su disponibilidad en el artículo. Gestionar esa información como dato estructurado en la base de datos del sistema editorial —no como texto libre en el cuerpo del artículo— es una práctica que mejora la trazabilidad, la verificación y la interoperabilidad, pero que todavía no es universal.

### Inteligencia artificial y bases de datos: el nuevo ciclo

La expansión de los sistemas de inteligencia artificial en el ecosistema de publicación científica no es independiente de las bases de datos: la IA depende de ellas de maneras fundamentales, y a su vez las está transformando.

Los grandes modelos de lenguaje (Large Language Models, LLMs) que han captado la atención pública desde 2022 fueron entrenados sobre corpus masivos de texto que provienen en gran parte de la web, incluyendo, entre otras fuentes, textos académicos disponibles públicamente. Sin embargo, los usos más relevantes de la IA en el contexto editorial son más específicos: sistemas entrenados o ajustados para tareas concretas del flujo editorial, que operan sobre los contenidos y metadatos gestionados por las plataformas de publicación.

La automatización del marcado XML-JATS es quizás el caso de uso más directo. Herramientas como Marcalyc ya incorporan algoritmos de automatización e inteligencia artificial para inferir automáticamente elementos estructurales de los artículos —como autores, resúmenes, palabras clave, secciones y citación—. Estos resultados son posteriormente supervisados y corregidos por el editor, quien valida el marcado final en XML-JATS.

La pregunta que muchos editores se hacen hoy es si los LLMs modernos podrían automatizar completamente ese proceso, eliminando la necesidad de revisión humana. La evidencia disponible sugiere que, aunque estos modelos muestran un rendimiento notable en tareas de extracción de información a partir de documentos bien estructurados, continúan produciendo errores de manera no predecible —especialmente en casos ambiguos o atípicos—, lo que los vuelve poco fiables para una automatización completa en contextos donde la precisión es crítica [12]. En consecuencia, la supervisión humana sigue siendo indispensable, aunque su papel está cambiando: de la producción manual del marcado a la verificación y corrección de resultados generados automáticamente.

Un desarrollo más reciente y con implicaciones profundas para las bases de datos editoriales es el de los sistemas de recuperación aumentada por generación (Retrieval Augmented Generation, RAG). En estos sistemas, un modelo de lenguaje no se limita a su conocimiento interno —fijado en el momento del entrenamiento—, sino que puede consultar dinámicamente bases de datos o repositorios documentales para fundamentar sus respuestas en información actualizada. En el ámbito editorial, esto habilita herramientas de asistencia capaces de responder preguntas sobre políticas editoriales a partir de documentación interna, o de sugerir revisores potenciales mediante el análisis de historiales de evaluación y perfiles temáticos almacenados en la plataforma.

Este tipo de integración entre inteligencia artificial y bases de datos editoriales se encuentra aún en una fase temprana de desarrollo práctico, pero señala una dirección clara de evolución: no sistemas que reemplacen el flujo editorial, sino sistemas que lo asistan mediante el aprovechamiento activo de las bases de datos construidas a lo largo del propio proceso de publicación.

### La web semántica y los datos enlazados

Paralelo al desarrollo de las bases de datos relacionales y NoSQL, ha existido desde inicios de los años 2000 un proyecto de más largo aliento: la **web semántica**, una visión propuesta originalmente por Tim Berners-Lee para transformar la web de una colección de documentos legibles por humanos en una red de datos legibles por máquinas y relacionados entre sí de manera explícita [13].

Los **datos enlazados** (Linked Data) son la manifestación práctica de esta visión: un conjunto de principios y tecnologías (RDF, OWL, SPARQL) para publicar datos en la web de manera que sean identificables mediante URIs, descritos con vocabularios estándar, y conectados con otros conjuntos de datos relacionados. La promesa es una web donde las relaciones entre entidades (este artículo fue escrito por este autor, este autor trabaja en esta institución, esta institución está ubicada en este país) sean explícitas y navegables por máquinas.

En el ecosistema de publicación científica, esta visión ha encontrado implementaciones parciales y pragmáticas. ORCID, ROR y CrossRef publican sus datos como datos enlazados, con URIs persistentes para cada entidad (cada investigador, cada institución, cada publicación) y vocabularios estándar para describir las relaciones. El proyecto Wikidata [14] incluye entidades científicas (publicaciones, investigadores, instituciones) conectadas con el resto del conocimiento representado en Wikidata, creando un grafo del conocimiento que integra ciencia con cultura, geografía, historia.

Para el editor, la relevancia práctica de los datos enlazados se materializa principalmente a través de los identificadores persistentes. Cuando un artículo en JATS declara el ORCID de su autor, el ROR de su institución, el DOI de cada referencia citada, y el DOI de los datasets usados, está en efecto conectando ese artículo al grafo del conocimiento científico global mediante datos enlazados. Los metadatos del artículo, expresados en JATS y depositados en CrossRef, se convierten en nodos del grafo con relaciones explícitas a otros nodos (el autor, la revista, los artículos citados).

Esta perspectiva permite entender por qué la completitud y precisión de los metadatos no es simplemente una cuestión de buena práctica editorial: es una contribución activa al grafo del conocimiento científico. Un artículo con metadatos incompletos o incorrectos es un nodo con relaciones rotas o ausentes en ese grafo: reduce la conectividad del conocimiento de maneras que van más allá del artículo individual.

### Soberanía de datos y dependencia de infraestructuras

Una tensión creciente en el ecosistema de publicación científica global es la concentración de infraestructura de datos en manos de un pequeño número de actores, predominantemente corporaciones y organizaciones del Norte Global. Web of Science fue adquirido por Clarivate Analytics; Scopus pertenece a Elsevier; los metadatos de CrossRef, aunque técnicamente accesibles, son gestionados por una organización con sede en Estados Unidos; incluso ORCID, pese a ser una organización sin fines de lucro, centraliza datos de identidad de investigadores de todo el mundo.

Esta concentración plantea preguntas sobre **soberanía de datos** que son particularmente relevantes para regiones como América Latina, donde la producción científica depende de infraestructuras sobre las que no tiene control directo [15]. Si CrossRef decide cambiar sus políticas de acceso a los metadatos, si ORCID cambia su modelo de financiamiento, si Clarivate modifica los criterios de inclusión en Web of Science, las consecuencias para las revistas latinoamericanas son inmediatas pero las posibilidades de influencia son limitadas.

Las respuestas a este desafío son múltiples y se desarrollan en paralelo. OpenAlex [8], mencionado anteriormente, es una respuesta directa: un índice completamente abierto de la producción científica global, financiado por el Mellon Foundation y operado por OurResearch, diseñado explícitamente para ser una alternativa abierta a los grandes índices propietarios. La iniciativa AmeliCA [16], impulsada en gran parte por actores latinoamericanos, propone una infraestructura regional de publicación científica basada en código abierto y gobernanza comunitaria.

Para el editor de una revista individual, la implicación práctica es doble. Por un lado, el uso de sistemas de código abierto (OJS, gbpublisher) y el depósito en infraestructuras abiertas (OpenAlex, DOAJ, repositorios institucionales) reduce la dependencia de actores propietarios. Por otro lado, la calidad y completitud de los metadatos que la revista proporciona a estas infraestructuras determina su visibilidad y usabilidad en el ecosistema abierto:

> una revista cuyos metadatos son incompletos o incorrectos será menos visible en OpenAlex que una revista con metadatos cuidadosamente gestionados, independientemente de su calidad científica intrínseca.

### El futuro inmediato: bases de datos vectoriales y búsqueda semántica

Un desarrollo muy reciente que comenzará a impactar el ecosistema editorial en los próximos años es el surgimiento de las **bases de datos vectoriales** (vector databases). Estos sistemas, diseñados originalmente para la industria de la inteligencia artificial, almacenan representaciones numéricas multidimensionales (vectores) de fragmentos de texto, imágenes u otros tipos de contenido, y están optimizados para encontrar el contenido más "similar" a una consulta, no exactamente igual.

La diferencia con la búsqueda tradicional es significativa. Una búsqueda tradicional en una base de datos editorial devuelve artículos que contienen exactamente las palabras buscadas. Una búsqueda semántica basada en vectores puede encontrar artículos que tratan sobre el mismo concepto aunque usen vocabulario diferente: buscar "modelos de lenguaje grande" y encontrar también artículos sobre "LLMs" y "transformers" aunque esas palabras no estén en la consulta. O encontrar artículos metodológicamente similares al artículo que el investigador está leyendo, aunque traten sobre temas distintos.

Sistemas como Semantic Scholar [17] ya implementan búsqueda semántica sobre la literatura científica, con resultados que muchos investigadores encuentran más útiles que las búsquedas por palabras clave. La integración de estas capacidades en las plataformas de publicación regional (OJS, SciELO, Redalyc) es previsible en los próximos años.

Para el ecosistema editorial latinoamericano, este desarrollo tiene una implicación importante:

> la búsqueda semántica opera directamente sobre el texto del artículo, no solo sobre sus metadatos.

Esto significa que artículos en español o portugués serán buscables semánticamente por usuarios que busquen en inglés y viceversa, siempre que los modelos de *embeddings* usados sean multilingüe. La barrera idiomática que ha limitado históricamente la visibilidad de la ciencia latinoamericana en el ecosistema anglófono podría reducirse en forma significativa, aunque el alcance real de ese efecto dependerá de la calidad multilingüe de los modelos de embeddings que cada plataforma adopte.

## 8. Conclusiones para el editor

Este recorrido por la historia, los modelos, el estado del arte y los desafíos de las bases de datos ha tenido un propósito específico: no convertir al editor en un administrador de bases de datos, sino dotarlo del vocabulario y los conceptos necesarios para entender el ecosistema tecnológico en el que trabaja y tomar decisiones informadas sobre él.

Algunas conclusiones merecen subrayarse:

**Las bases de datos son el substrato del XML-JATS.** El XML que una revista produce no surge de la nada: es la expresión de datos almacenados y estructurados en una base de datos. La calidad del XML depende directamente de la calidad de los datos en la base de datos. Invertir en la disciplina de ingreso de datos —usar identificadores persistentes, normalizar nombres de autores e instituciones, descomponer referencias en sus elementos constitutivos— es la inversión más eficiente que un equipo editorial puede hacer para mejorar la calidad de su producción.

**El modelo relacional sigue siendo el fundamento.** A pesar de la proliferación de modelos alternativos, las bases de datos relacionales siguen siendo la tecnología más apropiada para el núcleo de los sistemas editoriales: los datos de una revista son naturalmente relacionales, sus integridades son expresables como restricciones declarativas, y las consultas editoriales típicas son exactamente el tipo de consultas para las que SQL fue diseñado. La diversificación de modelos (documental, grafos, vectorial) ocurre en capas especializadas del ecosistema, no en el núcleo editorial.

**La fuente única de verdad no es un capricho de diseño sino una necesidad operacional.** En cualquier sistema donde los mismos datos existen en múltiples representaciones (base de datos local, archivo XML, metadatos en CrossRef, registros en sistemas de preservación), la consistencia solo puede mantenerse si una de esas representaciones es canónica y las demás se derivan de ella. Identificar y proteger esa fuente única de verdad es una decisión de arquitectura que tiene consecuencias directas sobre la confiabilidad de todo el sistema.

**Los identificadores persistentes son la integridad referencial del ecosistema global.** DOI, ORCID, ROR, ISSN: estos identificadores son el mecanismo por el cual los datos de la revista se conectan con el grafo del conocimiento científico global. Su completitud y corrección no es un detalle burocrático: es la condición de posibilidad de la interoperabilidad. Un artículo sin ORCID de sus autores es un artículo cuya autoría no se puede desambiguar automáticamente. Un artículo con un DOI mal formado es un artículo que puede no resolverse. Estas omisiones tienen consecuencias medibles en la visibilidad e impacto de la revista.

**La apertura de los datos, la IA y los datos enlazados convergen en la misma dirección.** Los tres desarrollos más importantes del ecosistema en los últimos años —la exigencia de datos de investigación abiertos, la integración de IA en flujos editoriales, y la maduración de las infraestructuras de datos enlazados— comparten una premisa: que el valor de la producción científica aumenta cuando los datos son **estructurados, abiertos y conectados**. Esta convergencia confirma que las inversiones en calidad de metadatos y estructuración de datos no responden a modas tecnológicas pasajeras sino a una tendencia estructural del ecosistema.

**El desafío de la soberanía de datos es real y requiere respuesta activa.** La infraestructura de datos que sostiene la visibilidad internacional de la ciencia latinoamericana está en gran parte controlada por actores externos a la región. La respuesta no puede ser ignorar esa infraestructura (lo que equivaldría a la invisibilidad), pero tampoco puede ser aceptarla pasivamente. El fortalecimiento de infraestructuras regionales abiertas (AmeliCA, OpenAlex, repositorios institucionales), el uso de estándares abiertos (JATS, ORCID, ROR, DOI), y el desarrollo de herramientas de código abierto adaptadas al contexto latinoamericano (OJS, gbpublisher) son las respuestas disponibles, y todas requieren que los editores comprendan suficientemente el ecosistema para elegir con criterio.

El editor que entiende qué es una base de datos, cómo se relaciona con el XML que produce, y qué rol juega en el ecosistema global no es un editor que sabe más de tecnología:

> es un editor que sabe mejor por qué hace lo que hace, y eso cambia la calidad de las decisiones que toma.

---

## Referencias

[1] Codd, E. F. (1970). A relational model of data for large shared data banks. *Communications of the ACM*, 13(6), 377–387. https://doi.org/10.1145/362384.362685

[2] Chamberlin, D. D., & Boyce, R. F. (1974). SEQUEL: A structured English query language. En *Proceedings of the 1974 ACM SIGFIDET Workshop on Data Description, Access and Control* (pp. 249–264). ACM. https://doi.org/10.1145/800296.811515

[3] Stonebraker, M., & Rowe, L. A. (1986). The design of POSTGRES. En *Proceedings of the 1986 ACM SIGMOD International Conference on Management of Data* (pp. 340–355). ACM. https://doi.org/10.1145/16894.16888

[4] Willinsky, J. (2005). Open Journal Systems: An example of open source software for journal management and publishing. *Library Hi Tech*, 23(4), 504–519. https://doi.org/10.1108/07378830510636300

[5] Leavitt, N. (2010). Will NoSQL databases live up to their promise? *IEEE Computer*, 43(2), 12–14. https://doi.org/10.1109/MC.2010.58

[6] PKP (Public Knowledge Project). (2024). *OJS usage statistics*. Recuperado de https://pkp.sfu.ca/software/ojs/

[7] Packer, A. L., Cop, N., Luccisano, A., Ramalho, A., & Spinak, E. (2014). *SciELO – 15 años de acceso abierto: un estudio analítico sobre acceso abierto y comunicación en la investigación*. UNESCO.

[8] Priem, J., Piwowar, H., & Orr, R. (2022). OpenAlex: A fully-open index of the world's research. *arXiv*. https://arxiv.org/abs/2205.01833

[9] Ireland, C., Bowers, D., Newton, M., & Waugh, K. (2009). A classification of object-relational impedance mismatch. En *Proceedings of the 2009 First International Confererence on Advances in Databases, Knowledge, and Data Applications* (pp. 36–43). IEEE. https://doi.org/10.1109/DBKDA.2009.11

[10] Wilkinson, M. D., Dumontier, M., Aalbersberg, I. J., Appleton, G., Axton, M., Baak, A., Blomberg, N., Boiten, J.-W., da Silva Santos, L. B., Bourne, P. E., Bouwman, J., Brookes, A. J., Clark, T., Crosas, M., Dillo, I., Dumon, O., Edmunds, S., Evelo, C. T., Finkers, R., … Mons, B. (2016). The FAIR guiding principles for scientific data management and stewardship. *Scientific Data*, 3, 160018. https://doi.org/10.1038/sdata.2016.18

[11] DataCite Metadata Working Group. (2021). *DataCite Metadata Schema Documentation for the Publication and Citation of Research Data and Other Research Outputs, version 4.4*. DataCite. https://doi.org/10.14454/3w3z-sa82

[12] Shah, N. H., Entwistle, D., & Pfeffer, M. A. (2023). Creation of a large language model–based chatbot for biomedical literature exploration. *JAMA Network Open*, 6(8), e2330620. https://doi.org/10.1001/jamanetworkopen.2023.30620

[13] Berners-Lee, T., Hendler, J., & Lassila, O. (2001). The semantic web. *Scientific American*, 284(5), 34–43. https://doi.org/10.1038/scientificamerican0501-34

[14] Vrandečić, D., & Krötzsch, M. (2014). Wikidata: A free collaborative knowledgebase. *Communications of the ACM*, 57(10), 78–85. https://doi.org/10.1145/2629489

[15] Babini, D., & Rovelli, L. (2020). *Tendencias recientes en las políticas científicas de ciencia abierta y acceso abierto en Iberoamérica*. CLACSO; Fundación Dialnet. https://doi.org/10.2307/j.ctv1gm02zq

[16] Becerril-García, A., & Aguado-López, E. (2019). The end of a centralized open access project and the beginning of a community-based sustainable infrastructure for Latin America: Redalyc.org after Fifteen Years. En *Scholarly Communication in Latin America, Spain, Portugal and the Caribbean* (pp. 89–104). ELPUB. https://doi.org/10.4000/proceedings.elpub.2019.20

[17] Lo, K., Wang, L. L., Neumann, M., Kinney, R., & Weld, D. S. (2020). S2ORC: The Semantic Scholar open research corpus. En *Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics* (pp. 4969–4983). ACL. https://doi.org/10.18653/v1/2020.acl-main.447

---

## Bibliografía adicional

Abiteboul, S., Hull, R., & Vianu, V. (1995). *Foundations of Databases*. Addison-Wesley.

Codd, E. F. (1990). *The Relational Model for Database Management: Version 2*. Addison-Wesley.

Date, C. J. (2003). *An Introduction to Database Systems* (8.ª ed.). Addison-Wesley.

García-Molina, H., Ullman, J. D., & Widom, J. (2008). *Database Systems: The Complete Book* (2.ª ed.). Pearson Prentice Hall.

Hartig, O., & Pérez, J. (2018). Semantics and complexity of GraphQL. En *Proceedings of the 2018 World Wide Web Conference* (pp. 1155–1164). ACM. https://doi.org/10.1145/3178876.3186014

Kleppmann, M. (2017). *Designing Data-Intensive Applications: The Big Ideas Behind Reliable, Scalable, and Maintainable Systems*. O'Reilly Media.

Loshin, D. (2010). *Master Data Management*. Morgan Kaufmann.

Ramakrishnan, R., & Gehrke, J. (2002). *Database Management Systems* (3.ª ed.). McGraw-Hill.

Sadalage, P. J., & Fowler, M. (2012). *NoSQL Distilled: A Brief Guide to the Emerging World of Polyglot Persistence*. Addison-Wesley.

Sandoval Almazán, R. (2011). Gobierno electrónico y bases de datos: fundamentos para su comprensión en las administraciones públicas latinoamericanas. *Gestión y Política Pública*, 20(2), 431–462.

Spinak, E. (2017). Sobre las veintidós definiciones de acceso abierto y las bases de datos relacionales. *SciELO en Perspectiva*. Recuperado de https://blog.scielo.org/es/

Stonebraker, M., & Çetintemel, U. (2005). "One size fits all": An idea whose time has come and gone. En *Proceedings of the 21st International Conference on Data Engineering* (pp. 2–11). IEEE. https://doi.org/10.1109/ICDE.2005.1

---

**Nota sobre fuentes**: Este artículo combina fuentes primarias de la literatura de sistemas de bases de datos (Codd, Chamberlin y Boyce, Stonebraker) con literatura sobre publicación científica abierta (Wilkinson et al., Becerril-García y Aguado-López, Babini y Rovelli) y documentación técnica de las infraestructuras relevantes para el ecosistema editorial latinoamericano (PKP, DataCite, OpenAlex). Las referencias a sistemas específicos (PostgreSQL, SQLite, MongoDB, Redis) se basan en su documentación oficial disponible en línea. Las afirmaciones sobre tendencias actuales en IA y datos vectoriales se apoyan en literatura académica reciente y se presentan como perspectivas en desarrollo, no como afirmaciones consolidadas.
