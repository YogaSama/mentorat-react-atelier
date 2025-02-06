# Références

## Cours

`useRef` est un **hook** qui permet de créer une **référence mutable** qui persiste entre les rendus d’un composant **sans provoquer de re-render** lorsqu’elle change.

---

## 1️. **Utilisation principale : Référencer un élément DOM**

On peut utiliser `useRef` pour **accéder directement à un élément du DOM**, comme un champ de saisie.

### **Exemple : Focus sur un champ input**

```jsx
import { useRef } from "react";

function FocusInput() {
  const inputRef = useRef(null);

  function handleFocus() {
    inputRef.current.focus(); // Met le focus sur l'input
  }

  return (
    <div>
      <input ref={inputRef} type="text" placeholder="Tapez ici..." />
      <button onClick={handleFocus}>Focus</button>
    </div>
  );
}
```

👉 Ici, `inputRef.current` pointe vers l’élément `<input>`, et `focus()` est appelé lorsqu'on clique sur le bouton.

---

## 2️. **Stocker une valeur sans déclencher de re-render**

Contrairement à `useState`, **modifier `useRef` ne provoque pas de re-rendu** du composant.

### **Exemple : Stocker un compteur qui ne déclenche pas de re-render**

```jsx
import { useRef, useState } from "react";

function Counter() {
  const countRef = useRef(0);
  const [count, setCount] = useState(0);

  function increment() {
    countRef.current += 1; // Change la valeur sans re-render
    setCount(count + 1); // Change la valeur avec re-render
    console.log("Ref:", countRef.current);
  }

  return (
    <div>
      <p>Compteur affiché : {count}</p>
      <button onClick={increment}>Incrémenter</button>
    </div>
  );
}
```

👉 `countRef.current` change **sans déclencher de mise à jour de l’UI**, contrairement à `useState`.
