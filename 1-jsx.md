# JSX

Le **JSX** (_JavaScript XML_) est une extension syntaxique de JavaScript permettant d'écrire des balises HTML directement dans du code JavaScript. Il est transformé en `React.createElement()` en interne.

- **Version JS** :

    ```ts
    const element = React.createElement(
      "div",
      { className: "container" },
      "Hello ",
      React.createElement("span", { className: "bold" }, "World")
    );
    ```

- **Version JSX** :

    ```tsx
    const element = (
      <div className="container">
        Hello <span className="bold">World</span>
      </div>
    );
    ```

## **Principes clés du JSX :**

1. **Syntaxe proche du HTML**

   ```tsx
   const element = <h1>Hello world !</h1>;
   ```

2. **Expressions JavaScript intégrées avec `{}`**

   ```tsx
   const name = "Alice";
   const element = <h1>Bonjour, {name} !</h1>;
   ```

3. **Attributs en camelCase (ex: `className` au lieu de `class`)**

   ```tsx
   <button onClick={() => alert("Clique !")} className="btn">
     Clique ici
   </button>
   ```

4. **Encapsulation dans des composants React**

   ```tsx
   interface WelcomeProps {
     firstname: string;
     lastname: string;
   }

   function Welcome(props: WelcomeProps) {
     return <h1>Salut {props.firstname} {props.lastname} !</h1>;
   }
   ```

5. **Un seul élément parent obligatoire** (utilisation de `<div>` ou `<>` _fragment_)

   ```tsx
   return (
     <>
       <h1>Bonjour</h1>
       <p>Bienvenue !</p>
     </>
   );
   ```

   > **Note**: Les `<>` _fragment_ ou `<Fragment>` si on veut lui ajouter des props, ne sont pas ajoutés à l'arbre HTML.

JSX simplifie la déclaration des interfaces React en combinant HTML et JavaScript de manière fluide. 🚀
