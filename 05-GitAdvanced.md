# Git Avancé


<div id="toc_container" style="background-color: #f7faff;">
<div id="toc-wrapper" style="margin-left: auto;margin-right: auto; width: 40%;">
<p class="toc_title"><strong>Contents</strong></p>
<p><a href="Readme.md">Retour au sommaire</a></p>
<ol class="toc_list" start="1">
  <li><a href="04-GitHub.md">GitHub - Son interface et son fonctionnement</a></li>
  <li><a href="05-GitHub.md">Git Avancé</a></li>
  <ol>
    <li><a href="05-GitHub.md/#intro">Introduction</a></li>
    <li><a href="05-GitHub.md/#commandes">Commandes Git Avancées</a></li>
    <ol>
        <li><a href="05-GitHub.md/#status">git status</a></li>
        <li><a href="05-GitHub.md/#log">git log</a></li>
        <li><a href="05-GitHub.md/#diff">git diff</a></li>
        <li><a href="05-GitHub.md/#checkout">git checkout</a></li>
        <li><a href="05-GitHub.md/#revert">git revert</a></li>
        <li><a href="05-GitHub.md/#blame">git blame</a></li>
        <li><a href="05-GitHub.md/#branch">git branch</a></li>
        <li><a href="05-GitHub.md/#merge">git merge</a></li>
        <li><a href="05-GitHub.md/#warning">Commande Git à NE JAMAIS FAIRE !</a></li>
    </ol>
  </ol>
  <li><a href="06-Workflow.md">Workflow - travailler en équipe</a></li>
</ol>
<p>...</p>
</div>
</div>



## Introduction <a id="intro"></a>

Collaborer - Vos premiers pas sur un projet


Et voilà, nous y sommes presque. 
Une fois ce chapitre terminé, vous saurez à peu près tout ce qu'il faut savoir pour travailler en équipe sur un projet de développement avec Git et GitHub.



Pour commencer nous allons aborder quelques commandes avancées de Git. Ensuite nous apprendrons quelques bonnes pratiques du travail en équipe. Enfin nous verrons comment nous servir de GitHub pour faire tout ça.



## Commandes Git Avancées <a id="commandes"></a>

### git status <a id="status"></a>

Celle-ci n'est pas vraiment une commande avancée mais possède à mon sens une très grande importance.

Nous l'avons vu dans le précédent chapitre. `git status` vous informe de la situation exacte dans laquelle vous vous trouvez. C'est donc un allié de taille pour comprendre ce qu'il se passe. Il faut en user sans modération. Je le fais personnellement avant et après chaque opération effectuée avec Git. Donc en moyenne 3 à 4 fois par commit. A raison d'une vingtaine de commits par jour en moyenne cela fait une bonne soixantaine de fois par jour. 



Adoptez le réflexe : `git status` !!



### git log <a id="log"></a>

Exécutez `git log` dans votre terminal. Vous y verrez l'historique de tous les commits de la branche actuelle.

Chaque commit possède un **SHA**. C'est un identifiant unique permettant de s'y référer pour revenir en arrière.

Git log dans sa forme simple se présente comme ceci : 

```shell
commit 2e14a826dbd76f31ff6e5664e29b77c9599a7cc1 (HEAD -> master, origin/master)
Author: Your Name <your@mail.com>
Date:   Mon Feb 25 12:18:32 2019 +0100

    Votre message de commit

```

Ici, le SHA est donc `2e14a826dbd76f31ff6e5664e29b77c9599a7cc1`. 



### git diff <a id="diff"></a>

Ahhh voilà une fonctionnalité attendue !

La commande `git diff` seule, permet d'afficher les différences entre l'espace de travail et l'index. Ainsi si vous avez des fichiers en cours de modifications, `git diff` vous donnera la différence de ces fichiers avec le dernier commit.



Mais encore mieux  ! 

vous pouvez donner des options à cette commande, comme le numéro de **SHA** ou le nom d'une branche. Git vous donnera la différence entre l'option que vous avez rentrée et votre espace de travail dans sa version actuelle.



