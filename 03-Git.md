# Git


<div id="toc_container" style="background-color: #f7faff;">
<div id="toc-wrapper" style="margin-left: auto;margin-right: auto; width: 40%;">
<p class="toc_title"><strong>Sommaire du chapitre</strong></p>
<p><a href="Readme.md">Retour au sommaire</a></p>
<ol class="toc_list" start="1">
  <li><a href="02-Installation.md">Installer cette stack</a></li>
  <li><a href="03-Git.md">Git</a></li>
  <ol>
    <li><a href="03-Git.md/#pourquoigit">Pourquoi on s'emm**** avec git ?</a></li>
      <ol>
        <li><a href="03-Git.md/#backtothefutur">Le cas de retour vers le futur</a></li>
        <li><a href="03-Git.md/#CasGit">Le cas avec git</a></li>
      </ol>
    <li><a href="03-Git.md/#FonctionnementGit">Le fonctionnement de Git</a></li>
      <ol>
        <li><a href="03-Git.md/#GitSpaces">Les différents espaces de Git</a></li>
        <li><a href="03-Git.md/#EspaceTravail">Espace de travail</a></li>
        <li><a href="03-Git.md/#Index">Index</a></li>
        <li><a href="03-Git.md/#DepotLocal">Dépôt Local</a></li>
        <li><a href="03-Git.md/#DepotDistant">Dépôt Distant</a></li>
      </ol>  
  </ol>
  <li><a href="04-GitHub.md">GitHub - Son interface et son fonctionnement</a></li>
</ol>
<p>...</p>
</div>
</div>


------


Oui je l'ai dit : on part vraiment de zéro.

De base lorsque vous mettez à jour un fichier (mettons un document word ou un readme.md), vous enregistrez régulièrement. Du moins j'espère. En tout cas, dans pas mal de cas, votre traitement de texte sauvegarde tout ce que vous faites, de manière à pouvoir utiliser le fameux `Ctrl + Z` lorsque vous souhaitez revenir en arrière. Génial non ?

## Alors pourquoi on s'emm\*\*\*\* avec git ? <a id="pourquoigit"></a>

Et bien parce qu'une fois que vous fermez votre fichier et que vous le rouvrez, en général vous ne pouvez plus faire `Ctrl + Z`. Pour les malins qui utilisent un traitement de texte capable de le faire malgré tout : éteignez brusquement votre ordinateur et rallumez-le... Ensuite on en reparle.

Bref c'est dommage. 

Un autre cas où le `Ctrl + Z` n'est plus si pratique est le suivant.

### Le cas de retour vers le futur <a id="backtothefutur"></a>

Imaginons le cas suivant. Vous modifiez votre fichier au fur et à mesure, et vous le sauvegardez régulièrement. Chaque point ci-dessous représente une sauvegarde de votre fichier (soit par vous, soit par votre éditeur de texte). Les traits reliant les points signifient que vous modifiez le fichier : 

![01whygit_01](D:/ADN/Formation/Git/pictures/01whygit_01.png)

A un moment donné, vous ressentez le besoin de revenir en arrière. Via `Ctrl + Z`par exemple ?

Cela donnerai ceci : 

![01whygit_02](D:/ADN/Formation/Git/pictures/01whygit_02.png)

où ![01whygit_03](D:/ADN/Formation/Git/pictures/01whygit_03.png) représente un retour en arrière.



Très bien... mais comment revenez vous au point de repère ?

Et bien vous ne pouvez plus, votre éditeur de texte ne peut pas savoir si vous souhaitez revenir au point de repère, ou encore plus loin dans le temps.



### <a id="CasGit" style="text-decoration:none;color:#000">Le cas avec git</a>

Cette fois-ci, utilisons git. Au lieu de simples points, nous allons leurs donner des noms juste pour nous repérer entre nous.

- Ø : représente un état quelconque et sauvegardé de votre fichier.
- $V_{1}$ : représente un **commit** de votre fichier. Imaginez un commit comme une sauvegarde qui aurait un nom.

![01whygit_04](D:/ADN/Formation/Git/pictures/01whygit_04.png)

Cette fois-ci, grâce à git, il vous est tout à fait possible, lorsque vous vous retrouvez en $V_{5}$, de revenir en $V_{1}$, $V_{2}$, $V_{3}$ ou $V_{4}$.  Magique non ?



On peut même imaginer fusionner les différentes version de votre fichier : 

![1550766628198](D:/ADN/Formation/Git/pictures/01whygit_05.png)

Et là vous commencez à sentir l'utilité d'un vrai outil de versionnage de fichiers.

Je ne parle même pas de la collaboration à plusieurs ! Tellement plus simple.



## Fonctionnement de Git <a id="FonctionnementGit"></a>

### Les différents espaces de git <a id="GitSpaces"></a>

Les amis de chez NDP Software ont pondu un outil que je trouve personnellement génial pour comprendre le fonctionnement de git, et ainsi se repérer dans la multitude de commandes en ligne : 

<span style="text-align: centered;"><a href="http://ndpsoftware.com/git-cheatsheet.html" target="_blank">![01whygit_05](D:/ADN/Formation/Git/pictures/01whygit_06.png)</a> </span> (image cliquable)



On y retrouve les éléments suivants : 

