# Backport de PepoMote Legacy para Android

Este fork es un **backport comunitario no oficial para Android, todavía en desarrollo**. Su objetivo es funcionar desde Android 4.4.4 KitKat (API 19) hasta Android 7.1.2 Nougat (API 25), en dispositivos de 32 bits `armeabi-v7a` y `x86`, y conectarse al **receptor vanilla de PepoMote para PC, sin modificarlo**.

Se pretende conservar la experiencia Android completa siempre que la plataforma antigua lo permita: emparejamiento por QR o manual, descubrimiento en la LAN, mando/Wiimote, Dolphin, Wii U/GamePad con segunda pantalla, Switch Pro, RetroArch, Nunchuk y Servidor Android. Las API exclusivas de Android 8 o posterior deben reemplazarse por equivalentes compatibles o aislarse con alternativas según la versión, no eliminar funciones sin más. Cámara, sensores, multicast Wi-Fi e integración con emuladores requieren pruebas en dispositivos reales.

## Estado de compatibilidad

El código Android original usa Jetpack Compose y AndroidX modernos. Cambiar solo `minSdk` no los vuelve compatibles con KitKat: todavía hace falta migrar la interfaz y dependencias y añadir los reemplazos de API correspondientes. No se debe considerar el repositorio ni el APK compatibles y validados para API 19–25 hasta superar la compilación Android y las pruebas en dispositivos físicos. Consulta la [auditoría del backport](ANDROID_API19_25_AUDIT.md) para el análisis por componentes y el plan.

## Compatibilidad con el receptor vanilla

El código del PC y el protocolo PMP v1 no se modifican para este backport. El cliente Android debe conservar el handshake/emparejamiento TCP con JSON por líneas y los formatos UDP PMP1 existentes, respetando cuándo se permiten paquetes extendidos según la capacidad confirmada. El receptor vanilla es la referencia: no se necesita un ejecutable de PC personalizado ni un handshake exclusivo del fork.

## Compilación

Las instrucciones definitivas se publicarán cuando estén migrados la UI y el toolchain antiguo. El objetivo es generar APK debug/release solo con ABI `armeabi-v7a` y `x86`, `minSdk 19` y `targetSdk 25`. La configuración Android moderna actual todavía no es una receta de compilación verificada para ese rango.

## Estado y atribución

Este es un fork comunitario no oficial de PepoMote; no está afiliado ni respaldado por PepoTech. Se conservan las especificaciones del protocolo y los vectores dorados originales como referencia de interoperabilidad. El backport Android no modifica el código fuente de las otras plataformas.
