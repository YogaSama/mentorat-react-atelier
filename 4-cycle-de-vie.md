## 🚀 **Cycle de vie d’un composant fonctionnel en React**  

Les composants fonctionnels **n'ont pas** de cycle de vie natif comme les classes (`componentDidMount`, `componentDidUpdate`, `componentWillUnmount`).  
Cependant, grâce aux **Hooks** (`useState`, `useEffect`), on peut gérer ces étapes manuellement.  

---

## **📌 1️⃣ Phase de Montage (Initialisation)**

📌 Le composant est **créé et ajouté au DOM**.  
✅ **Les `props` sont reçues** depuis le parent.  
✅ **Le `state` est initialisé** avec `useState()`.  
✅ **Le premier rendu est effectué**.  
✅ **`useEffect(..., [])` s'exécute une seule fois** (équivalent à `componentDidMount`).  

```tsx
import { useState, useEffect } from "react";

function Example({ name }) {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Composant monté !");
  }, []); // Exécuté une seule fois après le premier rendu

  return <p>Bonjour {name}, compteur : {count}</p>;
}
```

---

## **📌 2️⃣ Phase de Mise à jour (Update)**

📌 Le composant **se met à jour** lorsqu’un `state` ou une `prop` change.  
✅ **Si `props` changent**, React met à jour le composant et déclenche un **re-render**.  
✅ **Si `state` change**, le composant est mis à jour et **re-rendu**.  
✅ **`useEffect(..., [state])` est exécuté à chaque changement du `state` ou des `props`** (équivalent à `componentDidUpdate`).  

```tsx
useEffect(() => {
  console.log(`Le compteur a été mis à jour : ${count}`);
}, [count]); // Se déclenche à chaque modification de count
```

---

## **📌 3️⃣ Phase de Démontage (Suppression)**

📌 Le composant **est retiré du DOM**.  
✅ `useEffect` peut retourner une **fonction de nettoyage** (équivalent à `componentWillUnmount`).  
✅ Cela sert à **libérer les ressources** (ex: arrêter un timer, annuler une requête API…).  

```tsx
useEffect(() => {
  console.log("Composant monté !");
  
  return () => {
    console.log("Composant démonté !");
  };
}, []); // Fonction exécutée avant la suppression
```

---

## **📌 Schéma récapitulatif 🔄**

| Phase        | `props`         | `state`         | `useEffect`            |
|-------------|----------------|----------------|------------------------|
| **Montage** | Reçues au début | Initialisé      | `useEffect(..., [])`   |
| **Mise à jour** | Si changé, re-render | Si changé, re-render | `useEffect(..., [state])` |
| **Démontage** | Plus utilisées | Supprimé       | `return () => {...}` dans `useEffect` |

---

## **📌 Exemple complet : Gestion du cycle de vie**

```tsx
import { useState, useEffect } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  // Effet de montage et démontage
  useEffect(() => {
    console.log("🟢 Composant monté !");
    
    return () => {
      console.log("🔴 Composant démonté !");
    };
  }, []);

  // Effet de mise à jour du count
  useEffect(() => {
    console.log(`🔄 Le compteur est mis à jour : ${count}`);
  }, [count]);

  return (
    <div>
      <p>Compteur : {count}</p>
      <button onClick={() => setCount(count + 1)}>Incrémenter</button>
    </div>
  );
}
```

---

## **📌 Résumé rapide 🚀**  

✅ **Montage** → `useEffect(..., [])` (Exécuté une fois après le rendu)  
✅ **Mise à jour** → `useEffect(..., [state])` (Exécuté à chaque changement de `state` ou `props`)  
✅ **Démontage** → `return () => {...}` dans `useEffect` (Exécuté avant suppression)  

**🔹 Avec `useEffect`, on contrôle facilement le cycle de vie d’un composant fonctionnel React !** 🚀
