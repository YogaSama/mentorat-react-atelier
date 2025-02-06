# Configuration de l'espace de travail

Avant de commencer l'atelier, il est essentiel d'avoir un environnement ISO pour chaque participant.

## Prérequis

### Node.js

Lien de téléchargement : [https://nodejs.org/en](https://nodejs.org/en)

> **Note**: La formation se fait en Node.js `v20.17.0`. Une version proche (`>= 16.0.0`) devrait suffire.

Une fois installé, vérifiez l'installation en ouvrant VSCode et depuis un terminal taper pour afficher les versions.

```bash
node -v
npm -v
```

### Git

Lien de téléchargement : [https://git-scm.com/downloads](https://git-scm.com/downloads)

Vérifier l'installation avec :
```
git version
```

### Visual Studio Code

Lien de téléchargement : [https://code.visualstudio.com/download](https://code.visualstudio.com/download)

> **Note**: La formation se fait sur la version `1.94.0`. Une version moderne devrait suffire.

## Configuration de VSCode

Un profil spécifique doit être créé pour éviter tout conflit avec vos configurations personnelles.

### 1. **Créer un profil**

Depuis la barre d'outils, appuyer sur :  
`File` > `Preferences` > `Profile (...)` > `Profiles`

Une fenêtre de gestion de profil devrait être ouverte.
Cliquez sur `New Profile` et renseignez le nom `mentorat-reat` puis cliquez sur `Create` et fermez l'onglet `Profiles`.

### 2. **Sélectionner le profil**

Depuis la barre d'outils, appuyez sur :  
`File` > `Preferences` > `Profile (...)` > `mentorat-react`

### 3. **Installer les extensions**

- Prettier - Code formatter
- ESLint

### 4. **Editer les paramètres**

Ouvrir les paramètres avec `Ctrl`+`,` et dans la version JSON y coller la configuration suivante :

```json
{
    "editor.formatOnSave": true,
    "editor.formatOnPaste": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "typescript.tsdk": "node_modules\\typescript\\lib"
}
```
