# Lector de tarjetas (NFC / EMV)

App Android propia para leer **tus** tarjetas contactless, sin depender de apps de terceros.

## Qué hace
- Lee por NFC el número (PAN), la fecha de vencimiento y, si la tarjeta lo entrega, el titular.
- Muestra el número **enmascarado**; un botón lo revela.
- No puede leer CVV ni PIN: no existen en el canal NFC.

## Por qué es seguro
- **Sin permiso de INTERNET** (ver `AndroidManifest.xml`): la app no puede enviar nada fuera del teléfono.
- **Sin almacenamiento**: nada se guarda; los datos se borran al salir de la app.
- **FLAG_SECURE**: bloquea capturas de pantalla y la vista previa en apps recientes.
- **Sin dependencias externas**: solo la API nativa de Android. Todo el código está en 3 archivos Kotlin que puedes leer completos.
- Copias de seguridad desactivadas (`allowBackup=false`).

## Cómo obtener el APK (sin Android Studio)
1. Crea un repositorio **privado** en GitHub.
2. Sube **todo el contenido** de esta carpeta (descomprimida), incluida la carpeta oculta `.github`.
   - Si `.github/workflows/build.yml` no se sube, créalo con *Add file → Create new file*, escribe esa ruta como nombre y pega el contenido.
3. Ve a la pestaña **Actions → Compilar APK → Run workflow** (también corre solo al subir a `main`).
4. Cuando termine (unos 3-5 minutos), entra a la ejecución y descarga el artefacto **lector-tarjetas-apk**.
5. Descomprime el `.zip` descargado, pasa `app-debug.apk` al teléfono e instálalo (hay que permitir "instalar apps de esta fuente").

## Uso
Abre la app, acerca la tarjeta a la parte trasera del teléfono (cerca de la cámara o el centro) y manténla quieta un par de segundos.

## Si algo falla
- *"No entrega el número por NFC"*: muchas tarjetas protegen el PAN. No se arregla con código.
- *"La tarjeta rechazó la lectura"*: algunas exigen parámetros distintos en `buildPdolData` (archivo `EmvReader.kt`).
- Si la compilación falla en GitHub Actions, copia el error del log y se corrige.

## Uso responsable
Úsala solo con tus propias tarjetas.
