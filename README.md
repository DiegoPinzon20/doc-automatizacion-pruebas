<a target="_blank" href="https://www.youtube.com/@reliquiasdelsoftware">
  <p style="text-align:center;">
    <img alt="Logo Reliquias del Software" src="images/logo.png" width="150" height="200">
  </p>
</a>

# Documentación automatizacion de pruebas de softaware

Este repositorio contiene información clave para iniciar con la automatizacion de pruebas de software usando Java,
Serenity BDD y Cucumber. Además encontrarás detalles de implementación usando patrones de diseño POM y Screenplay. El
enfoque son pruebas web y API.

## Tabla de contenidos

## Gestor de dependecias

## Estructura base del proyecto

Para iniciar un proyecto de automatización se deben tener una estructura básica de archivos dentro de un proyecto base
de java.

<img alt="Logo Reliquias del Software" src="images/archivos_base.png" width="562" height="450">

Los archivos adicionales que deben acompañar el proyecto son:

- [serenity.conf]() - En este archivo podemos configurar todo lo relacionado con el navegador que queremos usar para
  ejecutar nuestras pruebas web, además de indicar
  las [capabilities](https://serenity-bdd.github.io/docs/guide/driver_config) del navegador. Entre otras cosas se
  encuentra:
    - Configurar si deseas usar un binario o drive para una versión especifica del navegador. En las versiones recientes
      de Serenity puedes olvidarte de descargar el binario y que el core gestione la descarga automatica del driver para
      ejecutar las pruebas. Esto último es lo mas recomendable por temas de mantenibilidad.
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

- [Page Object Model (POM)]():
- [Screenplay]():

## Autor 👨 ([emoji key](https://allcontributors.org/docs/en/emoji-key))

[![Information](https://github-stats-alpha.vercel.app/api?username=DiegoPinzon20 "Information")](https://github-stats-alpha.vercel.app/api?username=DiegoPinzon20 "Information")

## Copyright

Publicado bajo la Licencia MIT, ver el
archivo [LICENSE](https://github.com/DiegoPinzon20/doc-automatizacion-pruebas/blob/master/LICENSE).
