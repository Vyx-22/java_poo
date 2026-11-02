# 08 - Syntaxe de base

## Conditions

### if / else if / else
Définition : une structure conditionnelle exécute un bloc de code uniquement si une condition est vraie.

```java
if (note >= 16) {
    System.out.println("Très bien");
} else if (note >= 10) {
    System.out.println("Admis");
} else {
    System.out.println("Ajourné");
}
```

- condition entre parenthèses, code entre accolades
- `else if` en deux mots (pas `elif`, c'est du Python)

### Opérateurs
- comparaison : `==`, `!=`, `<`, `>`, `<=`, `>=`
- logique : `&&` (et), `||` (ou), `!` (non)

### Comparer des String
On n'utilise jamais `==`, toujours `.equals()`.
- `==` compare les références (le même objet en mémoire ?)
- `.equals()` compare le contenu (les mêmes lettres ?)
- `.equalsIgnoreCase()` compare le contenu sans tenir compte des majuscules

```java
"Chat".equals("chat")            // false
"Chat".equalsIgnoreCase("chat")  // true
```

### switch
Définition : le `switch` compare une variable à plusieurs valeurs précises et exécute le bloc correspondant.

```java
switch (choix) {
    case 1:
        System.out.println("Nouvelle partie");
        break;
    case 2:
        System.out.println("Voir les scores");
        break;
    default:
        System.out.println("Choix invalide");
}
```

Écriture courte (depuis Java 14), sans `break` :
```java
switch (choix) {
    case 1 -> System.out.println("Nouvelle partie");
    case 2 -> System.out.println("Voir les scores");
    default -> System.out.println("Choix invalide");
}
```

## Boucles
Définition : une boucle répète un bloc d'instructions tant qu'une condition est vraie.

### for
Quand on connaît le nombre de répétitions.
```java
for (int i = 0; i < 5; i++) {
    System.out.println("Tour " + i);
}
```
Trois parties : départ ; condition pour continuer ; changement à chaque tour.

### while
Tant que la condition est vraie, sans connaître le nombre de tours. Peut ne jamais s'exécuter.
```java
while (essais > 0) {
    essais--;
}
```

### do while
La condition est vérifiée à la fin : le bloc s'exécute au moins une fois.
```java
do {
    // jouer une partie
} while (veutRejouer);
```

### for-each
Parcourt tous les éléments d'un tableau ou d'une liste.
```java
for (String mot : mots) {
    System.out.println(mot);
}
```

### break et continue
- `break` : sort immédiatement de la boucle (ou du `switch`)
- `continue` : passe directement au tour suivant

## Pièges
- comparer des String avec `==` : le résultat peut être faux même si les mots sont identiques
- oublier `break` dans un `switch` classique : Java exécute aussi les `case` suivants (fall-through)
- boucle infinie : oublier de modifier la variable de la condition
- décalage d'un tour : `i <= 5` fait un tour de plus que `i < 5`
- `while` peut faire zéro tour, `do while` en fait toujours au moins un