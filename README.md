# Directus ![Directus](https://img.shields.io/badge/directus-%2364f.svg?style=for-the-badge&logo=directus&logoColor=white) 

**Directus** es un CMS que nos permite crear contenidos y una estructura y base de datos para luego exponer toda esa arquitectura mediante su API y así poder conectarlo con otras tecnologías y aplicaciones. Al ser un Headless CMS implica que la capa de presentación es independiente de la base de datos y de la lógica del proyecto. 

El objetivo de este estudio es analizar la viabilidad de usar Directus como CMS para futuros proyectos desde el punto de vista del **perfil frontend**. Para realizar un testeo exhaustivo, se desarrollarán varias aplicaciones sencillas y se analizará el acoplamiento de ambas partes (front y back).

> **NOTA:** Las aplicaciones serán implementadas por un único desarrollador fronted. Se aprovecharán los desarrollos para analizar la herramienta, de manera superficial, desde el punto de vista de otros perfiles implicados en el proceso.

## Primeros pasos

### Requisitos

Directus solo requiere Node.js y es compatible con la mayoría de los sistemas operativos y proveedores de bases de datos SQL.

- Node.js 12.20+
- npm 6.x+

**Bases de datos compatibles**

- PostgreSQL 10+
- MySQL 5.7.8+
- MariaDB 10.2+
- SQLite 3+
- MS-SQL X.X+
- OracleDB X.X+

### Instalación

#### Directus

Instalar con npm:

```console
npm init directus-project <nombre del directorio de la api>
```

Si da error de instalación instalar el módulo que falta:

```console
npm i @napi-rs/snappy-win32-x64-msvc
```

Durante el proceso de instalación seleccionar la base de datos deseada y las credenciales de administración.

Lanzar la aplicación:

```console
cd <ruta del directorio de la api>
npx directus start
```

Servidor lanzado en: http://localhost:8055

### Actualización

#### Directus

Introducir la versión actual en el archivo `package.json` para actualizar el proyecto a la última versión de Directus:

```console
{
  "dependencies": {
    "directus": "x.x.x"
  }
}
```

Ejecutar:

```console
cd <ruta del directorio de la aplicación>
npx install
```

#### Base de datos

Actualizar la base de datos si la hemos manipulado manualmente, para que Directus integre los cambios:

```console
cd <ruta del directorio de la aplicación>
npx directus database migrate:latest
```

## Testing

### Análisis en base a perfiles

#### Gestor de bases de datos

Análisis de los siguientes items en cuanto a la creación y gestión de modelos de datos en Directus:

| Testing | Valoración  | Comentarios |
| ------------- | ------------- | ------------- |
| `Interfaz`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | Interfaz de usuario amigable y atractiva. |
| `Robusted`  | <span style=" text-align: center; padding: 5px; background-color: 	#ffa500; color: #fff;">ACEPTABLE</span>  | Con la llegada de la versión 9 se ha ganado en consistencia, pero aún así se han detectado errores de implementación.  |
| `Configuración`  | <span style=" text-align: center; padding: 5px; background-color: 	#ffa500; color: #fff;">ACEPTABLE</span>  | Capacidad elevada de configuración, aunque se requiere cierta experiencia técnica.  |
| `Tiempo`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | En pocos minutos puedes tener creada y configurada una base de datos de complejidad media.  |
| `Capacitación`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | Para crear modelos de datos de complejidad media no se requieren grandes conocimientos de programación.  |
| `Codificación`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | El modelo de datos se puede crear en su totalidad a través de la interfaz de la herramienta.  |
| `Adaptabilidad`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span>  | Posibilidad de reutilizar una base de datos existente. Permite cambios funcionales. |
| `Escalabilidad`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span>  | Posibilidad de alojamiento en la nube, por lo que se pueden aumentar los recursos en función de las necesidades.  |
| `Flexibilidad`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span>  | Los datos se almacenan en una base de datos personalizada y se pueden migrar, exportar o hacer una copia de seguridad en cualquier momento.  |
| `Integridad`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">NOTABLE</span>  | Permite el acceso concurrente de usuarios.  |
| `Seguridad`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">NOTABLE</span>  | Incorpora soluciones para evitar brechas de seguridad o pérdidad de información pero no son lo suficientemente robustas. Desde la base de datos no se puede acceder al entorno de desarrollo por lo que se evitarán ataques de malware.  |
| `Restricciones`  | <span style=" text-align: center; padding: 5px; background-color: 	#ffa500; color: #fff;">ACEPTABLE</span>  | Es compatible únicamente con bases de datos relacionales.|

