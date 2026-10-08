# BJUP Iluminación

Catálogo estático de demostración con seis productos, filtros, búsqueda, selección de cantidades y temperaturas, cálculo ilustrativo por volumen y una escena animada al desplazarse. HTML, CSS y JavaScript sin dependencias de instalación.

Destino temporal previsto: `bjup.sin-yolanda.com`. El repositorio previsto sigue siendo `despertar-tec-digital-ia/bjup`. Este paquete no configura dominio ni publica el sitio.

## Uso local

Requiere Node.js 18 o posterior y, para este ejemplo de servidor, Python 3:

```sh
node scripts/build.mjs
python3 -m http.server 8080 --directory dist
```

Abrir `http://localhost:8080`. Las rutas de recursos son absolutas desde `/`; desplegar en la raíz del dominio, no en una subcarpeta. No abrir directamente como `file://`.

## Archivos

- `public/`: todo el sitio y sus cuatro imágenes.
- `scripts/build.mjs`: copia únicamente `public/` a `dist/`.
- `DEPLOY.md`: configuración prevista de GitHub y Cloudflare Pages.

## Alcance de esta demo

El formulario genera un resumen solamente en el navegador. No envía leads, mensajes ni pagos y no reserva mercancía. Probar con datos ficticios. El botón de copiar solo escribe el resumen en el portapapeles al pulsarlo. La selección se pierde al recargar.

Los precios, la moneda, los impuestos, el umbral de volumen, las existencias y las condiciones necesitan validación antes de un lanzamiento comercial. Algunas fotografías representan una familia de productos; el plafón conserva un marcador explícito por falta de foto. La escena ambiental es una imagen generada.

No se incluyen credenciales, historial Git, identidad de Sites, servicios de formularios ni herramientas de desarrollo de terceros. No hay integración de despliegue automático configurada en estos archivos.

**Privacidad del despliegue:** un repositorio privado no hace privado el sitio desplegado. La etiqueta «PROPUESTA PRIVADA» es contenido visual y no un control de acceso. Antes de publicar una revisión privada en Pages, confirmar si se necesita acceso restringido.

## Tipografía externa

El CSS conserva las importaciones originales de STIX Two Text, DM Sans y Manrope desde Google Fonts. Requiere conexión y genera solicitudes de fuente a Google; no transmite los campos del formulario. El resto de los recursos visuales está incluido. Las familias de reserva del CSS se usan si la fuente no está disponible.
