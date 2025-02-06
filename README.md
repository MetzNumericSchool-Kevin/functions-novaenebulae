[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/n2ZsgqDb)
# Exercices sur les fonctions en JavaScript

- Tu peux mettre toutes tes réponses dans le fichier `exercices.js`.
- À chaque exercice _(chaque sous-titre après le titre Exercices dans cet énoncé)_, tu dois faire un commit avec le titre de l'exercice.
- Tu n'es pas obligé de garder le code fait précédemment, mais ⚠️ **attention** certaines choses sont utiles pour plus tard.

## Rappels

La structure d'une fonction s'écrit de la manière suivante :

```js
// Mot clé function
// Un nom de fonction
// 0 à N paramètres qui permettent de réutiliser la fonction avec plusieurs contextes pour son exécution
function addition(A, B) {
  // Corps de la fonction
  return A + B; // Quand la fonction est exécutée, elle retournera la somme de la valeur du paramètre A et de la valeur du paramètre B
}

// Une fonction peut avoir un paramètre par défaut
function cube(x = 5) {
  // Si nous ne passons pas d'arguments (undefined), x vaudra 5 par défaut
  return x * x * x;
}
```

- Une fonction est d'abord définie, **son exécution** se fait avec `()` => `addition(1, 3)` avec les arguments `1` et `3`. Dans son exécution le paramètre `A` = `1` et le paramètre `B` = `3`. Le résultat que je récupérerai à la fin de l'exécution de la fonction sera `4`.
- `return` va faire "sortir" le résultat de la fonction pour pouvoir être utilisé à l'extérieur de cette fonction _(la fonction est comme une boîte dont on ne connaît pas le contenu)_.
- Une fonction peut être nommée ou anonyme.
- Une fonction peut exécuter d'autres fonctions.
- Une fonction peut recevoir en tant que paramètre, une autre fonction, et l'appeler quand il le souhaite (principe de callback).
- Une fonction peut utiliser des variables globales (mais ce n'est pas conseillé) ou appeler des fonctions globales.

Mettez vos ressources de cours pas loin de vous et n'oubliez pas de vérifier ce que vous faites avec du `console.log`.

## Thème 🔮🧙‍♂️🧪🪙🍄

- Tu es le sorcier Archibald 🧙‍♂️ et tu gères une petite boutique dans laquelle tu crées et vends des potions 🧪.

Dès que tu verras `<ce_genre_de_chose>` c'est qu'il faudra remplacer `<ce_genre_de_chose>` par la bonne variable appropriée au contexte.\
Tu comprendras en lisant la suite :)

Commencez avec ces constantes

```js
const nom_sorcier = "Archibald 🧙‍♂️";
const manuel_de_fabrication = {
  potion_soin: {
    ingredients: ["eau_de_source", "ecaille_de_dragon", "poudre_de_diamant"],
    temps_de_fabrication: 3, // exprimé en secondes
  },
};
const inventaire = [
  {
    id: "potion_soin", // identifiant unique de la potion
    prix: 10,
    stock: 0,
  },
];
```

## Exercices

### Salutation Aventurier

- Crée une fonction `salutations` qui prend en paramètre ton nom de sorcier
- Cette fonction affiche dans la `console` : `Salutations Aventurier ! Je me nomme <nom_sorcier> pour vous servir.`.
- ⚠️ Passe bien ton nom de sorcier en paramètre, n'utilise pas la constante de manière globale

### Quel est le tarif d'une potion ?

- Crée une fonction prenant en paramètre l'identifiant d'une potion et l'inventaire et une quantité demandée par défaut à 1
- Pas besoin de prendre le stock en compte pour cette fonction
- La fonction doit retourner `prix potion * quantité`
- Affiche dans la `console` un exemple de prix pour 3 potions coûtant 10 🪙 en exécutant cette fonction

### Fabrication de potion

- Crée une fonction avec en paramètres
  - identifiant de la potion
  - prix (pas obligatoire, par défaut à 10)
  - stock (pas obligatoire, par défaut à 1)
- La fonction doit te retourner un nouvel objet de la même structure que la potion existante dans l'`inventaire`
- Affiche dans la `console` la création de nouvelles potions, parfois change les paramètres de prix et de stock pour avoir des valeurs différentes

### Ajout de nouvelles potions dans l'inventaire

- Crée une fonction pour ajouter une potion à l'inventaire
  - premier paramètre est l'inventaire des potions
  - deuxième paramètre est une potion
- Dans cette fonction
  - Si la potion existe déjà
    - Met à jour le prix, et ajoute le stock au stock existant
    - Sinon, ajoute la potion dans son inventaire
  - À chaque ajout de potion on fait un tri sur l'inventaire du plus cher au moins cher avec la méthode `sort` disponible sur les tableaux _(cela va modifier le tableau original)_

### Cherche moi les potions qui...

- Écris une fonction qui permet de récupérer la liste de toutes les potions en stock. ⚠️ Utilise la méthode `filter` disponible sur les tableaux pour éviter de muter le tableau initial.
- Écris une fonction qui permet de récupérer la liste de toutes les potions avec un stock à 0.
- Exécute et affiche ton `inventaire`, le résultat de la première fonction et le résultat de la deuxième fonction dans la `console` et observe bien que chaque tableau est différent et que le tableau initial est bien intact.

### Allons faire de la cueillette, nous avons besoin de plus de potions !

Tu vas transformer la fonction de fabrication de potions pour prendre en compte des ingrédients.

