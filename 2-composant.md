# Composant

## Cours

Un **composant** en React est une fonction (ou une classe) qui retourne du JSX pour afficher une partie de l'interface utilisateur.

---

## 1️. **Composant**

Un **composant** est une simple fonction qui à la fin retourne du JSX.

### Exemple :

```tsx
function HelloWorld() {
  return <h1>Hello, world !</h1>;
}
```

👉 Ce composant affiche simplement un message sans interaction ni mise à jour.

---

## 2️. **Composant avec des propriétés (props)**

Les **props** (_properties_) permettent de passer des données à un composant pour le rendre réutilisable et dynamique.

### Exemple :

```tsx
interface GreetingProps {
  name: string;
}

function Greeting(props: GreetingProps) {
  return <h1>Salut, {props.name} !</h1>;
}
```

### Utilisation :

```tsx
<Greeting name="Alice" />
<Greeting name="Bob" />
```

👉 Ici, `name` est une prop qui permet d'afficher un message personnalisé.

---

## 3️. **Imbrication des composants**

Les composants peuvent être imbriqués pour structurer l'interface utilisateur.

### Exemple :

```tsx
function Header() {
  return <h1>Mon Site</h1>;
}

function Main() {
  return <p>Bienvenue sur mon site !</p>;
}

function App() {
  return (
    <div>
      <Header />
      <Main />
    </div>
  );
}
```

👉 `App` est un composant qui **inclut** `Header` et `Main`, structurant ainsi l'affichage.

--

## Exercice

Créé un fichier `PokemonItem.tsx` au même niveau que `App.tsx` et construit un **Composant** permettant d'afficher le HTML suivant :

```tsx
<div class="item">
  #1 pokemon
  <img
    class="icon"
    src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png"
  />
</div>
```

Le numéro #`1`, le nom `pokemon` et l'URL de l'image doivent être paramétrable avec les propriétés respectives : `id`, `label` et `url`.
