# Aide-mémoire — Commandes et scripts Bash

### Avant-propos.
Toutes les options ne sont pas indiquées. Pour plus de détails, se référencer aux pages de manuel (cf la commande ```man```). Une commande interne est une commande fournie par le shell bash, il faut alors regarder la page de manuel du shell.
Dans la suite, ```<fich>``` est le chemin (absolu ou relatif) d’un fichier, ```<rep>``` est le chemin (absolu ou relatif) d’un répertoire.

## 1 - Commandes de gestion des fichiers et répertoires
```ls``` : Liste le contenu d’un répertoire. Si aucun argument n’est donné, c’est le contenu du répertoire courant qui est affiché. Sinon, c’est le contenu des répertoires indiqués en paramètres qui est listé. 
```Options``` :<br>
```-a``` : liste également les fichiers et répertoires cachés (dont le nom commence par un point ```.```).<br>
```-l``` : liste en plus les attibuts des fichiers.<br>
```-h``` : avec ```-l``` donne les tailles des fichiers sous une forme plus lisible.

```cd (Change Directory)``` : Change le dossier/répertoire courant. Commande interne.<br>
Exemples :<br>
```cd <rep>``` : se déplace dans le répertoire indiqué en paramètre.<br>
```cd``` : se déplace dans le répertoire personnel (/)<br>
```cd ..``` : remonte dans le répertoire supérieur/parent.<br>
```cd -``` : se déplace dans le dernier répertoire visité.

```mkdir <rep1> <rep2>```: (Make Directory) créer les répertoires indiqués en parmètre (au moins un)  Les répertoires pères de ```<rep1> <rep2>``` doivent déjà exister.
```Options``` :<br>
```-p``` : si les répertoires pères n’existent pas, ils sont également créés.

```rmdir <rep1> <rep2>: ```(Remove Directory) supprime les répertoires indiqués (au moins un). Les
répertoires doivent être vides.

```rm <fich1> <fich2>``` (Remove) supprime les fichiers passés en paramètres. ATTENTION : aucun moyen de les récupérer par la suite.<br>
Options :<br>
```-i``` : demande confirmation avant chaque effacement.<br>
```-f``` : ne demande jamais de confirmation<br>
```-r``` : effacement récursif. Exemple : ```rm -r <rep1> <rep2>``` permet d’effacer les répertoires indiqués ainsi que tout ce qu’ils contiennent définitivement.

```cp``` (Copy) copie de fichiers et de répertoires.<br>
Utilisation :<br>
```cp <fich1> <fich2>```: crée un nouveau fichier de chemin ```<fich2>``` et copie dedans le contenu de ```<fich1>```dans  ``` <fich2>```. Si ```<fich2>``` existait déjà, il est écrasé.<br>
```cp <fich1> <fich2>``` ...```<rep>``` : copie dans le répertoire ```<rep>``` les fichiers indiqués en paramètres. ```<rep>``` doit déjà exister.<br>
```cp -r <rep1> <rep2>``` : si ```<rep2>``` existe, alors copie récursivement dedans le répertoire ```<rep1>``` et tout son contenu. Sinon, il crée le répertoire ```<rep2>``` et copie dedans tout le contenu de ```<rep1>```.

```mv``` (Move) déplace/renomme des fichiers et des répertoires.<br>
Utilisation :<br>
```mv <fich1> <fich2>``` : déplace le fichier ```<fich1>``` pour que son chemin devienne ```<fich2>```.<br>
```mv <fich1 ou rep1> <fich2 ou rep2>``` ...```<rep>``` : déplace, dans le répertoire ```<rep>```, les fichiers ou répertoires indiqués en paramètre. ```<rep>``` doit exister.<br>
```mv <rep1> <rep2>``` : si le répertoire ```<rep2>``` existe, alors il déplace ```<rep1>``` dedans. Sinon, il déplace le
répertoire <rep1> pour que son chemin devienne <rep2>.

```ln <fich1> <fich2>``` (Link) crée un lien physique du fichier <fich1> vers <fich2>.<br>
Option :
```-s``` : créer un lien symbolique au lieu d’un lien physique.

```touch <fich1> <fich2>``` créer des fichiers vides. Si les fichiers existent déjà, alors leur date de dernière modification est mise à la date courante.

