
## Exercice 1

Converti la structure HTML suivante en JSX dans le composant `App.tsx` :

```html
<header class="header">Pokedex</header>
<main class="main">
  <div class="tools">
    <button class="show-more">Voir plus</button>
    <div class="shiny">
      <label for="shiny-checkbox">shiny</label>
      <input id="shiny-checkbox" type="checkbox" />
    </div>
  </div>
  <div class="list">
    <div class="item">
      #1 pokemon
      <img
        class="icon"
        src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png"
      />
    </div>
    <div class="item">
      #2 pokemon
      <img
        class="icon"
        src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png"
      />
    </div>
    <div class="item">
      #3 pokemon
      <img
        class="icon"
        src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png"
      />
    </div>
  </div>
</main>
```

---

## Exercice 2

Actuellement chaque pokemon est dupliqué :

```tsx
<div className="item">
  #1 pokemon
  <img
    class="icon"
    src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png"
  />
</div>
<div className="item">
  #2 pokemon
  <img
    class="icon"
    src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png"
  />
</div>
<div className="item">
  #3 pokemon
  <img
    class="icon"
    src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png"
  />
</div>
```

Créer un nouveau composant nommé `PokemonItem` dans un **nouveau fichier**.
Il doit avoir les propriétés suivantes :

- `id`: **nombre** devant nom du pokemon (#`1`).
- `name`: nom du pokemon. (Actuellement `pokemon`)
- `url`: url de l'image du pokemon.

Import ce fichier dans `App.tsx` et remplace l'ancien code par ce nouveau composant.

## Exercice 3

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

---

## Exercice 4

Stocke les pokemons dans un état grâce à `useState` et génère `3` nouveaux pokemons à chaque fois que tu appuies sur `Voir plus`.

---

## Exercice 5

Créé une référence `listRef` avec `useRef` que tu associera à `list` grace à la propriété `ref` de l'élément `div`. On l'utilisera plus tard pour scroll automatiquement.

Une fois fait, colle ce bout de code dans ton composant `App`. On l'adaptera pour qu'il scroll automatiquement.

```tsx
useEffect(() => {
    listRef.current?.scrollTo({ top: listRef.current.scrollHeight });
}, []);
```

# Exercice 6

Créé un fichier `pokemonApi.ts` à la racine du dossier `src` et colle y le code suivant :

```ts
import type { NamedAPIResource, NamedAPIResourceList } from 'pokenode-ts';

export async function getPokemons(
  limit: number,
  offset: number
): Promise<NamedAPIResource[]> {
  const response = await fetch(
    `https://pokeapi.co/api/v2/pokemon/?limit=${limit}&offset=${offset}`
  );
  const json: NamedAPIResourceList = await response.json();
  return json.results;
}
```

La méthode `getPokemons` permet de récupérer des pokemons. Utilise cette méthode dans un `useEffect` pour mettre à jour la liste des pokemons.

---

# Exercice 7

Pour l'instant la fonction `getPokemons` ne remonte que `name` et une `url` pour chaque pokemon. Avant d'aller plus loin dans la récupération des informations sur le pokemon, on va corriger l'affichage pour conditionner l'affichage de l'ID (`id`) et de l'image (`url`) que s'ils sont présent.

---

# Exercice 8

Dans le fichier `pokemonApi.ts`, ajouter la fonction suivante :

```ts
export async function getPokemon(name: string): Promise<Pokemon> {
  const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${name}`);
  return response.json();
}
```

Utiliser cette fonction pour charger les données de chaque pokemon.
