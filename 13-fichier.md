# 13 - Fichier (File, Reader, Writer, Buffer)

## Lire et écrire un fichier
Définition : Java lit et écrit des fichiers texte grâce à des classes dédiées : `FileReader` pour lire, `FileWriter` pour écrire.

## Pourquoi un buffer
Lire un fichier caractère par caractère oblige à accéder au disque en permanence, ce qui coûte beaucoup de ressources.
Un buffer (mémoire tampon) charge un gros morceau du fichier d'un coup, puis le programme y pioche. Beaucoup moins d'accès au disque.
- `BufferedReader` enveloppe un `FileReader`
- `BufferedWriter` enveloppe un `FileWriter`

## Lire ligne par ligne
```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

try (BufferedReader lecteur = new BufferedReader(new FileReader("mots.txt"))) {
    String ligne;
    while ((ligne = lecteur.readLine()) != null) {
        System.out.println(ligne);
    }
} catch (IOException e) {
    System.out.println("Impossible de lire le fichier");
}
```
`readLine()` renvoie `null` quand il n'y a plus de ligne : c'est ce qui arrête la boucle.

## Écrire dans un fichier
```java
try (BufferedWriter ecrivain = new BufferedWriter(new FileWriter("scores.txt"))) {
    ecrivain.write("Riri : 8 points");
    ecrivain.newLine();
} catch (IOException e) {
    System.out.println("Impossible d'écrire");
}
```

## try-with-resources
Les parenthèses après `try` ouvrent le fichier et le ferment automatiquement à la fin, même en cas d'erreur. Pas besoin de `close()` ni de `finally`.

## Règles à retenir
- les erreurs de fichier (`IOException`, `FileNotFoundException`) sont des exceptions vérifiées : Java oblige à les gérer
- le chemin du fichier est relatif au dossier depuis lequel on lance le programme

## Pièges
- `new FileWriter("scores.txt")` efface le contenu existant. Pour ajouter à la fin : `new FileWriter("scores.txt", true)`
- oublier de fermer un fichier : utiliser try-with-resources