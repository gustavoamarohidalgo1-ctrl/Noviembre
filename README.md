# Noviembre

Aplicación Android de lectura bíblica en español, desarrollada con Kotlin y Jetpack Compose. Incluye el plan de noviembre: 30 días con tres lecturas diarias, 90 pasajes en total, disponibles sin conexión.

## Versión actual

- Nombre de la aplicación: **Mes de Noviembre**.
- Identificador Android: `com.example.appbiblialeeer.noviembre`.
- Versión: **1.0.1** (`versionCode = 2`).
- Android mínimo: API 25.

El identificador permite instalarla junto a la aplicación de septiembre, con progreso independiente. La app guarda las lecturas completadas y la posición de lectura.

## Textos y plan

El plan está en `app/src/main/java/com/example/appbiblialeeer/data/BiblePlan.kt`. El día 12 usa `Filemón 1` para representar el libro completo, de un solo capítulo.

Los 66 libros originales se conservan en `app/src/main/assets/origen/`. El APK empaqueta únicamente los 12 libros utilizados en noviembre, definidos en `packagedBibleBooks` dentro de `app/build.gradle.kts`. Una prueba comprueba que esa selección coincida con los libros requeridos por el plan.

La versión 1.0.1 reduce el tamaño del APK sin eliminar ninguna de las 90 lecturas del mes. Esta reducción no constituye una corrección confirmada de demoras de instalación en dispositivos concretos.

## Compilar y comprobar

Abre la raíz del proyecto en Android Studio, o utiliza el Gradle Wrapper incluido. Para reproducir el entorno de compilación utilizado, configura JDK 21 y Android SDK con la plataforma API 35 y Build Tools 36.0.0. Indica la ubicación del SDK mediante `ANDROID_HOME` o `sdk.dir` en un archivo local `local.properties`.

En macOS o Linux:

```sh
./gradlew :app:testDebugUnitTest :app:lintDebug :app:assembleRelease
```

En Windows, utiliza `gradlew.bat` con las mismas tareas. El APK se genera en:

```text
app/build/outputs/apk/release/app-release.apk
```

Las pruebas comprueban el procesamiento de los textos, las referencias del plan, los libros seleccionados para el APK y la cobertura de caracteres de las fuentes.

## Firma e instalación

La configuración actual firma `release` con la clave de depuración local para instalación directa. Las claves privadas no se incluyen en el repositorio. Para actualizar una instalación existente conservando sus datos, el nuevo APK debe usar el mismo identificador y certificado de firma. Un APK compilado en otro equipo puede utilizar una clave diferente.

Para distribuir una versión de producción, configura una clave de firma propia y revisa los requisitos del canal de distribución.
