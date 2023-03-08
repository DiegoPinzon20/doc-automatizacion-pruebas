<a target="_blank" href="https://www.youtube.com/@reliquiasdelsoftware">
    <img alt="Logo Reliquias del Software" src="images/logo.png" width="105" height="150">
</a>
<div>
<a href="https://www.youtube.com/@reliquiasdelsoftware" target="_blank">
  <img src="https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white">
</a>

# Documentación automatizacion de pruebas de softaware

Este repositorio contiene información clave para iniciar con la autonomization de pruebas de software usando Java,
[Serenity BDD](https://serenity-bdd.github.io/docs/guide/user_guide_intro) y Cucumber. Además encontrarás detalles de implementación usando patrones de diseño POM y Screenplay. El
enfoque son pruebas web y API.

## Tabla de contenidos
1. [Pre-requisitos](#pre-requisitos)
2. [Gestor de dependencias](#gestor-de-dependencias)
3. [Estructura base del proyecto](#estructura-base-del-proyecto)
4. [Patrones de diseño](#patrones-de-diseño)
5. [Autor](#autor)
6. [Copyright](#copyright)

## Pre-requisitos
- [Java](https://www.oracle.com/java/technologies/downloads/archive/): Tener instalado el JDK de java en su versión mínima de 8 o superior.
- [Variables de entorno](): Configurar las variables de entorno para Java y el gestor de dependecias (Gradle o maven).
- [IDE](): Tener instalado un entorno de desarrollo para proyectos Java como [Eclipse](https://www.eclipse.org/downloads/) o [IntelliJ IDEA](https://www.jetbrains.com/es-es/idea/). Se recomienda el uso de este último.
- [Plugins](): Instalar en su entorno de desarrollo los siguientes complementos:
  - Gherkin
  - Cucumber for Java
  - Lombok
  - Sonarlint

## Gestor de dependencias
Para administrar las dependencias de tu proyecto de automatización puedes utilizar:
- [Maven](https://maven.apache.org/): Se trata de un archivo llamado `pom.xml`, donde se utilizan etiquetas XML para agregar dependecias, complementos y demás configuración requerida. A continuación, se muestra un ejemplo:
  <br>
  <img alt="Archivo base POM" src="images/pomBaseMaven.png" width="450" height="110">
- [Gradle](https://gradle.org/): Gradle por su parte centra la información en un archivo llamado `build.gradle`, donde puede utilizarse lenguaje Groovy o Klotin para agregar las dependencias, plugins y otras configuraciones del proyecto.
  <img alt="Logo Reliquias del Software" src="images/buildBaseGradle.png" width="450" height="650">

Para efectos de este instructivo se utilizará como administrador de dependencias Gradle.

## Estructura base del proyecto

Para iniciar un proyecto de automatización se deben tener una estructura básica de archivos dentro de un proyecto base
de java.

<img alt="Archivos base para proyecto automatización" src="images/archivos_base.png" width="562" height="450">

Los archivos adicionales que deben acompañar el proyecto son:

- [serenity.conf]() - En este archivo podemos configurar todo lo relacionado con el navegador que queremos usar para
  ejecutar nuestras pruebas web, además de indicar
  las [capabilities](https://serenity-bdd.github.io/docs/guide/driver_config) del navegador. Entre otras cosas se
  encuentra:
    - Configurar si deseas usar un binario o drive para una versión especifica del navegador. En las versiones recientes
      de Serenity puedes olvidarte de descargar el binario y que el core gestione la descarga automatica del driver para
      ejecutar las pruebas. Esto último es lo más recomendable por temas de mantenibilidad.
    - Configurar si queremos que el navegador se ejecute en segundo plano o si quieres ver lo que está haciendo.
    - Indicarle a Serenity que tome capturas por cada paso, cada acción, etc.
    - Configurar los diferentes entornos que podemos necesitar para ejecutar nuestras pruebas. Ambientes como QA, UAT,
      DEV o default.
- [logback-test.xml]() - Este archivo permite que el core de Serenity BDD muestre la información en consola de las
  acciones que se realizan, además este archivo permite utilizarse para implementar nuestros logs
  usando [logback](https://logback.qos.ch/index.html).
- [.gitignore]() - Archivo que le indica a git que cambios debe ignorar y no se deben subir al repositorio. En este
  archivo se le indica que ignore el folder `target` por ejemplo, que es donde se almacenan los reportes de serenity.
- [serenity.properties]() - Archivo para indicarle a Serenity donde encontrar los `tests` del proyecto, configurar
  información adicional que se quiere mostrar en el reporte.

## Patrones de diseño

- [Page Object Model (POM)](): POM es un patrón donde se modelan las páginas webs como objetos, para realizar la automatización 
de las pruebas a través de pasos compuestos por interacciones. Este mismo enfoque se aplica para pruebas de servicios. Lo que distingue
este patrón es la forma en que se organiza el proyecto y el enfoque que se le da a los flujos. Cada página web es independiente con sus elementos
mapeados y sus respectivas interacciones. Una interacción puede ser ingresar un valor en un campo o completar un formulario, también puedes a través
de interacciones preguntar por el estado del sistema, si se levantó el mensaje esperado, etc.
  
  A continuación, se muestra la estructura es forma más básica un proyecto de automatización en Java aplicando el patrón:
  
  Es importante mencionar que para automatizar pruebas de aceptación usando este patrón y Serenity BDD, no es necesario agregar las dependencias
  de Screenplay(`serenity-screenplay`) en el archivo de administración de dependencias de su gestor del proyecto.

- [Screenplay](): Screenplay es la evolución del patrón POM, donde se le ha cambiado totalmente el enfoque de las pruebas de aceptación que se automatizan.
  Con este patrón la prueba ya no se centra en páginas e interacciones sino en el comportamiento del usuario al interactuar con el Sistema Bajo Prueba (SUT).
  Se introdujo el término `Actor` para hacer referencia al usuario, este actor puede tener diferentes habilidades que le permiten hacer acciones, entre las más básicas se encuentran:
  - Preguntar: Para saber cuál es el estado del sistema bajo prueba.
  - Realizar tareas: Para llevar a cabo la prueba en sí. Para realizar estas tareas el actor debe interactuar con el sistema.
  - Dependiendo de las habilidades asignadas al actor, este puede realizar diferentes acciones como consumir una API.
  
  Un proyecto base de Screenplay tiene la siguiente estructura para un proyecto realizado en Java: 
  <br>
  <img alt="Proyecto base usando Screenplay" src="images/screenplay-base.png" width="450" height="550">
  <br>
  Recuerde que para hacer uso de la implementación de Serenity para Screenplay debe incluir las dependencias correspondientes(`serenity-screenplay`). 

## Autor

[![Information](https://github-stats-alpha.vercel.app/api?username=DiegoPinzon20 "Information")](https://github-stats-alpha.vercel.app/api?username=DiegoPinzon20 "Information")

## Copyright
Publicado bajo la Licencia MIT, ver el
archivo [LICENSE](https://github.com/DiegoPinzon20/doc-automatizacion-pruebas/blob/master/LICENSE).
