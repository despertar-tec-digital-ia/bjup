# Despliegue previsto: GitHub + Cloudflare Pages

## Destinos

- Repositorio previsto: `despertar-tec-digital-ia/bjup`, privado por defecto.
- Proyecto: uno nuevo y separado para BJUP; no reutilizar el de otro negocio.
- Dominio temporal solicitado: `bjup.sin-yolanda.com`.

Este paquete no crea el repositorio, no instala aplicaciones, no publica y no cambia DNS.

## 1. Subir el código

En el repositorio nuevo, cargar el contenido de esta carpeta en la raíz: `public/`, `scripts/`, `README.md`, `DEPLOY.md` y `.gitignore`. Mantener las carpetas. Si se recibe un ZIP, descomprimirlo antes de cargar archivos por la interfaz de GitHub: subir el ZIP por sí solo no genera un árbol de código utilizable por Pages.

No subir `dist/`, `.git/`, `.openai/`, archivos `.env`, contraseñas ni tokens.

## 2. Elegir el modo de despliegue antes de crear el proyecto

La integración Git de Pages es la opción recomendada si se autorizan despliegues automáticos: permite desplegar al cambiar la rama de producción. Conectar GitHub puede requerir otorgar acceso persistente a Cloudflare. Antes de instalar o ampliar ese acceso, obtener autorización y limitarlo al repositorio BJUP cuando sea posible.

No se ha supuesto autorización para configurar esta integración. La alternativa es una carga manual de los archivos estáticos. Los modos de creación tienen restricciones de cambio: revisar la documentación oficial antes de elegir. En particular, un proyecto creado con integración Git no se puede convertir después a Direct Upload por el panel; la documentación permite desactivar despliegues automáticos y usar Wrangler.

### Configuración si se autoriza integración Git

- Framework: ninguno.
- Rama de producción: `main`.
- Directorio raíz: raíz del repositorio.
- Comando de compilación: `node scripts/build.mjs`.
- Directorio de salida: `dist`.
- Variables de entorno o secretos: ninguno necesario.
- Alternativa sin compilación: comando `exit 0`, salida `public`.

### Carga manual si se elige Direct Upload

Ejecutar `node scripts/build.mjs` y cargar únicamente el contenido de `dist/`, con `index.html` en la raíz de la carga. El paquete estático separado contiene esa estructura. No incluir README, documentación o scripts en el sitio publicado.

## 3. Dominio y verificación

Después de verificar el despliegue provisional, añadir `bjup.sin-yolanda.com` en Custom domains del proyecto BJUP. Revisar primero si ya existe un registro para ese nombre; no sobrescribir otro servicio sin resolver el conflicto.

Asociar el dominio en Pages antes de configurar un CNAME. Su destino debe ser el hostname `pages.dev` real que Cloudflare asigne al nuevo proyecto, no uno adivinado. Confirmar activación y HTTPS. No cambiar el dominio raíz ni otros subdominios.

Verificar imágenes, escena de scroll, modo de movimiento reducido, filtros, búsqueda, selección, precios a partir de diez piezas, cierre y reapertura de diálogos, y generación/copia del resumen de prueba. Comprobar consola y red. La demo debe seguir sin transmitir datos del formulario.

Un repositorio privado no protege el sitio publicado. Confirmar por separado cualquier necesidad de restricción de acceso.

## Referencias oficiales

Consultadas el 8 de octubre de 2026:

- HTML estático: https://developers.cloudflare.com/pages/framework-guides/deploy-anything/
- Integración Git: https://developers.cloudflare.com/pages/get-started/git-integration/
- Dominios: https://developers.cloudflare.com/pages/configuration/custom-domains/
