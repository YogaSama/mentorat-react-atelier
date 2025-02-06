### 🚀 **Les Hooks en React**  

Les **Hooks** sont des fonctions introduites dans **React 16.8** qui permettent d'utiliser l'**état (`state`)** et le **cycle de vie (`lifecycle`)** dans les **composants fonctionnels**, sans avoir besoin de classes.  

---

## 🔹 **Principaux Hooks en React**  

### **1️⃣ `useState` → Gérer un état local**  

Permet de gérer une valeur qui change dans un composant.  

```tsx
const [count, setCount] = useState(0);
```

👉 **`count`** est la valeur, **`setCount`** permet de la modifier.  

---

### **2️⃣ `useEffect` → Gérer les effets de bord**  

Sert à exécuter du code après le rendu, comme des appels API, timers, etc.  

```tsx
useEffect(() => {
  console.log("Composant monté !");
}, []); // S'exécute une seule fois
```

👉 Peut aussi s'exécuter **à chaque changement** d’une variable :  

```tsx
useEffect(() => {
  console.log(`Nouvelle valeur : ${count}`);
}, [count]);
```

---

### **3️⃣ `useContext` → Partager des données globales**  

Permet d’accéder à un **contexte global** sans passer par des `props`.  

```tsx
const theme = useContext(ThemeContext);
```

---

### **4️⃣ `useRef` → Référencer un élément HTML ou stocker une valeur persistante**  

Idéal pour manipuler un élément du DOM sans déclencher un re-render.  

```tsx
const inputRef = useRef(null);
<input ref={inputRef} />;
```

---

### **5️⃣ `useReducer` → Alternative avancée à `useState`**  

Permet de gérer un état complexe avec un **reducer** (similaire à Redux).  

```tsx
const [state, dispatch] = useReducer(reducer, initialState);
```

---

### **📌 Quand utiliser quel Hook ?**  

| Hook | Utilisation principale |
|------|-------------------------|
| `useState` | Gérer un état simple |
| `useEffect` | Effets de bord (API, timers, événements) |
| `useContext` | Accéder à un contexte global |
| `useRef` | Référencer un élément DOM ou stocker une valeur mutable |
| `useReducer` | Gérer un état complexe |

✅ **Les Hooks rendent les composants fonctionnels aussi puissants que les classes, tout en les simplifiant !** 🚀
