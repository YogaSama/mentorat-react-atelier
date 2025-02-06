### 🚀 **`useState` en React**  

`useState` est un **Hook** qui permet de gérer l’**état local** dans un **composant fonctionnel**.  

---

## **📌 Syntaxe de base**  

```tsx
const [state, setState] = useState(valeurInitiale);
```

👉 **`state`** : La valeur actuelle de l’état.  
👉 **`setState`** : Fonction pour mettre à jour l’état.  
👉 **`valeurInitiale`** : Valeur par défaut de l’état.  

---

## **🎯 Exemple : Un compteur simple**  

```tsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Compteur : {count}</p>
      <button onClick={() => setCount(count + 1)}>Incrémenter</button>
    </div>
  );
}
```

✅ **Chaque clic sur le bouton met à jour l’état et déclenche un re-render.**  

---

## **📌 Mise à jour basée sur l'état précédent**  

```tsx
setCount(prevCount => prevCount + 1);
```

👉 Utile pour éviter les **problèmes de concurrence** dans des mises à jour asynchrones.  

---

## **📌 `useState` avec un objet**  

```tsx
const [user, setUser] = useState({ name: "Alice", age: 25 });

setUser({ ...user, age: 26 }); // Mise à jour partielle
```

👉 **Toujours copier l'ancien état** (`...user`) pour éviter d’écraser les autres propriétés.  

---

### **📌 Résumé rapide**  

✅ `useState` permet d’ajouter un **état local** dans un composant fonctionnel.  
✅ Un changement d’état **déclenche un re-render**.  
✅ Pour des mises à jour basées sur l’état précédent, utiliser une **fonction** (`prevState`).  
✅ Avec un **objet**, il faut **conserver les propriétés existantes** avec `...`.  

**🔹 `useState` est l’un des Hooks les plus utilisés en React !** 🚀
