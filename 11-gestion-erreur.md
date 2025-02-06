### 🚀 **Gestion des erreurs en React (Résumé)**

En React, la gestion des erreurs permet de capturer et d'afficher les erreurs qui se produisent dans l'UI, tout en garantissant que l'application ne se "casse" pas.

---

## **📌 `Error Boundaries` (Limites d'erreurs)**  

Les **Error Boundaries** sont des composants React spéciaux utilisés pour **capturer les erreurs dans les composants enfants** et afficher un message de secours.

### Exemple de `Error Boundary`

```tsx
import { Component } from "react";

class ErrorBoundary extends Component {
  state = { hasError: false };

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.log("Erreur capturée:", error, info);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Quelque chose s'est mal passé !</h1>;
    }
    return this.props.children;
  }
}
```

**Utilisation** :

```tsx
<ErrorBoundary>
  <MyComponent />
</ErrorBoundary>
```

👉 **`ErrorBoundary`** capture les erreurs dans **`MyComponent`** et affiche un message personnalisé sans faire planter l'application.

---

## **📌 Utilisation avec `useEffect` et gestion des erreurs asynchrones**  

Pour gérer les erreurs dans des appels asynchrones (comme une requête API), on peut utiliser un `try-catch` dans un `useEffect`.

```tsx
import { useEffect, useState } from "react";

function MyComponent() {
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => {
    async function fetchData() {
      try {
        const response = await fetch("https://api.example.com/data");
        if (!response.ok) throw new Error("Erreur de réseau");
        const result = await response.json();
        setData(result);
      } catch (error) {
        setError(error.message);
      }
    }
    fetchData();
  }, []);

  if (error) return <p>Erreur : {error}</p>;
  return <div>{data ? "Données chargées" : "Chargement..."}</div>;
}
```

---

## **📌 Résumé rapide**  

✅ **Error Boundaries** capturent les erreurs des composants enfants et affichent un fallback.  
✅ Pour les erreurs **asynchrones**, on utilise `try-catch` dans les `useEffect`.  
✅ Permet d'éviter que l'application plante et d'afficher un message d'erreur compréhensible à l'utilisateur.  

**🔹 La gestion des erreurs assure une expérience utilisateur plus robuste et fiable en React !** 🚀
