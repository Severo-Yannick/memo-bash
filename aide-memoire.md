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