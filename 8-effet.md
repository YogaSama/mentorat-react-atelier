# Effet

## Cours

`useEffect` est un **hook** qui permet d’exécuter du code **après le rendu** d’un composant. Il est utilisé pour **gérer les effets secondaires**, comme :  
✅ Récupérer des données (API fetch)  
✅ Manipuler le DOM  
✅ Écouter des événements  
✅ Gérer des timers ou des abonnements

---

## 1️. **Exécuter un effet après chaque rendu**

Par défaut, `useEffect` s'exécute après **chaque** rendu du composant.

### **Exemple : Log à chaque rendu**

```jsx
import { useEffect } from "react";

function Example() {
  useEffect(() => {
    console.log("Le composant s'est rendu !");
  });

  return <p>Regarde la console !</p>;
}
```

👉 Ici, le message s'affiche **à chaque rendu**, y compris après une mise à jour d'état.

---

## 2️. **Exécuter un effet seulement au premier rendu**

On peut exécuter un effet **une seule fois** en passant un **tableau vide `[]`** comme second argument.

### **Exemple : Exécuter une seule fois**

```jsx
import { useEffect } from "react";

function Example() {
  useEffect(() => {
    console.log("Je s'exécute une seule fois !");
  }, []); // [] signifie "exécuter seulement au montage"

  return <p>Regarde la console !</p>;
}
```

👉 L'effet ne s’exécute **qu’au premier affichage** du composant.

---

## 3️. **Écouter un état ou une prop**

Si on passe une **variable** dans le tableau de dépendances `[state]`, l’effet se déclenche **seulement quand cette variable change**.

### **Exemple : Réagir à un changement d’état**

```jsx
import { useEffect, useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Le compteur a changé :", count);
  }, [count]); // Exécuté à chaque modification de `count`

  return (
    <div>
      <p>Compteur : {count}</p>
      <button onClick={() => setCount(count + 1)}>Incrémenter</button>
    </div>
  );
}
```

👉 `useEffect` s’exécute **uniquement quand `count` change**.

---

## 4️. **Nettoyer un effet (Cleanup)**

Si un effet crée un **abonnement** ou un **timer**, il faut le nettoyer pour éviter les fuites de mémoire.

### **Exemple : Nettoyage d’un timer**

```jsx
import { useEffect, useState } from "react";

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds((s) => s + 1);
    }, 1000);

    return () => {
      clearInterval(interval); // Nettoyage du timer au démontage
    };
  }, []);

  return <p>Temps écoulé : {seconds} sec</p>;
}
```

👉 `clearInterval(interval)` empêche le **timer de continuer après le démontage** du composant.

Idéal pour gérer le cycle de vie d’un composant React ! 🚀

## Exercice

Scroll en bas de la div `list` dès que de nouveaux pokemons y sont ajoutés.

Tu peux utiliser la méthode suivante pour scroll sur un élément HTML.

```tsx
monElement.scrollTo({ top: monElement.scrollHeight });
```