- Espace de travail : c'est votre ordinateur, c'est là que vous travaillez, on ne changera pas votre habitude
- Index : un espace intermédiaire dans lequel vous direz à git de mettre les fichiers que vous voulez (ou voudrez) sauvegarder.
- Dépôt local : l'espace dans lequel vous sauvegardez vos modifications, vos fameux **commit**.
- Dépôt distant : l'endroit où vous lisez ces lignes. Oui GitHub. Mais cela peut être aussi un serveur, un disque dur externe, [GitLab](gitlab.com), n'importe. C'est une sauvegarde à l'identique de tous les commits que vous aurez décidé d'y mettre.
- Remise : ou stash pour les intimes. Considérez cela comme un espace temporaire. Nous y reviendrons bien plus tard.



### Espace de travail :<a id="EspaceTravail"></a>

Ici, pas de surprises, vous savez comment cela fonctionne : vous le faites tous les jours.



### Index<a id="Index"></a>

En revanche, ici, cela devient plus intéressant. Imaginons le fichier `VotreFichier.txt` suivant : 

```tex
Ceci est le texte à partir du quel on va partir. Prenez le comme acquis, comme si un collègue vous l'avait donné.

Il a plusieurs lignes.

mé Il ya plain d'error ...

Votre collègue est-il nul ?
```



Concrètement vous allez modifier ce fichier qui se trouve dans votre espace de travail. Imaginons donc que vous voulez le modifier en ceci : 

```tex
Ceci est le texte à partir du quel on va partir. Prenez le comme acquis, comme si un collègue vous l'avait donné. Il y a moins de lignes.
Mais cette fois il n'y a plus d'erreurs...
Mon collègue n'est pas si nul que ça. Il était simplement pressé et a écrit un peu vite.
```

 

Vous enregistrez ce document. Il y a donc eu plusieurs modifications. Une pour la mise en forme (de 7 à 3 lignes... comptez bien), une pour les fautes d'orthographes, une autre enfin pour le contenu lui même : votre collègue n'est pas si nul que ça après tout. Mais si vous faites tout d'un coup, votre ligne d'historique ressemblera à ça : 

![01whygit_07](D:/ADN/Formation/Git/pictures/01whygit_07.png)



Pas très intéressant. 



Nous voulons garder une trace de toutes ces différentes modifications. Et en soit ce n'est pas mentalement épuisant de les distinguer. Vous allez donc commencer par faire la première modification : diminuer le nombre de lignes : 

```tex
Ceci est le texte à partir du quel on va partir. Prenez le comme acquis, comme si un collègue vous l'avait donné. Il y a moins de lignes.
mé Il ya plain d'error ...
Votre collègue est-il nul ?
```



Et là : vous voulez "Sauvegarder" cette modification. Regardons d'abord ce que nous donne la commande : 

```shell
git status
```

```shell
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   VotreFichier.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Concrètement ici, git nous dit qu'il a repéré qu'un fichier avait changé, mais que rien ne sera ajouté au prochain commit (comprenez, à la prochaine sauvegarde). Il nous dit aussi que pour cela, il faut utiliser la commande `git add <file>...` Ainsi, on ajoute notre fichier `VotreFichier.txt` dans l'**Index**.



### Dépôt local<a id="DepotLocal"></a>

A partir de cet instant on peut exécuter la commande de commit.

```shell
git add VotreFichier.txt
```

```shell
git commit -m "Modifie la mise en forme"
```

qui donne le résultat dans votre terminal : 

```shell
[master 3626782] Modifie la mise en forme
 1 file changed, 1 insertion(+), 5 deletions(-)
```

Et on continue la même opération pour toutes les autres modifications. On aura donc trois commits différents, ce qui nous donne le schéma suivant : 

![01whygit_08](D:/ADN/Formation/Git/pictures/01whygit_08.png)

Chaque fois qu'un commit est fait, l'espace d'index est vidé, et placé dans l'espace de **dépôt local**. Ce dernier ne contient que les changements effectués entre les différents commits.

En réalité, dans votre éditeur de texte, et tant que vous ne fermez pas votre fichier, vous pourrez toujours faire `Ctrl + Z` pour récupérer des étapes intermédiaires. Mais dans le fond ce ne sont pas elles qui sont importantes, mais bel et bien les points (commits) que vous venez de créer.



### Dépôt distant<a id="DepotDistant"></a>

Vous êtes maintenant prêt à partager vos modifications avec vos collègues ! Car pour le moment, tout ce que vous avez fait reste uniquement sur votre machine. C'est à ça que peut servir un dépôt distant. GitHub en est un, mais cela peut être le serveur de données de votre entreprise, bitbucket, gitlab ou bien d'autres.

L'important c'est que ce dépôt distant, dans le cas qui nous préoccupe, soit accessible par vos collègues. On doit donc "envoyer" ces modifications, et on parle alors de `push`.

Cela se fait grâce à la commande : 

```shell
git push <nom du dépôt distant> <Nom de votre branche>
```

où : 

- nom du dépôt distant : est le nom du serveur sur lequel vous envoyez vos modifications. Si vous n'en avez qu'un, il s'appellera `origin` par défaut. Mais vous pouvez le changer, où en avoir plusieurs.
- Nom de votre branche : est le nom de la branche sur laquelle vous avez travaillé. Je reviendrais plus tard sur cette notion, mais [les graphiques précédents](#CasGit) vous donnent une indication de ce dont il s'agit.



Pour récupérer ces modifications, votre collègue pourra exécuter, par la suite, la commande : 

```shell
git pull <nom du dépôt distant> <Nom de votre branche>
```

pour mettre à jour son travail avec le votre.

