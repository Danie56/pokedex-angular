¡Claro! Aquí tienes el documento con formato Markdown:

---

## 🧪 Paso a paso para desplegar pokedex-angular desde GitHub hasta Vercel

Este documento describe el proceso completo desde la descarga del proyecto hasta el despliegue exitoso en Vercel.

### 🔄 1. Descarga y descompresión del ZIP

Primero, descargué el proyecto pokedex-angular desde el repositorio original:

👉 https://github.com/rcuello/ac4dem1a

Ubicación del proyecto: `sistemas-distribuidos/poke-dex-lab`

Hice clic en "Code" y luego en "Download ZIP"

Lo descomprimí en mi equipo local

### ⚙️ 2. Instalación de dependencias

Una vez dentro del proyecto, ejecuté el siguiente comando para instalar todas las dependencias:

```bash
npm install
```

### 🖕 3. Subida a mi propio repositorio

Luego creé un nuevo repositorio en GitHub: 👉 https://github.com/Danie56/pokedex-angular

Copié el contenido del proyecto descomprimido a una nueva carpeta

Inicialicé un repositorio Git en esa carpeta:

```bash
git init
git remote add origin https://github.com/Danie56/pokedex-angular.git
git add .
git commit -m "Subida inicial del proyecto pokedex-angular"
git push -u origin master
```

### 🔧 4. Configuración del token de Codecov

Para habilitar la integración con Codecov, edité el archivo `.github/workflows/pipeline.yml` y agregué el token de Codecov como una variable de entorno segura.

#### 🔐 Cómo lo hice:

Fui a https://app.codecov.io/ y accedí con GitHub.

Dentro del proyecto de Codecov, copié el token del repositorio.

Luego, agregué el token a los Secrets del repositorio en GitHub:

`Settings > Secrets and variables > Actions > New repository secret`

- **Nombre:** `CODECOV_TOKEN`
- **Valor:** (el token copiado)

Aseguré que en `pipeline.yml` esté la línea que lo usa:

```yaml
- name: Upload coverage to Codecov
  uses: codecov/codecov-action@v3
  with:
    token: ${{ secrets.CODECOV_TOKEN }}
```

### 🧪 5. Ejecución de pruebas (opcional pero recomendable)

Antes de desplegar, verifiqué que las pruebas pasaran correctamente:

```bash
ng test --watch=false
```

### 🚀 6. Despliegue en Vercel

#### 📦 Preparación:

Me aseguré de tener una cuenta en https://vercel.com

Inicié sesión y conecté mi cuenta de GitHub.

Hice clic en "Add New Project" y seleccioné el repositorio `pokedex-angular`.

#### 🛠️ Configuración del proyecto en Vercel:

- **Framework:** Angular
- **Root directory:** `/` (raíz del repositorio)
- **Build Command:** `npm run build`
- **Output Directory:** `dist/pokedex-angular`

⚠️ Asegúrate de que el `angular.json` tenga configurado correctamente el `outputPath`.

#### 🚦 Deploy:

Vercel detectó la configuración automáticamente.

Hice clic en "Deploy" y esperé que finalizara el proceso.

Al terminar, obtuve una URL pública donde quedó alojado el proyecto.

### ✅ Resultado

La aplicación `pokedex-angular` quedó publicada en Vercel y con integración funcional a Codecov.

---

