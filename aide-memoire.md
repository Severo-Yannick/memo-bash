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

```nm <fich> (Names)``` : affiche la table des symboles de ```<fich>``` <br>(si c’est un fichier objet ou exécutable).

```od <fich> (Octal Dump)``` : affiche le contenu du fichier en octal (par défaut) ou avec d’autres codages
(hexadécimal, ASCII,. . .). Utile pour visualiser des fichiers binaires.

## 3 - Aides

```man <section> <commande>``` : affiche la page du manuel de la commande ```<commande>```. <br> Le paramètre ```<section>``` est facultatif il permet de spécifier la section du manuel ou de rechercher la commande.

```apropos <mot>``` : recherche une page de manuel contenant le mot dans sa description résumée.

```info``` : présente les pages d’infos qui sont en général plus détaillées et plus lisibles que les pages du manuel. Ces pages sont structurées en arbre. <br>Le plus simple est de les visualiser dans ```emacs``` : dans ```emacs``` taper Ctrl - h i . La plupart des commande présentées dans ce document sont accessible dans la section ```CoreUtils```.

## 4 - Gestion des permissions

```chmod <mode> <fich1 ou rep1> <fich2 ou rep2>``` (```Ch```ange ```m```ode) : Modifie les permissions d’accés de chacun des fichiers et répertoires indiqués, en suivant l’indication donne par ```<mode>```. Ce ```<mode>``` est :<br>
· soit un nombre octal de 3 chiffres représentant les nouvelles permissions. <br>Le tableau ci-dessous indique la correspondance des chiffres avec les droits.

### Table 1 – Correspondances de représentation des droits

| Droit | Valeur alphanumérique | Valeur octale |
|---|---|---|
| aucun droit | —— | 0 |
| écution seulement | -x  | 1 |
| écriture seulement | -w- | 2 |
| écriture et exécution | -wx- | 3 |
| lecture seulement | r- | 4 |
| lecture et exécution | r-x | 5 |
| lecture et écriture | r-w | 6 |
| tous les droits (lecture,  écriture et exécution) | rwx | 7 |

. soit une représentation symbolique du changement à effectuer, de la forme ```CSP``` où :<br>
- ```C``` est une suite de lettres indiquant à quelle(s) catégorie(s) d’utilisateurs s’applique les modifications de droits. Les choix possibles sont :<br>
```’u’ (user)``` pour le propriétaire ;<br>
```’g’ (group)``` pour le groupe d’utilisateurs ;<br>
```’o’ (other)``` pour les autres utilisateurs ;<br>
```’a’ (all)``` pour tous les utilisateurs.<br>
- ```S``` peut prendre comme valeur :<br>
```’+’``` pour ajouter des droits ;<br>
```’-’``` pour enlever des droits.<br>
- ```P``` est une suite de lettres indiquant quels sont les droits modifiés :<br>
```’r’ (read)``` pour la lecture ;<br>
```’w’ (write)``` pour l’ ́ecriture ;<br>
```’x’ (execute)``` pour l’execution.<br>
Exemples :<br>
· chmod 744 toto (mode numérique)<br>
· chmod ug+rw titi (mode symbolique) : il faut rajouter des droits (+) en lecture et  écriture (rw) au
propriétaire et au groupe (ug).

## 5 - Opérations sur les chemins

Les opérations suivantes sont principalement utiles dans les scripts.<br>
```basename <chemin>``` : affiche le nom seul du fichier indiqué par ```<chemin>```.<br>
Exemple : basename /app/src/component.js affiche component.js<br>
```dirname <chemin>``` : affiche le nom des répertoires.<br>
Exemple : dirname /app/src/component.js affiche /app/src<br>
```realink -f <chemin>``` : affiche le chemin absolu correspondant au chemin ```<chemin>```.

## 6 - Commandes sur les processus

```ps (Processus Status)``` : affiche des informations sur les processus en cours d’exécution.<br>
Exemples :<br>
· ```ps x``` : tous les processus de l’utilisateur.<br>
· ```ps ax``` : tous les processus de tous les utilisateur.

```pstree``` : affiche l’arbre des processus.<br>

```top``` : affiche en vue temps réel, les processus actuellement dans le système, avec des informations sur l’utilisateur de la mémoire, du processeur, etc. La vue est actualisée périodiquement.<br>
```h``` : affiche l’aide de top.<br>
```s``` : modifie la p ́eriode de rafraichissment (par d ́efaut : 3 s).<br>
```u``` : affiche seulement les processus d’un utilisateur particulier.<br>
```k``` : envoie un signal à un processus (comme la commande kill).<br>
```r``` : change le nice d’un processus.<br>

```kill <PID>``` : tue le processus de ```PID``` indiqué (pour utiliser le PID d’un processus, utiliser ```top``` ou ```ps```).<br> 
Options :<br>
```-s <signal>``` : envoie le signal ```<signal>``` au processus au lieu de le tuer.<br>
```-l``` : affiche la liste des signaux disponibles.

```killall <prog>``` : tue tous les processus de nom ```<prog>```.<br>
Option :<br>
```-s <signal>``` : envoie le signal ```<signal>``` aux processus au lieu de les tuer.

```nice +<valeur> <commande>``` : lance la commande ```<commande>``` avec un niveau de nice égal à ```<valeur>```.<br>
Exemple : nice +15 emacs

## 7 - Autres commandes

```time <commande>``` : exécute la ```<commande>``` et affiche le temps utilisée par celle-ci.<br>
```date``` : affiche la date et l’heure.<br>
```bc (Basic Calculator)``` : calculatrice.