### git checkout <a id="checkout"></a>

Je viens de mentionner votre espace de travail *dans sa version actuelle*. Cela veut dire qu'à tout moment vous pouvez changer son état, à condition que tous les fichiers en cours de modifications soient placés dans l'index (via `git add`).

`git checkout` permet alors de modifier l'état de votre espace de travail. Soit en changeant de branche, soit en vous plaçant sur un commit précédent etc...

Pour vous en convaincre : exécutez `git log` afin de trouver un **SHA** relativement ancien (pour lequel il y aurait beaucoup de différence avec les fichiers actuellement dans votre espace de travail).

puis : 

```shell
git checkout <Votre SHA>
```

Vous venez alors de voyager dans le temps !! Félicitation. Beaucoup moins spectaculaire que dans les films, mais c'est pourtant ce qu'il vient de se passer. Comme dans les films : ne touchez à rien, et exécutez : 

```shell
git checkout <La branche sur laquelle vous êtes>
```

Ici : <La branche sur laquelle vous êtes> est probablement "master". Ce qui donne `git checkout master`

Et vous reviendrez à votre "époque". Bien sûr, il est possible de modifier le passé. Mais réservez le aux pros dans un premier temps car cela devient vraiment compliqué à notre niveau.



Une autre utilité de `checkout` est aussi d'annuler toutes les modifications que vous avez faites sur un fichier qui n'est pas encore ajouté à l'index. Par exemple, vous venez de faire un commit et `git status` vous dit que tout est clean. Eventuellement vous êtes en avance par rapport au dépôt distant.

Modifiez un fichier au hasard, mais ne faites pas `git add`. A la place faites : 

```shell
git checkout -- VotreFichierModifié.***
```

Normalement cela devrait effacer les modifications que vous aviez faites.



### git revert <a id="revert"></a>

Vous l'aurez compris, même si c'est possible, il est très difficile (ou risqué) d'altérer le passé. Mais combien de fois, vous êtes vous dit : "Ahh... j'aurais aimé que cela ne soit jamais arrivé" ? Et bien ne le dites plus : passez à l'acte.

```shell
git revert <SHA>
```

Va rajouter un commit supplémentaire, mais pour défaire le commit possédant le numéro de SHA passé en argument... 

Essayez avec cet exercice : 

1. Repérez bien dans quel état se trouve un de vos fichiers
2. Editez le d'une manière repérable : puis `git add` et `git commit`... 
3. Effectuez une autre opération, comme par exemple ajouter un fichier. Ou même mieux : ajoutez une ligne au fichier précédent puis idem : `git add` et `git commit`
4. Faites un `git log` et repérez le SHA du commit de l'étape 3.
5. Exécutez `git revert <Ce SHA là>`
6. Regardez dans quel état se trouve votre fichier.





### git blame <a id="blame"></a>

```shell
git blame <Nom du fichier>
```

Vous donnera, commit après commit en remontant le temps, le responsable de chacune des lignes ayant été modifiées dans <Nom du fichier>.

C'est souvent une commande que l'on trouve en extension dans de nombreux éditeurs de texte.



### git branch <a id="branch"></a>

On en arrive à la partie la plus importante : les branches. Une branche est une ligne différente de l'Histoire de votre code.

![02github_13](/pictures/02github_13.png)

Et comme dans le film, tout peut être différent dans cette branche.



Pour créer une banche : 

```shell
git branch <Nom De Votre Nouvelle Branche>
```

Cela aura pour effet de créer une branche dans laquelle vos fichiers seront identiques à ceux de la branche où vous étiez au moment de la création. Les fichiers ont été dupliqués.

L'endroit dans le temps où l'on crée une branche est donc important.

On peut ensuite se placer dans la nouvelle branche en exécutant : 

```shell
git checkout <Nom De Votre Nouvelle Branche>
```

A partir de là, tous les `git add` et `git commit` affecteront cette nouvelle branche.

A tout moment vous pouvez revenir dans la branche master par : `git checkout master`



