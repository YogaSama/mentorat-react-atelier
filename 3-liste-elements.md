# Liste d'éléments

## Cours

En React, on utilise **les listes** pour afficher dynamiquement plusieurs éléments en les générant à partir d'un tableau de données.

---

## 1️. **Afficher une liste en JSX**

On peut utiliser `.map()` pour transformer un tableau en une liste d'éléments JSX.

### Exemple :

```jsx
const fruits = ["Pomme", "Banane", "Cerise"];

function FruitList() {
  return (
    <ul>
      {fruits.map((fruit) => (
        <li>{fruit}</li>
      ))}
    </ul>
  );
}
```

👉 Ici, chaque élément du tableau `fruits` est transformé en `<li>` et affiché à l'intérieur d’une `<ul>`.

---

## 2️. **L'importance de la prop `key`**

Chaque élément d'une liste doit avoir une **clé unique** (`key`) pour aider React à identifier les éléments et optimiser les mises à jour.

### Exemple avec `key` :

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

## Exercice

Factorise le code pour ne plus à répéter les `PokemonItem` en utilisant les listes dynamiques.

Tu peux récupérer ces fonctions pour créer des objets pokemons rapidement.

```tsx
function createPokemon(id: number) {
  return {
    id: id,
    name: "pokemon",
    url: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png",
  };
}

function createPokemons(offset: number, count: number) {
  return [...new Array(count)].map((v, i) => createPokemon(offset + i));
}
```