```find <rep> <expression>``` : recherche les fichiers ou les repertoires satisfaisant ```<expression>``` dans l’arborescence de racine ```<rep>```.<br>
Options (voir la page de manuel pour d’autres options) :<br>
```-name``` : recherche par nom de fichier.<br>
```-type``` : recherche par type de fichier.<br>
```-size``` : recherche par taille de fichier.<br>
Exemples :<br>
```find toto -name "hop"``` : recherche les fichiers ou répertoires de nom ```hop``` dans l’arborescence de
racine ```toto```.<br>
```find 􏰀 -name "*.txt"``` : recherche les fichiers ou répertoires dont le nom se fini par ```.txt``` dans
l’arborescence du répertoire courant.<br>
```find 􏰀 -type f``` : recherche les fichiers dans l'arborescence de racine le répertoire courant.
On peut évidemment combiner les critères.

```du (Disk Usage)``` : affiche la taille (en ko) de tous les répertoires et sous-répertoires du répertoire courant.<br>
On peut l’utiliser dans un tube avec sort pour trier les résultats : ```du | sort -n```.

## 8 - Commandes internes

Les commandes internes sont fournies par le shell bash lui-même. Pour plus d'informations sur ces commandes, lire la page ```man``` de ```bash```. Certaines de ces commandes sont réelement utiles que dans un script.

```echo <chaine>``` : affiche la ```<chaine>``` sur la sortie standart suivi d’un retour à la ligne.<br>
Option :<br>
```-n``` : pas de retour à la ligne.

```read <variable>``` : permet de mettre ce qui est lu sur l’entrée standard (via echo)
dans la variable ```<variable>```.<br>
voir section 9.1.

```shift <n>``` : décale les paramètres de ```<n>``` positions vers la gauche <br>
```<n>``` est facultatif, il vaut 1 par défaut.<br>
<b>Exemple</b> : Soit $1="un", $2="six", $3="toto" et $4="hop". Après la commande shift, on a $1="6",
$2="toto", $3="hop" et $4 est vide.

```exit <n>``` : termine un script avec comme code de retour ```<n>```.

```time <commande>``` : exécute la ```<commande>``` et affiche le temps utilisée par celle-ci.

## 9 - Script bash

Un script bash commence toujours par la ligne :<br>
#!/usr/bin/env bash <br>
Les scripts peuvent comporter des commentaires qui sont introduits par le caratère ``#``.

### 9.1 Variables

Les variables (ou les variables d’environement) du shell sont de type chaine de caractères ou entier.<br>
On peut leur affecter :<br>

• Des valeurs constantes :<br>
```a="bonjour"```<br>
```b=34```<br>

• Le contenu d’une autre variable ou variable d’environnement : <br>
```aa="$a $USER, ca va bien ?"```<br>

• Le résultat d’un calcul avec ```$(( ))``` (attention, le shell ne gère QUE les entiers) :<br>
```c=$((324 * 432 - $b ))```

• le résultat d’une commande avec ```$( )``` :

```bb=$(ls *.txt)```
```bb=$(ls *.txt | wc -l)```

Par exemple on peut récupérer le contenu d’un fichier comme suit :<br>
```bb=$(cat nom_fichier)```

• ce qui est lu sur l’entrée standard en utilisant read :<br>
```echo "age ?"; read n; echo "vous avez $n ans."```<br>
(met ce qui est lu sur l’entrée standard dans la variable n)<br>
<b>ATTENTION</b> : Ne pas mettre d’espaces avant et après le signe =.

### 9.1.1 Variables spéciales (dans un script)
• ```$0``` : nom de la commande<br>
• ```$1, $2, $3```,. . . : paramètres<br>
• ```"$@" ou $*``` : liste de tous les paramètres à partir de ```$1```<br>
• ```$#``` : nombre de param`etres (sans compter ```$0```)

### 9.1.2 Guillemets
• Le guillemet simple ’ dénote une chaîne dans laquelle **aucune** substitution de variables n’est faite.<br>
• Le guillemet double ” dénote une chaîne dans laquelle **toutes** les substitutions de variables sont faites.<br>
Exemple :<br>
```bash
morvant:~/Documents> ch1="Bonjour $USER"
morvant:~/Documents> ch2=’BONJOUR $USER’
morvant:~/Documents> echo $ch1
Bonjour morvant
morvant:~/Documents> echo $ch2
Bonjour $USER
```

### 9.1.3 Portée des variables
Une variable est locale à son interpréteur. Pour la rendre visible aux processus fils de l’interpréteur qui l’a définie, il faut l’**exporter** comme suit.<br>
```bash
export ma_variable
```

### 9.2 Conditionnelle
La syntaxe des conditionnelles est :<br>
```bash
if <commande>
then
    <liste de commandes1>
else
    <liste de commandes2>  # facultatif
fi;
```

***ATTENTION*** : Si on met sur la même ligne les mots-clés ```if```, ```then``` et/ou ```fi``` il faut mettre un point-virgule ```;``` séparateur.<br>
```bash
if <commande> ; then <liste de commandes1> ;else <liste de commandes2>; fi

Si <commande> renvoie un code de retour égal à 0 alors <liste de commande1> est exécutée sinon <liste de commande2> (s’il y a un else). <commande> peut être un test (c.f. section 9.5).
```
***Exemple*** :
```bash
if grep -q voiture fich; then echo "c’est vrai"; else echo "c’est faux"; fi
```