```tar, zip, unzip``` créer une archive ou extraire des fichiers d’une archive (voir les pages du man).

```gzip <fich>, gunzip <fich>``` compresser ou décompresser un fichier.

```diff <fich1> <fich2>``` affiche les différences de lignes entre les arguments. Fonctionne également pour les répertoires.

## 2 - Commandes de gestion des fichiers et répertoires

Pour toutes les commandes suivantes :<br>
􏰀→ si aucun chemin de fichier n’est donné en paramètre, la commande lit son entrée standard
```(stdin)``` ;<br>
􏰀→ le résultat de la commande est afficher sur sa sortie standard ```(stdout)```.

```cat <fich1> <fich2>``` (Catenate) : Affiche le contenu du (ou des) fichiers les uns à la suite des autres.

```wc <fich>``` (Word Count) compte le nombre de lignes, mots et caractères d’un texte.<br>
Options :<br>
```-l``` (Line) : le nombre de lignes.<br>
```-c```(Character) : le nombre de caract`eres.<br>
```-w``` (Word) : le nombre de mots.<br>

```head -n <nb> <fich>``` extraire les ```<nb>``` premières lignes.

```tail -n <nb> <fich>``` extraire les ```<nb>``` dernières lignes. Si ```<nb>```est de la forme +n, alors extraire à partir de la n-ième ligne.

```grep <motif> <fich>``` (Global Regular Expression Print) afficher les lignes contenant le <motif>.<br> Options : <br>
```-c``` : afficher le nombre de lignes contenant le ```<motif>```.<br>
```-n``` : afficher en plus le numéro de la ligne.<br>
```-v``` : afficher les lignes qui ne contiennent pas le ```<motif>```.<br>

```cut <colonnes> <fich>``` extrait certaines parties dans chaque ligne.<br>
Options : <br>
```-c``` : indique la ou les positions des parties à extraire.<br>
```-f``` : indique un numéro de champ.<br>
```-d``` : indique un caractère d ́elimiteur de champ.<br>
Exemples :<br>
```cut -c5-15,33-37-``` : extraire dans chaque ligne les caractères 5 à 15, le caractères 33 et les caractères de 37 jusqu'a la fin de la ligne.<br>
```cut -d’’,’’ -f3-5``` : extraire les champs 3 à 5 de chaque ligne en utilisant le caractère “,” comme délimiteur de champ.

```tr <liste1> <liste2>``` (Transform), ou` ```<liste1>``` et ```<liste2>``` sont des listes de caractères : Remplace les caractères de ```<liste1>``` par le caractère à la même position dans ```<liste2>```. Cette commande lit sur l’entrée standard ```stdin``` et envoie le résultat sur la sortie standard ```stdout```.<br>
Options :<br>
```tr -d <liste>``` : supprime de ```stdin``` tous les caractères de ```<liste>```.<br>
```tr -s <liste>``` : supprime de ```stdout``` toutes les répétitions des caractères de ```<liste>```.<br>
N.B. : Les listes de caractères peuvent se définir en les écrivant entre guillemets ou en utilisant des listes préd ́efinies (voir la page de man).

```sort <fich>``` : trie les lignes par ordre alphabétique croissant.<br> 
Options :<br>
```-r``` : tri décroissant.<br>
```-n``` : suppose que les lignes commencent par un nombre, trie en utilisant la valeur de ce nombre.

```more``` : affiche le contenu d’un fichier page par page. La touche ```espace``` permet de passer à la page suivante.<br>
La touche ```q``` permet de quitter.

```less``` : affiche le contenu d’un fichier page par page. Les touches ```↑``` et ```↓```
dans le texte .<br>
La touche ```/``` permet de rentrer au clavier une chaîne à rechercher dans le texte et les touches ```n``` et ```N``` permettent de se déplacer sur les diff ́erentes occurences de la chaîne.<br>
La touche ```q``` permet de quitter.

```which <fich>``` : localise la commande ```fich```.

```file <fich>``` : donne le type de ```fichier```.

```strings <fich>``` : affiche les chaînes de caractères affichables contenues dans ```<fich>``` <br>(principalement utilisé pour récupèrer les chaînes contenues dans les fichiers non-ASCII).