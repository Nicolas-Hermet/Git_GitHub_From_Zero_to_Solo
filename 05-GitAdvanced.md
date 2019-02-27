# Collaborer - Vos premiers pas sur un projet



Et voilà, nous y sommes presque. 
Une fois ce chapitre terminé, vous saurez à peu près tout ce qu'il faut savoir pour travailler en équipe sur un projet de développement avec Git et GitHub.



Pour commencer nous allons aborder quelques commandes avancées de Git. Ensuite nous apprendrons quelques bonnes pratiques du travail en équipe. Enfin nous verrons comment nous servir de GitHub pour faire tout ça.



## Commandes Git Avancées

### git Status

Celle-ci n'est pas vraiment une commande avancée mais possède à mon sens une très grande importance.

Nous l'avons vu dans le précédent chapitre. `git status` vous informe de la situation exacte dans laquelle vous vous trouvez. C'est donc un allié de taille pour comprendre ce qu'il se passe. Il faut en user sans modération. Je le fais personnellement avant et après chaque opération effectuée avec Git. Donc en moyenne 3 à 4 fois par commit. A raison d'une vingtaine de commits par jour en moyenne cela fait une bonne soixantaine de fois par jour. 



Adoptez le réflexe : `git status` !!



### git log

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



### git diff

Ahhh voilà une fonctionnalité attendue !

La commande `git diff` seule, permet d'afficher les différences entre l'espace de travail et l'index. Ainsi si vous avez des fichiers en cours de modifications, `git diff` vous donnera la différence de ces fichiers avec le dernier commit.



Mais encore mieux  ! 

vous pouvez donner des options à cette commande, comme le numéro de **SHA** ou le nom d'une branche. Git vous donnera la différence entre l'option que vous avez rentrée et votre espace de travail dans sa version actuelle.



### git checkout 

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



### git revert

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





### git blame

```shell
git blame <Nom du fichier>
```

Vous donnera, commit après commit en remontant le temps, le responsable de chacune des lignes ayant été modifiées dans <Nom du fichier>.

C'est souvent une commande que l'on trouve en extension dans de nombreux éditeurs de texte.



### git branch

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



### git merge

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



### :warning: Commande Git à NE JAMAIS FAIRE ! :warning:

A moins bien sûr de savoir exactement ce que vous faites.

- `git push -f origin <UneBranche>` : cela force le push... et ne fera aucun merge. Vous écraserez directement le travail de Jean-Claude sans sommation.
- D'une manière générale toute commande avec l'option `-f` doit être considérée comme dangereuse.





<span style="color:red;">*****</span> : On est d'accord, je parle de Jean-Claude, parce que c'est le premier nom qui me viens. Mais Jean-Claudine aurait pu très bien faire l'affaire aussi :wink:





## Le bon Workflow

### Qu'est ce qu'un workflow

Un workflow est un enchaînement d'actions faites par ensemble de personnes visant le même objectif.

En ce sens : 

- L'ensemble de personnes c'est vous et votre équipe
- L'objectif c'est de développer votre code et de réparer les bugs éventuels survenus en cours de route
- L'enchainement d'action : c'est le développement de nouvelles fonctionnalités, et le versionnage de votre code.



### La liste de tâches.

Pour développer votre code, il y a plusieurs manières. Les méthodes AGILE sont les plus répandues et c'est sur ce principe que je m'appuierai pour illustrer mon propos. Je ne détaillerai pas de quoi il s'agit exactement, cependant il y a pleins de ressources en ligne si cela vous intéresse. Mais rien ne vous y oblige.

Concrètement vous avez découpé votre code en plusieurs tâches à effectuer. Il faut écrire un Readme.md, il faut initier le répertoire de travail et le repository GitHub associé, il faut développer la fonctionnalité A, la B etc...



### Les Branches courantes : 

Quelque soit le domaine dans lequel vous développer, vous avez forcément une version du code que vous pouvez distribuer à vos utilisateurs. Celle-ci est stable, fiable, etc...  On appelle ça la production.

Mais il y a aussi une version de votre code sur laquelle vous êtes en train de développer de nouvelles choses. Celle-ci n'est pas entre les mains de vos utilisateurs, à moins que ceux-ci ne viennent directement sur votre GitHub. C'est la version de Développement.

Il peut y avoir d'autres versions, avec par exemple, des essais de technologies, de framework que sais-je.



