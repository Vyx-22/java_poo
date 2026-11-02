# 05 - Méthode

## Méthode
Définition : une méthode est un sous-programme défini dans une classe, qui regroupe des instructions exécutées lorsqu'on l'appelle.

Elle est composée de :
- sa visibilité (`public`, `private`...)
- son type de retour (`int`, `String`, `void`...)
- son nom
- ses paramètres
- son corps (le code entre `{ }`)

```java
public int additionner(int a, int b) {
    return a + b;
}
```

## Signature
Définition : la signature d'une méthode est formée de son nom et de la liste des types de ses paramètres.
La visibilité et le type de retour n'en font pas partie.
Ici : `additionner(int, int)`

## void ou type de retour
- `void` : la méthode ne retourne rien (une procédure en algorithmique)
- un type (`int`, `String`...) : la méthode retourne une valeur de ce type (une fonction en algorithmique)

## return
- renvoie une valeur au code qui a appelé la méthode
- arrête immédiatement la méthode, la suite n'est pas exécutée
- dans une méthode `void`, `return;` seul permet de sortir plus tôt

## Paramètre ou argument
- paramètre : la variable déclarée dans la méthode (`int a`)
- argument : la valeur passée lors de l'appel (`additionner(3, 5)`)

## Pièges
- une méthode avec un type de retour doit obligatoirement contenir un `return`, sinon erreur de compilation
- afficher n'est pas retourner : `System.out.println` montre la valeur à l'écran, mais le programme ne peut pas la récupérer