#### Gestor de contenidos

Análisis los siguientes items en cuanto a la gestión de la información en Directus:

| Testing | Valoración  | Comentarios |
| ------------- | ------------- | ------------- |
| `Interfaz`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | La usabilidad y experiencia de usuario es magnífica. Interfaz muy limpia e intuitiva. Ofrece multitud de opciones. |
| `Sencillez`  | <span style=" text-align: center; padding: 5px; background-color: 	#ffa500; color: #fff;">ACEPTABLE</span>  | La complejidad inicial radica en enfrentarse a un nuevo paradigma en cuanto a gestión del contenido se refiere, ya que la herramienta ofrece una estructura pura de presentación y organización de la información. Asumiendo ese cambio, es realmente sencillo agregar contenido a la aplicación.   |
| `Tiempo`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | En pocos minutos puedes tener alojado todo el contenido de la aplicación. Es un proceso ágil y rápido.  |
| `Internalización`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | La necesidad de crear sitios multi lenguaje, requiere sencillez y agilidad en el proceso. Directus está preparado para dar soporte a varios idiomas de manera rápida y sin complejidad.  |
| `Codificación`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | No se requieren conocimientos de programación o diseño web para gestionar el contenido.  |
| `Organización`  | <span style=" text-align: center; padding: 5px; background-color: 	#cb3234; color: #fff;">DEFICIENTE</span>  | Al no disponer de páginas, ni sitemaps para guiarse, hay que adaptarse a la forma "pura" en que está organizado el contenido, independientemente del sitio web. |
| `Restricciones`  | <span style=" text-align: center; padding: 5px; background-color: 	#cb3234; color: #fff;">DEFICIENTE</span>  | No permite la previsualización de los contenidos. Limitada capacidad para personalizar los datos. Al ser un sistema agnóstico, no entiende de plantillas, capas de presentación ni diseño. |

#### Frontend

Análisis los siguientes items en cuanto al desarrollo frontend en Directus:

| Testing | Valoración  | Comentarios |
| ------------- | ------------- | ------------- |
| `Rendimiento`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | Al hacer uso de APIs únicamente obtenemos el contenido necesario, minimizando así la carga. De esta manera, las páginas cargan en la mitad de tiempo usando los mismos recursos del servidor, lo que se traduce en una mejor experiencia de usuario. |
| `Escalabilidad`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span>  | La separación de la parte frontend del backend posibilita una mayor personalización, escalabilidad y la opción de incluir actualizaciones sin que el funcionamiento ni la usabilidad se vean afectadas.   |
| `Flexibilidad`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span>  | Amplia flexibilidad tanto en la reutilización de los componentes/contenido, como en el uso de frameworks o lenguajes del lado del cliente.   |
| `Integración`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | Se integra de forma fácil con nuevas tecnologías e innovaciones. Está preparado para el futuro al ser una teconología capaz de evolucionar rápidamente.  |
| `SEO`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">NOTABLE</span> | Alta capacidad para editar los metadatos y para modificar el contenido según el dispositivo. Al tratar el SEO como datos, nos da un control completo para definir las diferentes estrategias y soluciones. Una configuración correcta puede resultar algo compleja ya que es necesario una implementación técnica sólida.  |
| `Multicanal`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | La capacidad de entregar contenido a través de múltiples canales lo convierte en una herramienta poderosa. La compatibilidad es mucho más amplia.  |
| `Acceso a datos`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | Ofrece un amplio abanico de tecnologías para la petición de datos (API Rest, GraphQL, SDK o SQL queries).  |
| `Filtrado`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | Ofrece un potente filtrado para hacer solicitudes o paginación.  |
| `Datos dinámicos`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span> | No es necesario recargar una página para ver nuevos contenidos. La API entrega datos dinámicos sin necesidad de volverlos a cargar.  |
| `JSON`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span>  | Está preparado para recibir información vía JSON, lo que facilita la importación de datos de forma limpia y utilizando sólo la información que necesitamos. |
| `Restricciones`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span>  | El diseño web no está sujeto a las limitaciones de cada CMS. Mayor libertad creativa para desarrolladores y diseñadores. |

