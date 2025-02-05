# Les états

## Cours

L'**état** (`state`) est une **donnée interne** d'un composant React qui peut changer au cours du temps et provoquer une mise à jour du rendu du composant. Contrairement aux **props** qui sont immuables, l'état est modifiable depuis le composant lui-même.

En React, on gère l'état dans les **composants fonctionnels** grâce au **hook `useState`**.

---

## 1️. **Déclarer un état avec `useState`**

`useState` permet d'ajouter un état à un composant fonctionnel. Il retourne **un tableau avec deux éléments** :

1. **La valeur de l’état**
2. **Une fonction pour modifier cet état**

### **Exemple : un compteur simple**

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0); // Initialisation de l'état à 0

  return (
    <div>
      <p>Compteur : {count}</p>
      <button onClick={() => setCount(count + 1)}>Incrémenter</button>
    </div>
  );
}
```

👉 **Explication :**

- `count` est la valeur actuelle de l’état.
- `setCount` est la fonction qui permet de modifier `count`.
- `useState(0)` définit l’état initial à `0`.
- Lorsque l’on clique sur le bouton, `setCount(count + 1)` met à jour `count`, ce qui **rafraîchit automatiquement** le composant.

---

## 2️. **Mettre à jour l’état avec une fonction**

Si l’état dépend de sa valeur précédente, il est préférable d’utiliser une **fonction de mise à jour** dans `setState` :

```jsx
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Compteur : {count}</p>
      <button onClick={() => setCount((prevCount) => prevCount + 1)}>
        Incrémenter
      </button>
    </div>
  );
}
```

👉 **Pourquoi ?**  
Si plusieurs mises à jour se produisent en même temps, **React peut regrouper les mises à jour**. En utilisant `(prevCount) => prevCount + 1`, on s’assure d’avoir toujours la bonne valeur.

---

## 3️. **Utiliser plusieurs états avec `useState`**

On peut gérer **plusieurs états** dans un même composant :

```jsx
function UserProfile() {
  const [name, setName] = useState("Alice");
  const [age, setAge] = useState(25);

  return (
    <div>
      <p>Nom : {name}</p>
      <p>Âge : {age}</p>
      <button onClick={() => setAge(age + 1)}>Vieillir</button>
    </div>
  );
}
```

👉 Ici, `name` et `age` sont deux états indépendants.

---

## 4️. **État sous forme d’objet**

On peut stocker plusieurs valeurs dans un **objet** au lieu d'utiliser plusieurs `useState` :

```jsx
function UserProfile() {
  const [user, setUser] = useState({ name: "Alice", age: 25 });

  function incrementAge() {
    setUser((prevUser) => ({ ...prevUser, age: prevUser.age + 1 }));
  }

  return (
    <div>
      <p>Nom : {user.name}</p>
      <p>Âge : {user.age}</p>
      <button onClick={incrementAge}>Vieillir</button>
    </div>
  );
}
```

👉 **Pourquoi utiliser `{ ...prevUser }` ?**  
React ne fusionne pas automatiquement les objets d’état. Il faut donc **copier l’état précédent** avec `...prevUser` pour ne pas perdre les autres valeurs.

---

## Exercice

Stocke les pokemons dans un état grâce à `useState` et génère `3` nouveaux pokemons à chaque fois que tu appuies sur `Voir plus`.
