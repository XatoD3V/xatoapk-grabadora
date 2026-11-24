# XatoRecord Pantalla 0.3 — Blanco y negro

## Cambios de esta entrega
- Fondo claro, tarjetas blancas con bordes y sombras suaves, botones negros, menú lateral y navegación inferior monocromáticos.
- La imagen de fantasma enviada por el usuario se incorpora sin alterar el archivo original como icono adaptativo del lanzador, marca en la app y control flotante predeterminado. El encuadre se realiza mediante recursos Android.
- Flotante arrastrable, controles de pausa/reanudar/detener rediseñados, opción Mostrar al grabar, imagen propia, tamaños y transparencia. Se muestra durante la grabación si tiene permiso.
- Icono de notificación monocromático independiente para mantener legibilidad.
- Referencia GenScreenRecX: inspección estática del APK y de sus nombres de recursos/textos de grabación, ajustes y superposición; no se ejecutó ni se copió su código.

Para ver el fantasma en el flotante si antes elegiste otra imagen, pulsa Flotante → Restaurar icono Xato.

Verificación: sintaxis Java, XML, referencias de recursos e integridad del archivo original. Falta compilar el APK en Actions y validar el diseño y las funciones en el celular.

# Rediseño 0.3 — XatoRecord Pantalla

Nueva interfaz: tarjetas con bordes y sombras, fondo claro, contraste blanco y negro, iconos vectoriales, menú lateral animado, navegación inferior y secciones independientes. Vista previa de imagen, tamaño y opacidad del flotante. Sin dependencias adicionales.

## Actualizar tu repositorio existente
1. Descomprime este ZIP.
2. En GitHub → Code → Add file → Upload files, sube el contenido de la carpeta XatoRecord a la raíz del repositorio, reemplazando los archivos existentes. No subas el ZIP ni una carpeta XatoRecord adicional.
3. Si Windows no muestra .github, no es necesario reemplazarla si ya tienes el workflow corregido. Este ZIP también contiene la corrección setup-android@v4.
4. Confirma los cambios. Actions generará un nuevo APK. Descárgalo desde Artifacts e instálalo como actualización.
5. Si Android rechaza la actualización por firma diferente, la compilación debug anterior pudo usar otra clave. No desinstales sin revisar qué datos necesitas conservar. Para futuras actualizaciones utiliza una clave de firma estable.

Los archivos principales del rediseño son app/src/main/java/com/xato/record/MainActivity.java y app/build.gradle. El motor de grabación conserva su implementación. Se verificó la sintaxis Java y XML localmente; no se compiló ni se probó visualmente en Android en este entorno. Revisa distribución, permisos y grabación en tu teléfono.

---

# XatoRecord Pantalla — 0.3.0
Proyecto Android nativo Java, Android 10 o superior. Primera implementación; requiere compilación y pruebas en dispositivo antes de considerarse lista para uso habitual.

## Incluido
- MP4 H.264, 480p/720p/1080p máximos de lado corto, 24/30/60 FPS y 2/4/8/12 Mbps.
- Vídeo sin sonido o micrófono AAC. Pausa, reanudar y detener desde app, notificación o botón flotante.
- Botón arrastrable, imagen local propia reducida a 192x192, tres tamaños y tres opacidades.
- Guardado con MediaStore en Movies/XatoRecord, sin permiso de almacenamiento general.
- Sin publicidad, seguimiento, permiso de Internet ni dependencias de interfaz externas.
- Tema blanco y negro. Peso final pendiente de compilar y medir; tamaño del ZIP no equivale al APK.

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
