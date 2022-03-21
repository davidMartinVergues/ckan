# CKAN

CKAN es una herramienta que permite hacer web sites de datos abiertos (como un sistema de administración de contenido como WordPress, pero para datos). 
Nos permite administrar y publicar colecciones de datos.

Una vez que se publican sus datos, los usuarios pueden usar sus funciones de búsqueda para navegar y encontrar los datos que necesitan y obtener una vista previa usando mapas, gráficos y tablas.

- ## ckan tech

CKAN se basa en un framework de Python llamado Pylons, que solo es compatible con Python 2.

En 2016, Open Knowledge Foundation comenzó a trabajar para cambiar el framework subyacente de CKAN a Flask, tanto para modernizar la base de código como para admitir Python 2 y Python 3. 

CKAN 2.9, es compatible con Python 2.7 y Python 3.6 o superior
CKAN 3.0 solo admitirá Python 3.



- ## Datasets and resources 

En CKAN los datos se publican en unidades denominadas "datasets". Un conjunto de datos es un paquete de datos; por ejemplo, podrían ser las estadísticas de delitos de una región. Cuando los usuarios buscan datos, los resultados de búsqueda que ven serán conjuntos de datos individuales.

Un dataset contiene dos cosas:

1. Información o “metadatos” sobre los datos. Por ejemplo, el título y el editor, la fecha, en qué formatos está disponible, bajo qué licencia se publica, etc.
   
2. Una serie de "resources", que contienen los datos en sí. No importa en qué formato están los datos. Un recurso puede ser una hoja de cálculo CSV o Excel, un archivo XML, un documento PDF, un archivo de imagen, datos vinculados en formato RDF, etc. CKAN puede almacenar el recurso internamente o almacenarlo simplemente como un enlace, el recurso en sí está en otra parte de la web. Un dataset puede contener cualquier número de resources. Por ejemplo, diferentes resources pueden contener los datos de diferentes años o pueden contener los mismos datos en diferentes formatos.

En las primeras versiones de CKAN, los conjuntos de datos se llamaban "paquetes" y este nombre se ha quedado en algunos lugares, especialmente internamente y en las llamadas a la API. Paquete tiene exactamente el mismo significado que "conjunto de datos".

- ## Users, organizations and authorization

Los usuarios de CKAN pueden registrar cuentas de usuario e iniciar sesión. Normalmente (dependiendo de la configuración del sitio), no es necesario iniciar sesión para buscar y encontrar datos, pero es necesario para todas las funciones de publicación: los usuarios pueden crear, editar, etc. siempre y caundo tengan los permisos apropiados.

Normalmente, cada conjunto de datos es propiedad de una "organización". Una instancia de CKAN puede tener cualquier número de organizaciones. Por ejemplo, si un gobierno nacional utiliza CKAN como un portal de datos, las organizaciones pueden ser diferentes departamentos gubernamentales, cada uno de los cuales publica datos. Cada organización puede tener su propio flujo de trabajo y autorizaciones, lo que le permite gestionar su propio proceso de publicación.

Los administradores de una organización pueden agregarle usuarios individuales, con diferentes funciones según el nivel de autorización necesario. Un usuario de una organización puede crear un conjunto de datos propiedad de esa organización. En la configuración predeterminada, este conjunto de datos es inicialmente privado y visible solo para otros usuarios de la misma organización. Cuando esté listo para su publicación, se puede publicar con solo presionar un botón. Esto puede requerir un nivel de autorización más alto dentro de la organización.

Los conjuntos de datos normalmente no se pueden crear excepto dentro de las organizaciones. Sin embargo, es posible configurar CKAN para permitir conjuntos de datos que no pertenecen a ninguna organización. Dichos conjuntos de datos pueden ser editados por cualquier usuario que haya iniciado sesión, lo que crea la posibilidad de un centro de datos similar a un wiki.

>Puedes probar una versión demo de ckan en el siguiente link [ckan demo](https://demo.ckan.org/)

By default CKAN allows members of organizations with three roles:

1. Member – can see the organization’s private datasets
2. Editor – can edit and publish datasets
3. Admin – can add, remove and change roles for organization members

- ## Installing CKAN 

Hay 3 maneras de instalar ckan:

1. [Install from an operating system package](http://docs.ckan.org/en/2.9/maintaining/installing/install-from-package.html)
2. [Install from source](http://docs.ckan.org/en/2.9/maintaining/installing/install-from-source.html)
3. [Install from Docker Compose](http://docs.ckan.org/en/2.9/maintaining/installing/install-from-docker-compose.html)

La manera más sencilla y limpia es instalarlo usando docker compose. Para no utilizar una versión diferente de la q usa desidedatum clonaremos el repo de [ckan-docker](https://github.com/desidedatum/ckan-docker) que es la imagen base de ckan que usaremos para todos los proyectos.

### INstalación con docker compose

0. debemos poder ejecutar docker sin sudo `sudo usermod -aG docker ${USER}` esto añade nuestro user al grupo `docker`
   
1. crear el directorio dnd clonaremos el repo 
   
2. `git clone git@github.com:desidedatum/ckan-docker.git`
   
3. Podemos bajar tb una version de ckan oficial (sin modificar) para ello `git clone https://github.com/ckan/ckan.git`
   
   1. si queremos usar una version en concreto hacemos un checkout al tag correspondiente `git checkout tags/ckan-2.9.2`
   
4. crear un archivo .env en la raíz del proyecto `cp .env-template .env`
   
5. dirigirme donde se encuentra el archivo `docker-compose.yml` y ejecutar
   ```
   docker-compose up -d --build
   ```
6. si da error de conexión con la bbdd ejecutar `docker-compose restart ckan` algunas veces
   
7. Para poder usar el ckan de desidedatum debo tener un usuario git que enga permisos para conectarse al repo de la empresa.

8. 







