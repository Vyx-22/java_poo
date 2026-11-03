# 09 - Collections (List et Set)

## Collection
Définition : une collection est un objet qui regroupe plusieurs éléments du même type, et dont la taille s'adapte automatiquement quand on ajoute ou retire des éléments.

Avantage sur un tableau : la taille d'un tableau est fixée à sa création, celle d'une collection ne l'est pas.

## List
Définition : une `List` est une collection ordonnée, où chaque élément a une position (index, qui commence à 0), et qui accepte les doublons.

```java
import java.util.ArrayList;
import java.util.List;

List<String> mots = new ArrayList<>();
mots.add("chat");
mots.add("java");
mots.get(0);             // "chat"
mots.contains("java");   // true
mots.size();             // 2
mots.remove("java");
```

## Set
Définition : un `Set` est une collection qui refuse les doublons. Dans sa version courante (`HashSet`), il n'a pas d'ordre ni d'index.

```java
import java.util.HashSet;
import java.util.Set;

Set<String> lettresProposees = new HashSet<>();
lettresProposees.add("e");
lettresProposees.add("e");          // ignoré : doublon
lettresProposees.contains("e");     // true
```

## Méthodes principales
- `add()` : ajouter
- `remove()` : retirer
- `contains()` : vérifier la présence
- `size()` : nombre d'éléments
- `get(index)` : récupérer par position (List uniquement)

## Règles à retenir
- `List` et `Set` sont des interfaces, `ArrayList` et `HashSet` les classes qui les implémentent
- on déclare avec l'interface, on crée avec la classe : `List<String> l = new ArrayList<>();`
- `<String>` indique le type des éléments
- une collection ne contient que des objets : `List<Integer>`, jamais `List<int>`

## Pièges
- `Set<String> s = new ArrayList<>();` ne compile pas : `ArrayList` est une List, pas un Set
- oublier `()` après `new HashSet<>`
- `contains(e)` sans guillemets cherche une variable `e`, pas le texte "e"