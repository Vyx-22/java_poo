# 02 - Variable et référence

## Variable
Une boîte avec un nom. Une variable n'est pas un objet.
- pour un nombre, la boîte contient directement la valeur
- pour un objet, la boîte contient son adresse en mémoire : c'est la référence

Image : la référence, c'est le contact « Maman » dans le téléphone. Ce n'est pas ma mère, c'est son numéro.

## Copie
```java
int a = 20;
int b = a;      // copie de la valeur
b = 50;         // a vaut toujours 20

Vehicule v1 = new Vehicule("K41qs", "Toyota");
Vehicule v2 = v1;   // copie de la référence, pas de l'objet
v2.nom = "Z99";     // v1.nom vaut aussi "Z99"
```

## Règles à retenir
- autant de `new`, autant d'objets
- `=` entre deux objets copie la référence, jamais l'objet
- deux objets créés avec les mêmes valeurs restent deux objets distincts (des jumelles)

## Types primitifs
Ils contiennent directement une valeur. On peut calculer et comparer avec eux, mais ils n'ont pas de méthodes.

| Type | Taille | Contient |
|---|---|---|
| `byte` | 8 bits | entier de -128 à 127 |
| `short` | 16 bits | entier de -32 768 à 32 767 |
| `int` | 32 bits | entier jusqu'à environ ±2,1 milliards |
| `long` | 64 bits | très grand entier, s'écrit avec `L` : `5000000000L` |
| `float` | 32 bits | décimal peu précis, s'écrit avec `f` : `3.14f` |
| `double` | 64 bits | décimal précis, le type par défaut |
| `char` | 16 bits | un caractère, entre apostrophes : `'A'` |
| `boolean` | non fixé | `true` ou `false` |

Usage courant : `int` (âge), `double` (prix), `boolean` (connecté ou pas), `char` (une lettre).

## Primitif ou référence
- primitif : la variable contient la valeur, la copie duplique la valeur
- référence : la variable contient l'adresse de l'objet, la copie duplique l'adresse
- `String` n'est pas un primitif, c'est une classe (majuscule)

## Pièges
- dépassement : `int` à 2147483647, plus 1, donne -2147483648, sans aucune erreur. C'est une faille connue en sécurité (integer overflow)
- `double` fait des erreurs d'arrondi (`0.1 + 0.2` donne `0.30000000000000004`). Pour l'argent en vrai projet, on utilise `BigDecimal`

## Constante (final)
Une variable `final` ne peut plus être modifiée après son initialisation. Toute modification provoque une erreur de compilation.

```java
public static final int MAX_ESSAIS = 6;
```

Conventions :
- nom en MAJUSCULES, mots séparés par `_`
- les vraies constantes s'écrivent `static final` (elles appartiennent à la classe)

Piège avec les références : `final` bloque la variable, pas l'objet.
```java
final int[] notes = {10, 12};
notes[0] = 15;         // autorisé : on modifie l'objet
notes = new int[3];    // erreur : on change la référence
```