- Ajoute en 2ème paramètre un tableau d'ingrédients _(liste de chaînes de caractères)_
- La fonction doit retourner la nouvelle potion si la liste d'ingrédients est complète. Sinon, elle retournera une erreur `new Error('Il manque des ingrédients à cette potion')`. Utilise le `manuel_de_fabrication` pour vérifier cela.
- ⚠️ Ici nous ne passons pas la constante `manuel_de_fabrication` en paramètre. Nous utilisons cette constante de manière **globale** directement dans la fonction. Ce n'est pas une pratique conseillée mais dans le cas de notre exercice cela sera plus simple.

---

- Teste la création de plusieurs potions, parfois avec tous les ingrédients, parfois avec des ingrédients manquants.
  - **⚠️ Attention** il faut utiliser la fonction d'ajout de potion uniquement si la fabrication a fonctionné.
  - Pour cela, fais un test si la création de fonction retourne une erreur
    - Si `<resultat_creation_potion> instanceof Error`, affiche `console.error(<resultat_creation_potion>.message)`
    - Sinon, utilise la fonction d'ajout de potion dans l'inventaire

### Une potion n'est jamais fabriquée en retard, ni en avance d'ailleurs. Elle est fabriquée précisément à l'heure prévue !

Si tu regardes le manuel de fabrication tu peux voir que les potions ont un délai de fabrication.

- Transforme la fonction de fabrication pour ajouter ce délai avec `setTimeout`. Je t'aide un peu:

```js
// Tu dois utiliser cette fonction
// 1er argument est une fonction de rappel, c'est à dire, la fonction à exécuter quand le temps est écoulé
// 2ème argument le délai exprimé en millisecondes
setTimeout(<fonction_de_rappel>, <temps_de_fabrication> * 1000) // x1000 pour convertir les millisecondes en secondes
// Tu trouveras le temps de fabrication dans le manuel de fabrication
```

- Ajoute un paramètre en 3ème position de la fonction.
  - Ce paramètre sera une fonction qu'on pourra appeler lorsque setTimeout aura terminé.
  - Lors de l'appel de ce paramètre, passe en argument la nouvelle potion.
  - **⚠️ La fonction ne retourne plus la potion créée. Cela doit se faire uniquement quand le délai du `setTimeout` est terminé !**

Je t'aide un peu pour te montrer ce que cela **pourrait** donner à l'utilisation :

```js
function laPotionEstFinie(potion) {
  console.log("Fabrication de potion finie :", potion);
  // On exécute ici le code quand la potion est finie, par exemple ce que tu as déjà fait : l'ajout de la nouvelle potion dans l'inventaire
}
// 1er argument l'identifiant
// 2ème argument le tableau d'ingrédients (qui doit être dans le manuel pour que cela fonctionne)
// 3ème argument la fameuse fonction de rappel :)
// 4ème argument le prix
// 5ème argument le stock
const erreurDeFabrication = fabriqueUnePotion("potion_de_sommeil", ["coeur_de_cristal", "seve_arbre_des_reves", "fleurs_de_lune"], laPotionEstFinie, 200, 10);
if (erreurDeFabrication instanceof Error) console.error(erreurDeFabrication.message);
```

### Epreuve ultime, la fabrication de plusieurs inventaires indépendants

Dans ce dernier exercice tu vas utiliser des `closures` pour permettre de créer plusieurs inventaires qui vont fonctionner de manière indépendante.
Un exemple de closure pour un système de compteur que vous pouvez essayer et tester (supprimez le code ensuite) :

```js
// Déclaration d'une fonction permettant de créer un compteur indépendant
function createCounter() {
  // count sera "capturé" par l'objet retourné par cette fonction car les méthodes de l'objet ont une dépendance envers count
  // ce qui permettra à chaque création de compteur, d'avoir une variable count unique
  let count = 0; // variable locale à la fonction createCounter

  return {
    // increment est ici une méthode "closure" capturant la variable "libre" count dans son contexte
    increment: function () {
      count++;
    },
    // decrement est ici une méthode "closure" capturant la variable "libre" count dans son contexte
    decrement: function () {
      count--;
    },
    // value est ici une méthode "closure" capturant la variable "libre" count dans son contexte
    value: function () {
      return count;
    },
  };
}

// à l'utilisation
const compteurA = createCounter();
const compteurB = createCounter();

compteurA.increment();

compteurB.increment();
compteurB.increment();

console.log(compteurA.getValue()); // Affichera 1
console.log(compteurB.getValue()); // Affichera 2
```

Nous allons faire la même chose avec l'inventaire. Crée une fonction qui permet de créer un inventaire unique et de manipuler cet inventaire.
Je t'aide un peu pour la définition :

```js
function creationInventaire() {
  const inventaire = [];

  return {
    ajoutPotion(potion) {
      // code de l'ajout de potion dans l'inventaire
    },
    lesPotionsEnStock() {
      // retourne la liste des potions en stocks
    },
    lesPotionsEnRuptureDeStock() {
      // retourne la liste des potions en rupture de stock
    },
  };
}

const inventaireBoutiquePotionsA = creationInventaire();
const inventaireBoutiquePotionsB = creationInventaire();
```

### Bonus, un sorcier a toujours la classe !

- Transforme la fonction de l'exercice précédent en une `class` avec des propriétés et des méthodes.
  - Cet exercice te fera découvrir une autre syntaxe qui rappelle la programmation orientée objet comme en Python, Java, PhP, C++, C#, etc.
  - Le comportement sera exactement le même que dans l'exercice précédent. Uniquement la syntaxe changera :)