Je vais choisir arbitrairement de vous montrer un workflow classique. Mais si ce sujet vous intéresse, je vous recommande l'excellent [git flow](https://fr.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) pour aller vous inspirer de différents workflows.



![02github_15](/pictures/gitflow.svg)



Ici la branche master représente la version en production, la branche de Develop, la version en cours de développement, et les branches Feature celle en cours d'élaborations par vos collègues



Ainsi, à chaque nouvelle tâche, vous partez de la branche Develop, vous créez votre nouvelle branche Feature, vous développez et ensuite, UNE FOIS SEULEMENT que vous avez vérifier que cela n'ajoutait pas de bug, vous faites un merge sur la branche Develop.

Une fois de temps à autre, avant chaque release : vous faites un merge sur la branche master, afin d'en faire profiter vos utilisateurs.



## Votre première collaboration

### Quelques notions rapide

#### Clone 

1. **Qu'est ce que c'est ?**

La copie intégrale du repo (dans la branche spécifiée) sur votre ordinateur (espace de travail) avec un lien direct vers votre repo. Git est donc déjà initialisé et vous aurez accès, depuis votre ordinateur, aux `git log`, `git blame` etc.

Seulement il faut avoir les droits d'accès à ce repo : être collaborateur dessus ou faire parti de l'organisation ou de l'équipe qui maintient le code. C'est le cas pour votre propres repositories.

2. **Comment on fait ?**

Rendez-vous sur un de vos repository, et cherchez le bouton *Clone or Download* : 



![03Collab_01](/pictures/03Collab_01.png)

Comme vous le voyez le menu qui s'affiche, vous avez 4 possibilités. La première est de l'ouvrir dans l'application GitHub Desktop (si vous l'avez téléchargée) : **Open in Desktop**, la deuxième est de **Download Zip** qui téléchargera la copie de la branche sur laquelle vous vous trouvez au format zip sur votre ordinateur. Cependant vous perdrez toute notions de git, pas d'init, pas de commit possible, pas de push ni de pull...

