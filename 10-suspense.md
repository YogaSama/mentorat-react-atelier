### 🚀 **`Suspense` en React**  

`Suspense` est un composant React qui permet **d’attendre** le chargement de **données asynchrones** (comme un `lazy import` ou une requête API) avant d’afficher un contenu.  

---

## **📌 Utilisation principale : Lazy Loading (`React.lazy`)**  

Charge un composant de manière **asynchrone** pour optimiser les performances.  

```tsx
import { Suspense, lazy } from "react";

const LazyComponent = lazy(() => import("./LazyComponent"));

function App() {
  return (
    <Suspense fallback={<p>Chargement...</p>}>
      <LazyComponent />
    </Suspense>
  );
}
```

👉 **`lazy()`** charge le composant **à la demande**.  
👉 **`fallback`** affiche un **contenu temporaire** (ex: `Chargement...`).  

---

## **📌 `Suspense` avec `React Server Components` et `fetch` (React 18+)**  

React 18 permet d’utiliser `Suspense` pour attendre **les données d'une API**.  

```tsx
<Suspense fallback={<p>Chargement des données...</p>}>
  <DataComponent />
</Suspense>
```

---

## **📌 Résumé rapide**  

✅ **Utilisé pour le chargement asynchrone de composants ou de données**.  
✅ **Améliore les performances** en réduisant le temps de chargement initial.  
✅ **Affiche un `fallback` (ex: "Chargement...") en attendant que les données arrivent**.  

🔹 **Idéal pour optimiser le rendu et éviter les écrans vides en React !** 🚀