#### Backend

Análisis los siguientes items en cuanto al desarrollo backend en Directus:

| Testing | Valoración  | Comentarios |
| ------------- | ------------- | ------------- |
| `Acceso a datos`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span>  | Permite crear nuevos Endpoints o adaptarse a las peticiones API. |
| `Almacenamiento`  | <span style=" text-align: center; padding: 5px; background-color: 	#cb3234; color: #fff;">DEFICIENTE</span>  | Se han detectado ciertos problemas para la recuperación de los metadatos de los ficheros almacenados en el S3 de Amazon. |
| `Personalización`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span>  | Proporciona un conjunto de herramientas rico en funciones, para configurar la lógica de backend |
| `Extensibilidad`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span>  | Permite adaptar las aplicaciones sin limitaciones a través de ganchos de integración, flujos de trabajo de automatización, transformaciones de datos, plugins, alertas o eventos. |
| `Escalabilidad`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span>  | Existe la posibilidad de escalar toda la infraestructura a medida que el volumen de contenido crece. |
| `Costes`  | <span style=" text-align: center; padding: 5px; background-color: 	#cb3234; color: #fff;">DEFICIENTE</span>  | Escasez de características integradas, ya que no siempre tiene incorporado todo lo que se necesita. Esto implica tener que implementar la funcionalidad, lo que eleva los costes de producción. |
| `Documentación`  | <span style=" text-align: center; padding: 5px; background-color: 	#cb3234; color: #fff;">DEFICIENTE</span>  | Documentación muy escasa y pobre para la implementación de interfaces y extensiones y gran complejidad en sus detalles técnicos. |
| `Comunidad activa`  | <span style=" text-align: center; padding: 5px; background-color: 	#3CB371; color: #fff;">EXCELENTE</span>  | Es un CMS ampliamente usado y soportado. Tiene muchos colaboradores, lo que garantiza una resolución rápida de problemas y un mantenimiento frecuente. |
| `Restricciones`  | <span style=" text-align: center; padding: 5px; background-color: 	#ffa500; color: #fff;">ACEPTABLE</span>  | Para la implementación de ciertas extensiones como interfaces, layouts o módulos es necesario dominar el framework Vue.js, ya que la interfaz de Directus está escrita en este lenguaje. |

### Conclusiones generales

#### Aspectos positivos