Bien sûr il existe une commande permettant de tout faire d'un coup : la création et le déplacement dans la nouvelle branche : 

```shell
git checkout -b <Nom de Votre Nouvelle Branche>
```

Notez également que `git status` vous indiquera dans quelle branche vous vous trouvez !



### git merge <a id="merge"></a>

On comprend bien que créer une ligne temporelle différente n'est pas forcément très intéressant en soi. A moins d'avoir plusieurs versions différentes de son code. Pourquoi pas.

Mais c'est surtout l'intérêt de pouvoir fusionner plusieurs branches entre elles qui est intéressant.

Repartons de notre repository du chapitre précédent.

Vous devriez avoir au moins un fichier Readme.md présent.

exécutez la commande 

```shell
git checkout -b NouvelleBranche
```

Publiez cette branche immédiatement sur GitHub afin que tous vos collègue sachent que celle-ci est disponible : 

```shell
git push origin NouvelleBranche
```

ensuite modifiez le fichier Readme.md. Chez moi il ressemble pour l'instant à cela : 

```markdown
WOUUHOU !!!!
J'ai rajouté du texte à mon fichier readme !!
```

Je vais le modifier de cette manière : 

```markdown
WOUUHOU !!!!
J'ai rajouté du texte à mon fichier readme !!
Voici la ligne venant de ma NouvelleBranche
```

Faites un `git add` et `git commit` de ce fichier, puis publiez là dans votre nouvelle branche : `git push origin NouvelleBranche`.

Revenez maintenant dans votre branche master : 

```shell
git checkout master
```

et modifiez le fichier Readme.md comme ceci : 

```markdown
WOUUHOU !!!!
J'ai rajouté du texte à mon fichier readme !!
Ceci est une ligne dans la branche master
```

Faites un `git add` et `git commit` de ce fichier, puis publiez là dans votre nouvelle branche : `git push origin master`.

Puis, revenez sur votre NouvelleBranch : `git checkout NouvelleBranch`



Le même fichier est modifié différemment dans chacune des branches. Intuitivement c'est problématique pour les fusionner. Si des lignes différentes avaient été modifiées, git s'en serait sorti tout seul comme un chef et l'exercice n'aurait pas eu d'intérêt (testez-le par vous même).

Ici on va considérer que nous collaborons à plusieurs. On vient donc de simuler ici le cas suivant : 

"Jean-Claude<span style="color:red;">*****</span>: Tiens je vais modifier Readme.md dans la branche master !

\- Vous : Tiens je vais créer une branche spéciale pour modifier le fichier Readme.md"

Aucun de vous deux n'a bien sûr pensé à prévenir l'autre de ses intentions.



Voici donc le procéder à suivre quasi systématiquement : 

- Dans NouvelleBranch : vous allez vérifier que vous êtes à jour par rapport à GitHub en exécutant `git pull origin NouvelleBranch`. Si ce n'est pas le cas, git fera un merge, c'est-à-dire une fusion entre votre travail et celui présent sur GitHub. Mais je considère que vous êtes en train de travailler seul.
- Vous allez vous placer dans la branche master, et idem, récupérer le travail éventuel de vos collègues (dont celui de Jean-Claude) : `git checkout master` puis `git pull origin master`.
- Maintenant que vous êtes à jour sur les deux branches, revenez dans votre NouvelleBranche et exécutez : 

```shell
git merge master
```

- git devrait alors vous péter à la gueule en vous disant : 

```shell
Auto-merging Readme.md
CONFLICT (content): Merge conflict in Readme.md
Automatic merge failed; fix conflicts and then commit the result.
```

- Dans votre éditeur de texte ouvrez le fichier Readme.md. Vous devriez avoir quelque chose comme ceci : 

![02github_14](/pictures/02github_14.png)

Ici, git vous a laissé un petit message dans votre fichier.

```markdown
<<<<<<< HEAD
Voici la ligne venant de ma NouvelleBranche
```

une ligne de séparation : `=======` ainsi que : 

```markdown
Ceci est une ligne dans la branche master
>>>>>>> master
```

