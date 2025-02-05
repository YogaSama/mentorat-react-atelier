# Syntaxe JSX

## Cours

Le JSX (_JavaScript XML_) est une extension syntaxique de JavaScript utilisée avec React pour décrire l'interface utilisateur. Il permet d'écrire des balises HTML directement dans le code JavaScript.

### 1. **Syntaxe de base**

JSX ressemble à du HTML, mais il est transformé en `React.createElement()` sous le capot.

```tsx
const element = <h1>Hello, world !</h1>;
```

### 2. **Intégration d'expressions JavaScript**

On peut insérer des expressions JavaScript dans JSX à l'aide des `{}`.

```tsx
const name = "Alice";
const element = <h1>Bonjour, {name} !</h1>;
```

### 3. **Attributs JSX**

Les attributs utilisent la camelCase au lieu du kebab-case comme en HTML.

```tsx
const element = (
  <button onClick={() => alert("Clique !")} className="btn">
    Clique ici
  </button>
);
```

> **Note** : Les mots clés réservé au JavaScript ne peuvent pas être directement utilisés. On utilise `className` au lieu de `class` car `class` est un mot réservé en JavaScript. Pareil pour `for` qui devient `htmlFor`.

### 6. **JSX et composants**

On peut encapsuler du JSX dans des composants React.

```tsx
function Welcome(props) {
  return <h1>Salut, {props.name} !</h1>;
}

const element = <Welcome name="Alice" />;
```

### 7. **JSX doit retourner un seul élément parent**

On doit toujours envelopper plusieurs éléments dans un seul élément parent, comme une `<div>` ou un `<>` (_fragment_).

```tsx
// Mauvais
// return ( <h1>Bonjour</h1> <p>Bienvenue !</p> );

// Correct
return (
  <>
    <h1>Bonjour</h1>
    <p>Bienvenue !</p>
  </>
);
```

JSX facilite l'écriture des interfaces React tout en gardant la puissance de JavaScript. 🚀

## Exercice

Transforme la structure HTML suivante en JSX dans le composant `App.tsx` :

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
