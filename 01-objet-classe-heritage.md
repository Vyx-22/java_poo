# 01 - Objet, classe, héritage

## Classe
Plan de construction. 

Définition : une classe est un modèle qui définit les attributs (données) et les méthodes (comportements) communs à un ensemble d'objets.

Elle définit :
- des attributs : ce que l'objet possède
- des méthodes : ce que l'objet sait faire

```java
class Vehicule {
    // attributs
    String nom;
    String marque;

    // constructeur
    public Vehicule(String nom, String marque) {
        this.nom = nom;
        this.marque = marque;
    }

    // méthodes
    public void avancer() {
        
    }
}
```

## Objet
Instance d'une classe, créée avec `new`. Chaque objet a ses propres valeurs.

```java
Vehicule maVoiture = new Vehicule("K41qs", "Toyota");
Vehicule taVoiture = new Vehicule("B72zz", "Peugeot");
maVoiture.avancer();
```

## Constructeur
Sert à créer un objet et à initialiser ses attributs.
- il porte exactement le même nom que la classe (majuscule comprise)
- il n'a aucun type de retour, même pas `void`
- il se trouve à l'intérieur de la classe
- `this.nom` désigne l'attribut de l'objet, `nom` seul désigne le paramètre

Piège : dès qu'on écrit un constructeur avec paramètres, `new Vehicule()` sans arguments ne compile plus. Java ne fournit un constructeur vide automatiquement que si la classe n'en a aucun.

## Héritage
Une classe enfant récupère automatiquement les attributs et les méthodes de sa classe mère, et peut ajouter les siens.

Test : la phrase « une Voiture est un Véhicule » doit être vraie. Sinon, pas d'héritage.

```java
class Voiture extends Vehicule {

    // constructeur
    public Voiture(String nom, String marque) {
        super(nom, marque);
    }

    // méthode propre à Voiture
    public void activeAirbag() {
        System.out.println("Airbag activé");
    }
}

class Moto extends Vehicule {

    // constructeur
    public Moto(String nom, String marque) {
        super(nom, marque);
    }

    // méthode propre à Moto
    public void deployerBequille() {
        System.out.println("Béquille déployée");
    }
}
```

Utilisation :
```java
Voiture v = new Voiture("K41qs", "Toyota");
v.avancer();        // hérité de Vehicule
v.activeAirbag();   // propre à Voiture
```

Règles à retenir :
- `extends` indique la classe mère
- `super(...)` appelle le constructeur de la mère, obligatoirement en première ligne
- si la mère n'a qu'un constructeur avec paramètres, l'enfant doit appeler `super(...)`, sinon erreur de compilation
- une méthode a toujours un corps `{ }`, même vide
- relation mère-fille, pas entre sœurs : `Moto` ne peut pas appeler `activeAirbag()`, car `Voiture` et `Moto` héritent toutes les deux de `Vehicule` sans hériter l'une de l'autre
- en Java, une classe n'a qu'une seule mère

