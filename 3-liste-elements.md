# Liste d'éléments

En React, on utilise **les listes** pour afficher dynamiquement plusieurs éléments en les générant à partir d'un tableau de données.

---

## 1️. **Afficher une liste en JSX**

On peut utiliser `.map()` pour transformer un tableau en une liste d'éléments JSX.

### Exemple

**Liste statique** :

Affiche statiquement les éléments `li` de notre liste.

```jsx
const element = (
  <ul>
    <li>Pomme</li>
    <li>Banane</li>
    <li>Cerise</li>
  </ul>
);
```

**Liste dynamique brute** :

Construit la liste d'éléments dans un `Array`. De cette manière React identifie chaque `li` comme un élément dynamique.

```jsx
const element = (
  <ul>
    {[
      <li key={1}>Pomme</li>,
      <li key={2}>Banane</li>,
      <li key={3}>Cerise</li>
    ]}
  </ul>
);
```

> **Note**: La propriété `key` est utilisée pour **identifier** de manière **unique** un élément dans une liste. Elle permet à React d'**optimiser** le rendu en réutilisant et repositionnant les éléments plutôt que de les recréer, notamment lors d'un tri ou d'une mise à jour de la liste. 🚀

**Liste dynamique depuis `Array.map`** :

```jsx
const fruits = ["Pomme", "Banane", "Cerise"];

const element = (
  <ul>
    {fruits.map((fruit, index) => (
      <li key={index}>{fruit}</li>
    ))}
  </ul>
);
```

> **Note** : Piqûre de rappel, la fonction `map` sert à transformer un tableau d'object **A** en un nouveau tableau d'objets **B**. Chaque valeur du tableau est traitée unitairement.

👉 Ici, chaque élément du tableau `fruits` est transformé en `<li>` et affiché à l'intérieur d’un `<ul>`.

## 2️. **L'importance de la prop `key`**

Chaque élément d'une liste doit avoir une **clé unique** (`key`) pour aider React à identifier les éléments et optimiser les mises à jour.

### Exemple avec `key`

```jsx
const fruits = ["Pomme", "Banane", "Cerise"];

function FruitList() {
  return (
    <ul>
      {fruits.map((fruit, index) => (
        <li key={index}>{fruit}</li>
      ))}
    </ul>
  );
}
```

👉 `key={index}` est utilisé pour donner une **clé unique** à chaque `<li>`.

> **Attention !** Utiliser `index` comme clé peut causer des problèmes si la liste change dynamiquement. Il est préférable d'utiliser une **id unique** si possible.