Enfin : soit vous clonez ce repository par la méthode SSH (Vous pouvez normalement le faire si vous avez suivi l'installation), soit en HTTPS.

La différence entre les deux est la suivante : 

- Par HTTPS : vous rentrerez votre login et mot de passe chaque fois que vous ferez un push
- Par SSH : vous rentrerez votre phrase de passe une seule fois par redémarrage de votre ordinateur.

Si vous n'avez pas de phrase de passe, l'option SSH est encore plus rapide.

3. **Et maintenant ?**

Et bien maintenant vous pouvez travailler sur votre ordinateur comme dans le chapitre précédent. 

**Note : ** vous pouvez cloner plusieurs fois le même repository. Vous serez alors dans le schéma suivant, et pourrez mieux simuler les actions de Jean-Claude, ou Jean-Claudine... c'est d'ailleurs ce qui se passe quand votre collègue fera un clone de votre repository de son côté.



#### Qu'est ce qu'un Fork ?

1. **Definition**

Un fork est une copie du repository sur votre compte GitHub. Vous devenez le propriétaire de la copie et pouvez faire ce que vous voulez avec : comme un clone par exemple.

Imaginez une fourchette. Le propriétaire du repository possède un des pics de la fourchette. Vous en possédez un autre.

GitHub gardera une trace du lien existant entre votre nouveau repository et celui que vous venez de fork. Cela sera pratique pour les pull request que vous verrez dans un instant.



2. **Comment faire ?**

Cherchez le bouton *Fork* en haut à droite du repository dont vous souhaitez un fork.

![03Collab_02](/pictures/03Collab_02.png)

Cliquez dessus, le repository sera directement ajouté à vos repositories personnels. GitHub vous demandera peut-être où vous souhaitez ajouter ce repository : chez vous ? ou dans votre organisation (si vous faites partie d'une).

Bien sûr vous ne pouvez pas fork votre propre repository. Cela n'a pas de sens.



3. **Modifier le repository d'origine**

Pour envoyer une modification sur le repo d'origine il faudra faire une pull request, soit via GitHub directement, ou via VS Code. C'est ce que vous allez faire avec ce repository que vous êtes en train de lire :wink:



#### Qu'est-ce qu'une Pull Request ?

1. **Définition**

Une pull request est une demande de merge de votre branche, ou de votre fork vers une autre branche de votre repo ou du repo d'origine.

2. **Pourquoi la Pull Request est nécessaire** 

Dans le workflow vous êtes responsable de votre branche.

Mais toute l'équipe est responsable de la branche de Develop et Master. Donc lorsque vous faites un merge de votre travail sur l'une de ces deux branches, il faut que quelqu'un d'autre la valide avant. Les relecteurs (reviewers) doivent regarder votre code, le tester, et valider votre travail. Lorsqu'un nombre suffisant de relecteur à validé votre travail, alors celui-ci peut être merge.

C'est d'ailleurs le cas dans pas mal de projets. Les branches master et Develop sont bloquées en push. Cela signifie que vous ne pourrez pas exécuter `git push origin master` par exemple. Seul le propriétaire du projet peut faire un push sur ces branches. En dehors de lui, tous les autres devront passés par une Pull request.

Cela évite des accidents malencontreux, du style Jean-Claude, qui tente un `git push -f origin master` pour bien péter votre travail.



### Exercice guidé :

Nous allons, dans cet exercice, modifier ce repository. Oui, celui que vous êtes en train de lire. Nous le ferons à l'aide de VS Code. Nous pourrions le faire avec l'interface web de GitHub, ou tout autre outils. J'ai choisi de vous guider pas à pas par l'intermédiaire de VS Code pour des raisons purement professionnelles. Si toute fois vous souhaitiez faire autrement, je vous renverrai alors vers l'excellent repository suivant : [First Contribution](https://github.com/firstcontributions/first-contributions). Vous le constaterez, je me suis largement inspiré de sa méthode, et je tiens à remercier le propriétaire de ce repository d'avoir mis ce projet en license MIT. C'est d'ailleurs le cas de ce présent repository.



1. **Faites un Fork de ce repository**
2. **Clonez le repository ainsi créé**

Cliquez simplement sur le bouton ![03Collab_01](/pictures/03Collab_01.png) et copiez l'adresse HTTPS ou SSH.

3. **Ouvrez VS Code**

Utilisez bien la commande `code` dans un terminal git bash pour ce faire.

![1551188647694](/pictures/03Collab_06.png)

Normalement, la page d'accueil doit apparaitre comme ci-dessous. 

D'ici : tapez `F1` ou `Ctrl + P` puis `>`. 

<img src="/pictures/03Collab_03.png" alt="Clone Popup (Command Popup)" />

Entrez `git clone` dans cette barre comme suit : 

<img src="/pictures/03Collab_04.png" alt="Entrez git clone" />

Et copiez l'URL que vous venez de copier dans GitHub. Cela doit fonctionner aussi bien en SSH qu'en HTTPS.

<img src="/pictures/03Collab_05.png" alt="Collez le chemin d'accès, ici en HTTPS" />

VS Code vous demandera où vous voulez cloner le repository sur votre ordinateur, et vous demandera ensuite s'il doit ouvrir le dossier.





4. **Créez une nouvelle branche.**

Vous allez appeler cette branche comme votre login GitHub. Si je devais le faire, cette branche s'appellerai `Nicolas-Hermet`. 

Pour cela, toujours dans VS Code, appuyez de nouveau sur `F1`, ou faites `Ctrl + P` puis `>`.

Tapez *branch* et cliquez sur *Create Branch*. Et entrez le nom de la branche (mettez votre login, ce sera plus clair pour moi lors de l'acceptation de votre pull request).

Ensuite sélectionnez à partir de quoi vous créez la branche. Je sais c'est légèrement différent par rapport aux invite de commandes. Dans le doute sélectionnez master.

Normalement à ce stade, VS Code vient de créer votre nouvelle branche en local et vous êtes déjà dessus. Vous vous souvenez de `git checkout` ? Et bien maintenant plus besoin.



5. **Faites vos modifications**

Ouvrez le fichier Contributors.md situé dans le dossier éponyme, et placez l'adresse de votre compte github n'importe où dans le fichier.

Soyez sympa : n'enlevez rien au fichier, ne faites simplement que rajouter votre compte.

Question syntaxe, c'est un fichier en MarkDown. Si ce n'est pas votre tasse de thé : copié-collez une ligne et remplacer les noms par le votre.

![03Collab_07](/pictures/03Collab_07.png)



6. **Add et commit**

Vous savez désormais qu'il faut maintenant ajouter ce fichier à l'index, puis le commit. Sous VS Code, rien de plus simple, cherchez l'icone de versionnage sur la gauche de VS Code et cliquez dessus :

![03Collab_08](/pictures/03Collab_08.png)

Normalement vous devriez avoir la liste des fichiers qui ont été modifiés : 



![03Collab_09](/pictures/03Collab_09.png)



En passant votre souris sur le fichier Contributors.md vous constaterez que plusieurs symboles apparaissent : 

![03Collab_10](/pictures/03Collab_10.png)

De gauche à droite : le premier sert à ouvrir le fichier si ce n'est pas déjà le cas. Le deuxième sert à annuler l'intégralité des changements apportés à ce fichier depuis le dernier commit, et enfin le `+` sert à ajouter le fichier à l'index. C'est le strict équivalent à `git add Contributors.md`.



![03Collab_11](/pictures/03Collab_11.png)

Une fois ce fichier ajouté à l'index, vous pouvez entrer votre message de commit dans le champs situé juste au dessus et appuyer sur `Ctrl + Entrée` lorsque vous aurez fini.

Votre premier commit avec VS Code ! :champagne: :tada:



Maintenant : publiez votre branche. Ce sera fait bien entendu sur votre propre repository. Mais en fonction de votre méthode de clonage, VS Code vous demandera vos identifiants et mot de passe GitHub.

![03Collab_12](/pictures/03Collab_12.png)



7. **Votre première pull request**

Si vous avez bien suivi la partie installation, vous pouvez la faire directement avec VS Code. En bas à gauche de votre fenêtre, si vous êtes dans la partie versionnage vous trouverez un panel pour la gestion des pull requests : 

![03Collab_13](/pictures/03Collab_13.png)

Cliquez sur le bouton `+` et sélectionner la branche sur laquelle vous voulez faire votre merge.

**Rappel** : une pull request c'est avant tout un merge.

Dans cette capture d'écran vous ne voyez que la branche master de ce repository. La raison est simple : je ne peux pas fork mon propre repository. Pour vous normalement vous devriez avoir une autre ligne vous présentant la branche master de **mon** repository. C'est celle là qu'il faut choisir.



Une page doit s'ouvrir se présentant à peu près comme suit : 

![03Collab_14](/pictures/03Collab_14.png)

Remplissez la partie description et éventuellement commentaire, afin de bien décrire au propriétaire du repository ce que vous avez fait et en quoi vous apporter une amélioration.

Dans le cas présent dites moi juste que vous souhaitez faire votre première contribution.



En essence, la pull request à ce stade est déjà créée. C'est pour cette raison qu'il n'y a pas de bouton "Envoyer" ou autre de la sorte. Mais dans l'encadré en bas à gauche, réservé aux pull request, vous verrez que la votre est bien apparue, et est en attente.

En attente de ma validation.



De mon côté je recevrais un mail me disant que vous souhaiter faire un merge de votre travail avec le mien. Je regarderais quels sont les différences de code, et validerais, ou vous demanderais de changer certaines choses.



Si j'accepte : vous venez de faire votre toute première contribution !!!!

Félicitations !! :champagne::tada:



### Exercice non guidé : 

1. Contribuez à ce repository.
2. Faites une contribution, dans le dossier SandBox. Attention : aucun code ne sera autorisé. Seulement du MarkDown, HTML5, Text ou éventuellement du LaTeX. Mais n'oubliez pas que certaines personnes peuvent faire pareil que vous au même moment. Faites donc attention à Jean-Claude ou Jean-Claudine !



## Quelques astuces supplémentaires concernant VS Code et Git / GitHub.

### `git diff` automatique : 

Dans le bandeau vertical à gauche de VS Code, cliquez dans l'outil de versionnage, et, si vous avez modifié un de vos fichiers, VS Code vous l'indiquera. Cliquez alors sur le fichier pour voir toutes les modifications faites au fichier : 

![03Collab_15](/pictures/03Collab_15.png)



Idem en haut à gauche sur ce bouton : 

![03Collab_16](/pictures/03Collab_16.png)

### `git log` stylé : 

il suffit de cliquer sur ce bouton en haut à droite, et de patienter un peu. Une nouvelle vie s'offre à vous.

![03Collab_17](/pictures/03Collab_17.png)

![03Collab_18](/pictures/03Collab_18.png)

Je vous laisse découvrir toutes les fonctionnalités.