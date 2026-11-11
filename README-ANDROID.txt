# JRG · Mi Control Financiero — proyecto Android

La aplicación original se conserva dentro de `www/`. Se agregó identidad visual JRG,
icono, manifiesto y caché offline. Los datos continúan guardándose localmente en el
dispositivo mediante localStorage, igual que en la versión HTML.

## Generar la aplicación Android (APK)

Necesitas Node.js LTS, Android Studio y Android SDK.

1. Descomprime esta carpeta.
2. Abre una terminal dentro de esta carpeta.
3. Ejecuta:

   ```bash
   npm install
   npx cap add android
   npx cap sync android
   npx cap open android
   ```

4. En Android Studio espera a que termine la sincronización de Gradle.
5. Para generar un APK de prueba: **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
6. Android Studio mostrará la ubicación del APK generado. Para distribuirlo en Google Play
   necesitarás crear una versión firmada desde **Build → Generate Signed Bundle / APK**.

## Importante
- Este paquete es el proyecto fuente listo para envolver la app con Capacitor; no es todavía
  un APK firmado.
- La aplicación no sube tus datos financieros a un servidor: conserva el almacenamiento
  local del HTML original. Si borras los datos de la app o desinstalas, puedes perderlos.
  Usa **Configuración → Respaldo de información** para exportar copias periódicamente.
- Para importar tickets desde archivos JSON, sigue usando la sección Tickets de la app.


## Opción de generar el APK en la nube (sin instalar Android Studio)

Se incluye el flujo `.github/workflows/android-apk.yml`.

1. Crea una cuenta en GitHub si todavía no tienes una.
2. Crea un repositorio nuevo y sube el contenido de esta carpeta (incluida la carpeta oculta `.github`).
3. En el repositorio abre **Actions**.
4. Selecciona **Construir APK Android** y pulsa **Run workflow**.
5. Cuando termine correctamente, abre la ejecución y descarga el artefacto
   **JRG-Mi-Control-Financiero-APK**. Dentro estará `app-debug.apk`.
6. Pasa el APK al teléfono Android, ábrelo y permite la instalación desde esa fuente
   si Android lo solicita.

Este flujo produce un APK de depuración instalable para pruebas; no es una versión
firmada para publicar en Google Play.
