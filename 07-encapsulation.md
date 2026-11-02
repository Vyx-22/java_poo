# 07 - Encapsulation

## Encapsulation
Définition : l'encapsulation consiste à protéger les attributs d'une classe en les rendant inaccessibles depuis l'extérieur (`private`), et à contrôler leur accès par des méthodes publiques (getters et setters).

But : la classe décide de ce qu'elle accepte. Personne ne peut mettre une valeur invalide dans un attribut. C'est le principe de validation des entrées en cybersécurité.

## Visibilités

| Visibilité | La classe | Le package | Les filles | Tout le monde |
|---|---|---|---|---|
| `private` | oui | non | non | non |
| (rien) | oui | oui | non | non |
| `protected` | oui | oui | oui | non |
| `public` | oui | oui | oui | oui |

## Getter et setter
- getter : méthode qui retourne la valeur d'un attribut (il ne l'affiche pas)
- setter : méthode qui modifie un attribut, après vérification

```java
public class Joueur {

    private int essaisRestants;

    public int getEssaisRestants() {
        return this.essaisRestants;
    }

    public void setEssaisRestants(int essaisRestants) {
        if (essaisRestants >= 0) {
            this.essaisRestants = essaisRestants;
        }
    }
}
```

## Conventions
- attributs en `private`, getters et setters en `public`
- noms : `getNomAttribut` et `setNomAttribut`, exactement le nom de l'attribut
- le paramètre du setter porte le nom de l'attribut, `this` permet de les distinguer

## Pièges
- `private` ne veut pas dire « personne » : la classe elle-même y a accès
- préférer `int` à `Integer` pour un paramètre : `Integer` peut valoir `null` et faire planter le programme