En gros, git vous explique qu'il a trouvée deux version différentes : celle de HEAD, qui est l'endroit où vous vous trouviez quand vous avez souhaité faire un merge, et celle de master, la branche que vous vouliez merge (ou fusionner) dans la votre.

Vous avez alors 4 cas de figure : supprimer votre ligne, supprimer celle de Jean-Claude, supprimer les deux, ou laisser les deux (et éventuellement les réagencer).

Je vais choisir de garder les deux, mais vous pouvez refaire l'exercice avec tous les cas de figures. 

:warning: n'oubliez pas de bien enlever également les '<<<<<HEAD' ; '===='' et '>>>> master'. Git ne vous embêtera pas avec, mais votre compilateur peut être un peu plus.

Puis sauvegardez votre fichier.

J'ai donc pour ma part un fichier Readme.md qui ressemble à cela : 

```markdown
WOUUHOU !!!!
J'ai rajouté du texte à mon fichier readme !!
Voici la ligne venant de ma NouvelleBranche
Ceci est une ligne dans la branche master

```

`git status` vous dira que vous êtes en plein merge. Il faut alors résoudre les conflits à la main, et commit le(s) fichier(s) concerné(s). 

Nous avons résolu le conflit. On peut donc `git add Readme.md` puis `git commit -m "Un message pour dire ce que vous avez choisi"`.

Faites maintenant `git push origin NouvelleBranche`.



Ce n'est pas fini !!

Revenez maintenant dans la branche master : `git checkout master`

Dans le doute, refaites : `git pull origin master` des fois que Jean-Claude vous ai encore pondu un truc pendant ce temps là. Si c'est le cas, et bien repartez dans votre NouvelleBranche et refaites un merge. Dans le cas où Jean-Claude est resté sage faite 

```shell
git merge NouvelleBranche
```

Cette fois-ci, vous importez les modifications de votre NouvelleBranche dans la branche master. Tout devrait bien se passé, et git devrait vous donner un compte rendu des modifications.

Chez moi : 

```shell
Updating 1e0eaa4..ac87931
Fast-forward
 Readme.md | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)
```



Et publiez immédiatement votre fichier sur GitHub avant que Jean-Claude ne revienne de la pause café  : `git push origin master`.



Bravo ! Vous venez de faire votre premier merge.

Rassurez-vous : ce sera plus simple avec VS Code et les pull request.



Refaites cet exercice en suivant seulement ces indications pour vérifier que vous avez bien compris ce qu'il se passait : 

1. Créez une nouvelle branche (que j'appellerai **B**) depuis la branche master.
2. Dans **B** modifiez le fichier de votre choix (fichier **F**).
3. Publiez cette modification dans GitHub (attention à ce qu'aurait pu faire Jean-Claude ? `git pull` pour être sûr d'être à jour)
4. Revenez dans la branche master et jouez le rôle de Jean-Claude : modifiez le fichier **F** et publiez la modification sur GitHub.
5. Repartez à nouveaux dans **B** et faites un merge
6. Résolvez les conflits et publiez la branche.
7. Revenez dans master et faites attentions à ce bon vieux Jean-Claude (git pull).
8. Merge **B** dans master
9. Push vers GitHub...



Cela à l'air facile... Mais n'oubliez pas qu'il y a toujours un Jean-Claude dans votre équipe. Si... Toujours... Et donc pour éviter de se faire avoir : 

Ayez le reflexe : `git status`



### :warning: Commande Git à NE JAMAIS FAIRE ! :warning:<a id="Warning"></a>

A moins bien sûr de savoir exactement ce que vous faites.

- `git push -f origin <UneBranche>` : cela force le push... et ne fera aucun merge. Vous écraserez directement le travail de Jean-Claude sans sommation.
- D'une manière générale toute commande avec l'option `-f` doit être considérée comme dangereuse.





<span style="color:red;">*****</span> : On est d'accord, je parle de Jean-Claude, parce que c'est le premier nom qui me viens. Mais Jean-Claudine aurait pu très bien faire l'affaire aussi :wink:
