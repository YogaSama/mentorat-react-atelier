# Projet : Pokeguess

### Objectif du jeu

Le but du jeu est de deviner le nom d'un Pokemon en ne voyant que son ombre. L'utilisateur doit entrer sa réponse dans un champ de texte et valider pour voir s'il a raison.

---

### Fonctionnalités attendues

1. **Affichage de l'ombre d'un Pokemon** :
   - Utiliser l'API PokéAPI (<https://pokeapi.co/>) pour récupérer une image d'un Pokemon et la transformer en ombre (silhouette noire).
   - Afficher cette ombre dans l'interface.

    > **Aide**: Utilise le code suivant pour appeler la **pokeapi**.

    ```tsx
    // pokemonApi.ts
    import type { Pokemon } from 'pokenode-ts';

    export async function getPokemonById(id: number): Promise<Pokemon> {
    const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${id}`);
    return response.json();
    }
    ```

    > **Aide**: En CSS, pour afficher une image en noir, il suffit de lui ajouter la règle CSS `filter: brightness(0);`.

2. **Saisie et validation de la réponse** :
   - Ajouter un champ de texte pour que le joueur entre le nom du Pokemon.
   - Ajouter un bouton "Valider" pour vérifier la réponse.
   - Comparer la saisie de l'utilisateur avec le vrai nom du Pokemon.

3. **Retour utilisateur** :
   - Si la réponse est correcte, afficher un message de félicitations et révéler l'image en couleur.
   - Si la réponse est incorrecte, afficher un message d'erreur et permettre une nouvelle tentative.

4. **Passage au Pokemon suivant** :
   - Une fois la réponse validée, proposer un bouton "Suivant" pour afficher un nouveau Pokemon.

5. **Score et progression** :
   - Ajouter un compteur de score (ex: +1 point par bonne réponse).
