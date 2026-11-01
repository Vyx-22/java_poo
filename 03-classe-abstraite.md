# 03 - Classe abstraite

## Classe abstraite
Classe déclarée avec `abstract`. On ne peut pas créer d'objet avec `new` à partir d'elle.
Elle sert de modèle commun quand l'objet « général » n'a pas de sens : on ne conduit pas un véhicule, on conduit une voiture ou une moto.

Elle peut contenir des attributs, un constructeur, des méthodes normales et des méthodes abstraites.

## Méthode abstraite
Méthode déclarée avec `abstract`, sans corps, terminée par `;`.
Chaque enfant doit obligatoirement la redéfinir, à sa manière.

```java
abstract class Vehicule {
    String nom;

    public Vehicule(String nom) {
        this.nom = nom;
    }

    public abstract void avancer();
}

class Voiture extends Vehicule {
    public Voiture(String nom) {
        super(nom);
    }

    @Override
    public void avancer() {
        System.out.println("La voiture roule");
    }
}
```

## Règles à retenir
- une classe qui contient une méthode abstraite doit être abstraite (l'inverse n'est pas obligatoire)
- un enfant qui ne redéfinit pas une méthode abstraite provoque une erreur, sauf s'il est lui-même abstrait
- `@Override` est facultatif mais conseillé : Java vérifie qu'on redéfinit bien une méthode existante
- `new Vehicule(...)` est interdit si `Vehicule` est abstraite