

---
# Common Assets

Ce dépôt contient des **images partagées** (photos, illustrations, visuels UI) utilisées par plusieurs projets.

L’objectif est simple : **un seul endroit pour les assets**, sans duplication, accessibles partout via **jsDelivr**.

---

## 📁 Structure

```
photos/
illustrations/
ui/
```

Chaque dossier est librement organisé par projet ou par thème.

---

## 🚀 Utilisation (via jsDelivr)

Format général :

```
[https://cdn.jsdelivr.net/gh/](https://cdn.jsdelivr.net/gh/)<USER>/<REPO>@main/<PATH>
```

### Exemple

```
[https://cdn.jsdelivr.net/gh/tsurubaso/common-assets@main/photos/image.jpg](https://cdn.jsdelivr.net/gh/tsurubaso/common-assets@main/photos/image.jpg)

````
---

## 🧩 HTML / React / Vite

```html
<img
  src="https://cdn.jsdelivr.net/gh/tsurubaso/common-assets@main/photos/image.jpg"
  alt="Image"
/>
````

---

## 🟦 Next.js

Autoriser jsDelivr dans `next.config.js` :

```js
module.exports = {
  images: {
    remotePatterns: [
      {
        protocol: "https",
        hostname: "cdn.jsdelivr.net",
        pathname: "/gh/**",
      },
    ],
  },
};
```

Puis :

```jsx
<Image
  src="https://cdn.jsdelivr.net/gh/tsurubaso/common-assets@main/photos/image.jpg"
  alt="Image"
  width={1200}
  height={800}
/>
```

---

## ⚠️ Cache

jsDelivr met fortement en cache.

Recommandé :

* versionner les fichiers (`image-v2.jpg`)
* ou utiliser un hash de commit à la place de `@main`

---

## 📌 Règle

* ❌ Pas de duplication d’images dans les projets
* ✅ Toujours consommer via jsDelivr

---

Assets centralisés = maintenance simple.

---

## 🔁 Optionnel — Centraliser l’URL des assets

Pour faciliter la maintenance et les changements futurs, il est recommandé de centraliser l’URL de base des assets.

```js
const ASSETS = "https://cdn.jsdelivr.net/gh/tsurubaso/common-assets@main";
```

Puis l’utiliser partout :

```jsx
<img src={`${ASSETS}/photos/image.jpg`} alt="Image" />
```
integration fini

