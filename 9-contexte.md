### 🚀 **Les Contextes (`Context API`) en React**  

Le **Context API** permet de **partager des données globales** entre composants **sans passer par des props** à chaque niveau (**"prop drilling"**).  

---

## **📌 Création d’un contexte**  

```tsx
import { createContext } from "react";

const ThemeContext = createContext("light"); // Valeur par défaut
```

---

## **🎯 Fournir le contexte (`Provider`)**  

Un **Provider** entoure les composants qui doivent accéder aux données.  

```tsx
function App() {
  const [theme, setTheme] = useState("dark");
  return (
    <ThemeContext.Provider value={{ theme: theme, setTheme: setTheme }}>
      <Child />
    </ThemeContext.Provider>
  );
}
```

👉 **Tous les composants enfants** peuvent accéder au thème `"dark"` et le changer.

---

## **📌 Consommer le contexte (`useContext`)**  

Les composants utilisent `useContext` pour récupérer la valeur.  

```tsx
import { useContext } from "react";

function Child() {
  const { theme, setTheme } = useContext(ThemeContext);
  return (
    <>
      <p>Thème actuel : {theme}</p>
      <button onClick={() => setTheme(theme === 'dark' ? 'light' : 'dark')}>Changer le thème</button>
    </>
  );
}
```

👉 **Le composant `Child` peut lire directement le contexte sans `props`.**  

---

## **📌 Résumé rapide**  

✅ **Évite le "prop drilling"** (passage inutile de `props` entre composants).  
✅ **Utilisé pour des données globales** (thème, langue, utilisateur, etc.).  
✅ **`Provider` définit la valeur**, et **`useContext` l’utilise**.  

**🔹 Idéal pour simplifier la gestion des données globales en React !** 🚀
