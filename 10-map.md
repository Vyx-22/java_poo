# 10 - Map (HashMap et LinkedHashMap)

## Map
Définition : une `Map` est une structure qui associe des clés uniques à des valeurs. On accède à une valeur uniquement par sa clé, pas par une position.

Équivalent : tableau associatif en PHP, dictionnaire en Python.

```java
import java.util.HashMap;
import java.util.Map;

Map<String, String> dico = new HashMap<>();
dico.put("chat", "Animal qui miaule");
dico.put("java", "Langage de programmation");
```

`<String, String>` : type de la clé, puis type de la valeur.

## Méthodes principales
- `put(cle, valeur)` : ajouter, ou remplacer si la clé existe déjà
- `get(cle)` : récupérer la valeur (renvoie `null` si la clé n'existe pas)
- `containsKey(cle)` : vérifier qu'une clé existe
- `remove(cle)` : retirer
- `size()` : nombre d'associations
- `keySet()` : toutes les clés, sous forme de `Set`

## Parcourir une Map
On parcourt ses clés avec `keySet()`, puis on récupère chaque valeur avec `get()`.
```java
for (String mot : dico.keySet()) {
    System.out.println(mot + " : " + dico.get(mot));
}
```

## HashMap ou LinkedHashMap
- `HashMap` : ne garantit aucun ordre
- `LinkedHashMap` : garde l'ordre d'ajout

## Règles à retenir
- les clés sont uniques, les valeurs peuvent se répéter
- une `Map` n'a pas d'index : pas de `get(0)`
- une `Map` ne fait pas partie de l'interface `Collection`

## Pièges
- `put` sur une clé existante remplace la valeur sans prévenir
- `get` sur une clé absente renvoie `null`, qui fait planter le programme si on l'utilise : vérifier avec `containsKey()` avant