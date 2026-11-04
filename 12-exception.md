# 12 - Exception (try, catch, finally)

## Exception
Définition : une exception est un événement anormal qui survient pendant l'exécution et interrompt le déroulement normal du programme. Si elle n'est pas gérée, le programme s'arrête (il plante).

Causes possibles :
- extérieures : fichier introuvable, saisie invalide de l'utilisateur
- internes : division par zéro, `null` utilisé, index hors de la liste

## try, catch, finally
- `try` : contient le code qui risque de provoquer une exception
- `catch` : s'exécute uniquement si l'exception indiquée se produit
- `finally` : s'exécute dans tous les cas, exception ou non

```java
try {
    int choix = Integer.parseInt(clavier.nextLine());
} catch (NumberFormatException e) {
    System.out.println("Merci de taper un nombre");
} finally {
    System.out.println("Fin de la saisie");
}
```

Dès qu'une exception survient dans le `try`, le reste du `try` est ignoré et Java saute au `catch`.

## Deux familles
- non vérifiées (unchecked) : la gestion n'est pas obligatoire. Ex : `NumberFormatException`, `NullPointerException`, `ArithmeticException`
- vérifiées (checked) : Java refuse de compiler si elles ne sont pas gérées. Ex : `FileNotFoundException`

## Pièges
- les lignes du `try` situées après l'erreur ne sont jamais exécutées
- un `catch` n'attrape que le type d'exception indiqué
- `Integer.parseInt("abc")` provoque une `NumberFormatException` : toujours protéger la saisie du joueur