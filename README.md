# Cuaderno de Alonso

Blog personal hecho con [Hugo](https://gohugo.io) — generador de sitios estáticos.
Escribes cada entrada en un archivo de texto (Markdown), y Hugo arma el sitio HTML completo por ti.

## Estructura

```
cuaderno-alonso/
├── content/posts/       ← aquí van tus entradas (un archivo .md por entrada)
├── layouts/              ← plantillas (no necesitas tocarlas normalmente)
├── static/css/style.css  ← el diseño
├── hugo.toml             ← configuración del sitio
└── .github/workflows/    ← publica el sitio solo, cada vez que subas cambios
```

## 1. Instalar Hugo en tu computadora

- **Mac**: `brew install hugo`
- **Windows**: `winget install Hugo.Hugo.Extended` (o `choco install hugo-extended`)
- **Linux**: `sudo apt install hugo` (o revisa https://gohugo.io/installation/)

Verifica que quedó instalado:
```
hugo version
```

## 2. Ver el sitio en tu computadora antes de publicar

Desde la carpeta del proyecto:
```
hugo server
```
Abre `http://localhost:1313/` en el navegador. Se actualiza solo mientras editas.

## 3. Escribir una entrada nueva

La forma más simple:
```
hugo new posts/titulo-de-tu-entrada.md
```
Esto crea un archivo en `content/posts/` con esta cabecera (edítala):

```markdown
---
title: "Título de tu entrada"
date: 2026-03-10
categories: ["Historia"]
summary: "Un resumen de una o dos frases que aparece en la portada."
---

Aquí escribes el texto completo de la entrada, en Markdown normal.
```

Categorías usadas hasta ahora: `Historia`, `Viajes`, `Opinión` — puedes añadir las que quieras.

## 4. Publicarlo gratis en GitHub Pages

1. Crea una cuenta en [github.com](https://github.com) si no tienes.
2. Crea un repositorio nuevo, por ejemplo `cuaderno-alonso` (público).
3. Sube esta carpeta al repositorio:
   ```
   git init
   git add .
   git commit -m "Primer commit del blog"
   git branch -M main
   git remote add origin https://github.com/TU-USUARIO/cuaderno-alonso.git
   git push -u origin main
   ```
4. En GitHub: **Settings → Pages → Source → GitHub Actions**. El flujo ya incluido
   (`.github/workflows/deploy.yml`) construye y publica el sitio automáticamente
   cada vez que hagas `git push`.
5. Abre `hugo.toml` y cambia la línea `baseURL` por tu URL real:
   ```
   baseURL = "https://TU-USUARIO.github.io/cuaderno-alonso/"
   ```
   (o tu dominio propio, si conectas uno más adelante en Settings → Pages).

Desde ese momento, publicar una entrada nueva es: escribir el `.md`, y luego
```
git add .
git commit -m "Nueva entrada: título"
git push
```
GitHub hace el resto solo.

## Personalizar

- **Colores y tipografía**: `static/css/style.css` (variables al inicio del archivo).
- **Nombre, tagline, correo**: sección `[params]` en `hugo.toml`.
- **Plantillas** (si quieres cambiar la estructura de la página): carpeta `layouts/`.
