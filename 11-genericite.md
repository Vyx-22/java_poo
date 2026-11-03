# 11 - Généricité

## Généricité
Définition : la généricité permet d'écrire une classe ou une méthode qui fonctionne avec n'importe quel type, en indiquant ce type entre chevrons `< >` au moment de l'utilisation.

Deux intérêts :
- éviter la répétition de code : une seule classe au lieu d'une par type
- la sécurité des types : une erreur de type est détectée à la compilation, pas à l'exécution

```java
class Boite<T> {
    private T contenu;

    public Boite(T contenu) {
        this.contenu = contenu;
    }

    public T getContenu() {
        return contenu;
    }
}

Boite<String> b1 = new Boite<>("chat");
Boite<Integer> b2 = new Boite<>(42);
String mot = b1.getContenu();
```

`T` est remplacé par le vrai type au moment de l'utilisation.

## Vocabulaire
- chevrons : les signes `< >`
- diamant : `<>` vide dans `new Boite<>()`, Java devine le type
- conventions de nommage : `T` (type), `E` (élément), `K` (clé), `V` (valeur)

## Règles à retenir
- tu l'utilises déjà : `List<String>`, `Map<String, String>` sont des classes génériques
- seulement des objets entre chevrons : `Boite<Integer>`, jamais `Boite<int>`

## Pièges
- `Boite<String> b = new Boite<>(42);` ne compile pas : la boîte attend un `String`