# 04 - Interface

## Interface

Définition : une interface est un ensemble de méthodes abstraites qui définit un contrat. Toute classe qui l'implémente avec `implements` doit définir ces méthodes.


Une interface est un contrat qui liste des compétences. Si une classe signe le contrat, elle doit obligatoirement savoir faire ces compétences.

L'interface dit quoi faire, jamais comment.

```java
interface Rechargeable {
    void recharger();
}

interface Connectable {
    void seConnecter();
}

class Voiture extends Vehicule implements Rechargeable, Connectable {
    // doit définir avancer(), recharger() et seConnecter()
}

class Telephone implements Rechargeable {
    @Override
    public void recharger() {
        System.out.println("Le téléphone se recharge");
    }
}
```

## Classe abstraite ou interface
- classe abstraite : ce que je suis (une Voiture est un Véhicule)
- interface : ce que je sais faire (une Voiture sait se recharger)
- une seule mère avec `extends`, plusieurs contrats avec `implements`
- n'importe quelle classe peut signer un contrat, même sans lien de parenté

## Règles à retenir
- mot-clé : `implements` (avec un s)
- pas d'attributs normaux, seulement des constantes (automatiquement `public static final`)
- on ne peut pas faire `new` sur une interface
- depuis Java 8, une interface peut contenir des méthodes avec du code (`default`)