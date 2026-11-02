# 06 - Surcharge et polymorphisme

## Surcharge
Définition : la surcharge consiste à définir, dans une même classe, plusieurs méthodes portant le même nom mais avec des paramètres différents (en nombre, en type ou en ordre).

Java choisit la bonne version à la compilation, selon les arguments passés.

```java
public int additionner(int a, int b) { return a + b; }
public int additionner(int a, int b, int c) { return a + b + c; }
public double additionner(double a, double b) { return a + b; }
```

Piège : changer seulement le type de retour ne suffit pas, puisqu'il ne fait pas partie de la signature.

## Redéfinition
Définition : la redéfinition consiste, pour une classe fille, à réécrire une méthode héritée de sa mère, avec exactement la même signature. On la signale avec `@Override`.

## Polymorphisme
Définition : le polymorphisme est la capacité d'une variable du type de la classe mère à contenir un objet d'une classe fille, et d'appeler automatiquement la version redéfinie de la méthode correspondant à l'objet réel.

Polymorphisme veut dire « plusieurs formes » : une même instruction produit des comportements différents selon l'objet.

```java
Vehicule v1 = new Voiture("A1");
Vehicule v2 = new Moto("B2");
v1.avancer();   // version de Voiture
v2.avancer();   // version de Moto
```

- type déclaré : le type de la variable (`Vehicule`)
- type réel : le type de l'objet créé avec `new` (`Moto`)
- c'est le type réel qui décide quelle méthode est exécutée, à l'exécution

## Différences

| | Surcharge | Redéfinition (polymorphisme) |
|---|---|---|
| Signature | différente | identique |
| Où | même classe | mère et fille |
| Choix de la méthode | à la compilation | à l'exécution |