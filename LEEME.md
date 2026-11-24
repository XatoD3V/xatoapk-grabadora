# XatoRecord Pantalla — 0.1.0
Proyecto Android nativo Java, Android 10 o superior. Primera implementación; requiere compilación y pruebas en dispositivo antes de considerarse lista para uso habitual.

## Incluido
- MP4 H.264, 480p/720p/1080p máximos de lado corto, 24/30/60 FPS y 2/4/8/12 Mbps.
- Vídeo sin sonido o micrófono AAC. Pausa, reanudar y detener desde app, notificación o botón flotante.
- Botón arrastrable, imagen local propia reducida a 192x192, tres tamaños y tres opacidades.
- Guardado con MediaStore en Movies/XatoRecord, sin permiso de almacenamiento general.
- Sin publicidad, seguimiento, permiso de Internet ni dependencias de interfaz externas.
- Tema oscuro y acento rojo. Peso final pendiente de compilar y medir; tamaño del ZIP no equivale al APK.

## Obtener el APK sin Android Studio
1. Crea un repositorio de GitHub y sube el CONTENIDO de esta carpeta a su raíz, incluyendo `.github/workflows/android.yml`.
2. En GitHub, abre Actions → Compilar APK XatoRecord. Si es necesario, habilita Actions.
3. Al terminar correctamente, abre esa ejecución y descarga el artefacto XatoRecord-Pantalla-APK.
4. Descomprime y transfiere app-debug.apk al celular. Permite la instalación desde la app que abre el APK.
El APK de depuración sirve para pruebas. Para distribución, genera una versión release firmada con una clave propia y conservada de forma segura. El proyecto no incluye claves.

## Android Studio
Abre esta carpeta, instala SDK 35, usa JDK 17 y Gradle 8.9. Si solicita Gradle, selecciona instalación local 8.9. No se incluye Gradle Wrapper binario. Sincroniza y usa Build → Generate Signed App Bundle / APK para una versión firmada. Por terminal, con Gradle 8.9 instalado: `gradle assembleDebug`.

## Uso
Configura calidad, activa micrófono si lo necesitas, permite superposición para el flotante, elige una imagen y pulsa Iniciar grabación. Concede los permisos y confirma la captura de Android. El permiso de superposición es opcional; la notificación ofrece controles. No hay inicio automático o captura oculta.

## Límites de esta versión
No incluye audio interno, mezcla de fuentes, cámara frontal, editor, streaming, cuenta regresiva o programación. No cambia la orientación durante una sesión: detén y vuelve a iniciar para cambiarla. La disponibilidad real de 60 FPS y 1080p depende del codificador y hardware. El sistema puede capturar el botón flotante. Contenido protegido puede salir negro. El sistema y el fabricante pueden interrumpir la sesión al bloquear pantalla o limitar procesos. Un cierre forzado o pérdida de energía puede dejar un vídeo pendiente o incompleto.

## Verificación pendiente en teléfono
- Compilar APK; instalar en Android 10 y Android 14/15.
- Probar captura con/sin micrófono y con permisos rechazados.
- Pausar/reanudar; finalizar desde las tres superficies; comprobar MP4 reproducible y audio sincronizado.
- Elegir imagen grande; reiniciar app; arrastrar flotante por bordes.
- Cancelar consentimiento, detener desde sistema, bloquear pantalla, retirar superposición y probar poco almacenamiento.
- Medir peso APK, FPS, consumo, temperatura y sesiones de 30 minutos.

## Referencias técnicas
https://developer.android.com/media/grow/media-projection
https://developer.android.com/develop/background-work/services/fgs/service-types
