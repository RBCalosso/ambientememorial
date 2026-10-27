# MEMORIAL RIO CHOCANCHARAVA

Build estática completa, preparada para Vercel. Incluye HTML, CSS, JavaScript, imágenes, croquis, el modelo GLB, el SketchUp descargable y Three.js con su licencia. No necesita instalar dependencias ni variables de entorno.

## Publicar desde GitHub

1. Descomprime el ZIP.
2. Sube el CONTENIDO de la carpeta `memorial-chocancharava-vercel` a un repositorio de GitHub. En la raíz deben quedar `vercel.json`, `README.md` y la carpeta `public/`. Conserva todas las subcarpetas.
3. En Vercel, crea un proyecto e importa ese repositorio.
4. La configuración incluida indica: Framework Preset **Other**, Output Directory **public**, sin Build Command ni Install Command. Si Vercel pregunta por Root Directory, usa la raíz del repositorio.
5. Pulsa Deploy. Comparte el dominio de producción que Vercel asigne al proyecto.

No subas solo `index.html`: el modelo y las imágenes dependen de las carpetas incluidas. El ZIP se descomprime antes de subir los archivos; no es un importador de ZIP dentro de Vercel.

## Publicar desde tu computadora con la terminal

Con Node.js instalado, abre una terminal en la carpeta que contiene `vercel.json` y ejecuta:

```bash
npx vercel --prod
```

Inicia sesión en Vercel cuando lo solicite y vincula la carpeta a un proyecto nuevo o al proyecto de destino. Esta orden publica en producción; la configuración estática está incluida.

## Acceso público

Esta build no contiene inicio de sesión de ChatGPT. La visibilidad final depende de la configuración de tu proyecto de Vercel. En Settings → Deployment Protection, comprueba que el dominio de producción no requiera Vercel Authentication ni contraseña. Verifica el enlace en una ventana de incógnito antes de compartirlo. No es necesario hacer público el repositorio de GitHub para que el sitio sea público.

## Editar

- `public/index.html`: contenido y estructura completa de la página.
- `public/style.css`: diseño y adaptación a pantallas pequeñas.
- `public/app.js`: galería, croquis y relato interactivo.
- `public/viewer.js`: visor del modelo 3D.
- `public/assets/`: renders, croquis y archivos del modelo.
- `public/vendor/`: bibliotecas locales del visor, sin depender de un CDN.

El archivo `public/assets/memorial.glb` es idéntico al GLB adjuntado. Se carga automáticamente al acercarse a la sección del modelo. La vista normal utiliza WebGL; si no está disponible, se activa la vista geométrica de compatibilidad sin texturas.

Los archivos GLB y SKP tienen enlaces de descarga en la página y estarán accesibles a los visitantes cuando publiques esta build.

## Vista previa local

Si tienes Python instalado, ejecuta desde esta carpeta:

```bash
python -m http.server 8000 --directory public
```

Abre `http://localhost:8000`. En Windows también puedes usar `py -m http.server 8000 --directory public`. El modelo debe probarse desde un servidor HTTP; abrir el HTML con doble clic puede bloquear la carga de módulos o del GLB.

## Documentación de Vercel

- Configuración estática: https://vercel.com/docs/project-configuration/vercel-json
- Publicación por CLI: https://vercel.com/docs/cli/deploy
- Acceso y autenticación: https://vercel.com/docs/deployment-protection/methods-to-protect-deployments/vercel-authentication
