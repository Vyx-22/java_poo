# 02 - Variable et référence

## Variable
Une boîte avec un nom. Une variable n'est pas un objet.
- pour un nombre, la boîte contient directement la valeur
- pour un objet, la boîte contient son adresse en mémoire : c'est la référence

Image : la référence, c'est le contact « Maman » dans le téléphone. Ce n'est pas ma mère, c'est son numéro.

## Copie
```java
int a = 20;
int b = a;      // copie de la valeur
b = 50;         // a vaut toujours 20

Vehicule v1 = new Vehicule("K41qs", "Toyota");
Vehicule v2 = v1;   // copie de la référence, pas de l'objet
v2.nom = "Z99";     // v1.nom vaut aussi "Z99"
```

## Règles à retenir
- autant de `new`, autant d'objets
- `=` entre deux objets copie la référence, jamais l'objet
- deux objets créés avec les mêmes valeurs restent deux objets distincts (des jumelles)