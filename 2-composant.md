# Composant

Une **fonction composant** en React est une fonction JavaScript (ou TypeScript) qui retourne du **JSX** pour afficher une partie de l'interface utilisateur. Elle permet de structurer et réutiliser du code facilement.  

---

### **Synthèse d'une fonction composant :**  

- C'est une **fonction** qui retourne du **JSX**.  
- Elle peut recevoir des **props** (_properties_) pour être dynamique.  
- Elle s’écrit en **PascalCase** (`NomDuComposant`).  
- Elle peut être **imbriquée** dans d’autres composants.  

---

### **Exemple d'une fonction composant :**  

```tsx
function HelloWorld() {
  return <h1>Hello, world !</h1>;
}
```

👉 Affiche un message statique.  

---

### **Exemple avec des `props` :**  

```tsx
interface GreetingProps {
  name: string;
}

function Greeting({ name }: GreetingProps) {
  return <h1>Salut, {name} !</h1>;
}
```

👉 `name` est une prop qui rend le composant dynamique.  

---

### **Exemple d'imbrication de composants :**  

```tsx
function Header() {
  return <h1>Mon Site</h1>;
}

function App() {
  return (
    <div>
      <Header />
      <p>Bienvenue sur mon site !</p>
    </div>
  );
}
```

👉 `App` inclut `Header`, structurant ainsi l'interface. 🚀