-  **Rendimiento:** Al hacer uso de APIs únicamente obtenemos el contenido necesario, minimizando así la carga. De esta manera, las páginas cargan en la mitad de tiempo usando los mismos recursos del servidor. Páginas más rápidas se traducen en una mejor experiencia de usuario y un mejor SEO. 
-  **Eficiencia y tiempos:** Directus da lugar a un trabajo ágil y una gestión del tiempo más eficiente, debido a que prácticamente todos los equipos involucrados (como pueden ser backend, frontend, desarrollo de contenidos, etc.) tienen la capacidad de trabajar al mismo tiempo, de manera que la entrega y el lanzamiento del proyecto reduce notablemente su tiempo de entrega. 
-  **Actuación:** Ofrece métodos de renderizado como SSR (Representación del lado del servidor) y SSG (Generación de sitios estáticos) que ayudan a mejorar el rendimiento de la página y los tiempos de carga.
-  **Optimización:** Al separar backend y frontend, el trabajo se hace más independiente y se puede contar con desarrolladores específicos para cada área. Incluir distintos perfiles especializados es vital para lograr unos resultados idóneos siempre que el trabajo en equipo sea coherente y coordinado.
-  **Código abierto y gratuito:** Al ser completamente de código abierto, modular y extensible, Directus se puede adaptar completamente a los requisitos de cualquier proyecto.
-  **Gestión de usuarios y permisos:** Directus posee un módulo de administración de usuarios con permisos granulares y múltiples integraciones de inicio de sesión, incluido el de inicio de sesión único.
-  **Almacenamiento:** Directus admite una amplia gama de bases de datos SQL. Nuestras bases de datos no necesitan estar vacías a la hora de instalar Directus.
-  **Imágenes y documentos:** El almacenamiento físico usa UUID en nombres de archivos para evitar colisiones. De forma predeterminada se almacenan de forma local, pero se puede usar AWS S3, Google Cloud Storage o conectar con uno propio.
-  **Datos dinámicos:** Todos los datos están disponibles a través de la API REST y/o GraphQl que se rigen por la gestión de usuarios y los permisos. Se entregan sin necesidad de volverlos a cargar.
-  **Interfaz:** La interfaz de usuario es muy intuitiva y elegante y además proporciona multitud de opciones necesarias para los administradores de contenido. Cada campo se puede personalizar para adaptarlo a cualquier requisito y sino es así se puede hacer uso de sus extensiones. El panel informativo se puede personalizar para adaptarlo a las preferencias del usuario en cuanto a visualización de los datos.
-  **Seguridad:** Al no poder acceder al entorno de publicación de contenido desde la base de datos, se evitarán ataques de malware. Posibilidad de usar protocolos específicos de seguridad y servicios de autenticación.
-	 **Codificación:** Al ser un CMS agnóstico a la parte frontend no es necesario aprender lenguajes de desarrollo específicos. Además, los tiempos de desarrollo son más rápidos al poder probar varias hipótesis muy rápidamente.
-	 **Compatibilidad:** Es una herramienta compatible con multitud de tecnologías al poder entregar el contenido cuando se desee. Los datos se almacenan en su base de datos personalizada y se pueden migrar, exportar o hacer una copia de seguridad en cualquier momento.
-	 **Flexibilidad y libertad:** Aporta un plus de flexibilidad en tanto que se puede elegir el lenguaje de programación y el framework, eliminando gran parte de las limitaciones que existían con el modelo tradicional. Además, es posible utilizar contenidos similares en proyectos distintos, reutilizándolos con una exportación sencilla.
-  **Personalización**: Los desarrolladores pueden comunicarse a través de un API y formatos de datos (como JSON), lo que permite más opciones de personalización sin necesidad de aprender nuevos lenguajes de programación.
-	 **Extensible:** Todos los aspectos de la herramienta son modulares, lo que permite adaptar, personalizar y ampliar infinitamente el motor Core.
-	 **Escalabilidad:** La separación de backend y frontend posibilita una mayor personalización, escalabilidad y la opción de incluir actualizaciones sin que el funcionamiento ni la usabilidad se vean afectadas.
-  **Multicanal:** La posibilidad de servir contenido a varias webs a pesar de que estén en otro servidor, es de gran utilidad para facilitar la gestión de distintos proyectos utilizando una única interfaz administrativa.
-	 **Comunidad activa:** Significa que es un CMS ampliamente usado y soportado. Tiene muchos colaboradores, lo que garantiza una resolución rápida de problemas y un mantenimiento frecuente.

#### Aspectos negativos

-  **DevOps:** Se necesita un equipo de DevOps para administrar la estructura del contenido y para crear las interfaces que consumen ese contenido a través de los diferentes canales.
-	 **Errores:** Al ser código abierto y gratuito frecuentan los errores. Con la versión 9 se han revisado y corregido muchos de ellos y actualmente es algo más estable que antes, pero aun así la herramienta debería tener más consistencia. Las versiones se actualizan constantemente.
-  **Documentación:** Documentación muy escasa para la implementación de interfaces y extensiones y gran complejidad en sus detalles técnicos. 
-	 **Bases de datos:** Directus solo puede usar bases de datos relacionales.
-  **Costes:** Caro debido a los costos adicionales de implementación. Al poseer escasas características integradas, hay que implementar la funcionalidad, lo que eleva los costes de producción.
-  **Mantenimiento:** Requiere un equipo técnico. Mantenimiento realizado por el equipo del proveedor en la nube.
-  **Organización del contenido:** Al no disponer de páginas, ni sitemaps para guiarse, el gestor de contenidos tendrá que adaptarse a la forma "pura" en que está organizado el contenido, independientemente del sitio web.
-  **Restricciones del contenido:** Los gestores de contenido disponen de funciones más limitadas para gestionar y personalizar el contenido que si se usa un CMS tradicional. Al tener la parte de frontend desacoplada del CMS no existen las vistas previas de la información por lo que es más difícil editar esos datos. La herramienta no entiende de plantillas, capas de presentación ni diseño.
-  **Configuración**: Requiere cierta experiencia técnica.