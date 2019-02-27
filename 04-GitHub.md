# GitHub - Son interface et son fonctionnement


<div id="toc_container" style="background-color: #f7faff;">
<div id="toc-wrapper" style="margin-left: auto;margin-right: auto; width: 40%;">
<p class="toc_title"><strong>Sommaire du chapitre</strong></p>
<p><a href="Readme.md">Retour au sommaire</a></p>
<ol class="toc_list" start="1">
  <li><a href="03-Git.md">Git</a></li>
  <li><a href="04-GitHub.md">GitHub - Son interface et son fonctionnement</a></li>
  <ol>
    <li><a href="04-GitHub.md/#Apercu">Aperçu rapide des différentes pages</a></li>
      <ol>
        <li><a href="04-GitHub.md/#Accueil">Page d'accueil</a></li>
        <li><a href="04-GitHub.md/#Overview">Votre profil - Overview</a></li>
      </ol>
    <li><a href="04-GitHub.md/#VosRepos">Vos repositories</a></li>  
      <ol>
        <li><a href="04-GitHub.md/#PaPPremierRepo">Créer votre premier repository - pas à pas</a></li>
        <ol>
          <li><a href="04-GitHub.md/#Créer votre premier repository - pas à pas">Créez votre premier répertoire de travail avec git</a></li>
          <li><a href="04-GitHub.md/#RelierGitHub">Relier votre espace de travail à GitHub</a></li>
          <li><a href="04-GitHub.md/#ModifFichier">Modifiez votre fichier</a></li>
          <li><a href="04-GitHub.md/#PointImportant">Points importants</a></li>
        </ol>  
        <li><a href="04-GitHub.md/#Exercice">Exercice</a></li>  
      </ol>  
  </ol>
  <li><a href="05-GitHub.md">Git Avancé</a></li>
</ol>
<p>...</p>
</div>
</div>


------


## Aperçu rapide des différentes pages <a id="Apercu"></a>

Bienvenue dans GitHub. D'abord qu'est ce que GitHub ? C'est ce que l'on appelle un **dépôt distant** pour Git. Mais cela peut aussi être un moyen de sauvegarde de vos dossiers. L'avantage c'est que tous ces dossiers sont versionnés avec Git. 
Ainsi vous pourriez très bien vous passez d'avoir le moindre dossier sur votre ordinateur. Mais ce ne serait pas très pratique.



Voyons tout de suite comment cela fonctionne : 

### Page d'accueil <a id="Accueil"></a>

![02github_01](/pictures/02github_01.png)

Voilà à quoi elle ressemble.

1. Ce cadre vous permettra de 
   - Revenir à la page d'accueil
   - Effectuer une recherche dans votre profil ou dans l'ensemble de la plateforme GitHub
   - Afficher l'ensemble des pull request (on y reviendra) vous concernant.
   - Afficher l'ensemble des issues (on y reviendra) vous concernant.
   - Marketplace et Explore servent à parcourir les applis que vous pouvez connecter à votre compte GitHub ainsi que les projets open source en vogue du moment.
   - Une cloche vous indiquant les notifications pertinentes vous concernant.
   - Le "+" pour créer un nouveau repository, une équipe etc...
   - Votre photo de profil dans laquelle vous pourrez accéder à vos paramètres, et bien d'autres choses encore.
2. Ce cadre permet de voir les repositories sur lesquels vous avez récemment travaillé, ainsi que ceux de votre organisation.
3. Le cadre 3 représente un fil d'actu de ce qu'il se passe dans votre réseau.
4. Enfin ici, en fonction de vos activités, GitHub vous propose des projets que vous pourriez vouloir consulter.

### Votre profil - Overview <a id="Overview"></a>

Cliquez sur votre photo de profil, puis sur "Your Profile" :



 ![02github_02](/pictures/02github_02.png)

Vous arrivez sur votre profil, à la rubrique "**Overview**"

Cette rubrique se compose comme suit : 

![02github_03](/pictures/02github_03.png)

Vous avez sur votre gauche de quoi éditer votre profil, et au milieu les différents onglets que vous retrouvez également en cliquant sur votre photo de profil (tout en haut à droite).

En dessous, les différents répertoires que vous souhaitez mettre en avant au près de la communauté, suivi de vos statistiques ainsi que des différentes contributions ou travaux que vous avez fait par le passé.

Mais je vous laisse le soin de regarder tout ça.

Passons à ce qui nous intéresse le plus : vos répertoires.

Cliquez sur l'onglet "**Repositories**", par le biais que vous souhaitez.

## Vos repositories <a id="VosRepos"></a>

### Créer votre premier repository - pas à pas <a id="PaPPremierRepo"></a>

Normalement, en arrivant sur cette page, vous n'avez aucun répertoire versionné sur votre machine, ni aucun repository sur GitHub. Si c'est pourtant le cas, vous pouvez vous affranchir de cette partie.

Sinon, que ce soit sur la page d'accueil, sur le petit "**+**" en haut à droite, ou ailleurs, cherchez le petit : 

![02github_04](/pictures/02github_04.png)

Cela vous permettra de créer un nouveau repository sur votre compte GitHub. Nous le remplirons tout de suite après.

Vous devez donc arriver sur une page ressemblant à cela : 



![02github_05](/pictures/02github_05.png)

Il va vous falloir ici remplir plusieurs choses.

1. **Propriétaire**

   Déjà : commencez par dire qui est le propriétaire ("**Owner**") du repository. Vous même, comme c'est mon cas ici, ou l'organisation à laquelle vous appartenez.

2. **Titre**

   Intitulé Repository Name, il ne doit comporter aucun espace, ni aucun caractère spécial et être unique parmi tous vos repositories.

3. **Description**

   Optionnel, mais pourtant pratique. Décrivez ici succinctement en quoi consiste votre projet.

4. **Public / Private**

   Comme son nom l'indique, choisissez si quelqu'un peut voir l'existence de votre repository ou si vous souhaitez le garder caché. Si vous souhaitez le rendre privé, vous pourrez toujours ajouter des collaborateurs par la suite pour vous aider à le faire évoluer. Mais vous serez limité en nombre de collaborateurs dans la version gratuite de GitHub.

5. **Readme ou pas ?**

   Vous devez choisir ici, si vous souhaitez initialiser votre repertoire avec un fichier qui sera nommé Readme.md.

   Par défaut, GitHub (et la majeure partie de ses concurrents) arrive à repérer les fichiers Readme.md qui seraient situés à la racine de votre répertoire. C'est aussi une pratique courante dans pas mal de framework, de créer automatiquement ce fichier Readme.md à la racine. Ce fichier, écrit en markdown est alors directement interprété par GitHub, qui l'affichera en première page de votre repository. Ainsi lorsque d'autres personnes iront voir votre projet, ils tomberont par défaut directement sur cette page.

   

   Nous allons donc laisser cette option de côté pour le moment. Cela aura pour effet de créer un repository parfaitement vide.

6. **.gitignore et License ?**

   C'est là que cela devient intéressant. Laisser la partie License à "none" pour le moment. Vous êtes simplement en train de dire qu'aucune license ne protège le contenu de votre repository. En gros tout le monde aura donc le droit de le copier, l'utiliser, voir carrément commercialiser ce qui se trouvera dans votre répertoire. Pas très grave pour le moment : on s'entraîne à utiliser GitHub. Je doute que quelqu'un fasse des millions de dollars de bénéfices avec ça.

   Je traite la partie .gitignore dans les paragraphes suivant. Laissez l'option sur "none" également pour le moment. Mais pour faire simple, ce fichier, systématiquement appelé, `.gitignore` est un fichier texte, listant l'intégralité des fichiers que vous ne voulez pas versionner, ni voir apparaître sur GitHub. Typiquement un fichier de configuration, vos clefs d'API secrètes, éventuellement des fichiers contenant vos mot de passes en clair (pas bien)... 



Si vous n'avez pas initialisé de Readme, ni de .gitignore ou de fichier de LIcense, vous devriez tomber sur cette page : 

![02github_06](/pictures/02github_06.png)

Ici on vous propose plusieurs choses : 

1. **Quick setup**

   On laissera tomber pour le moment. C'est pour les grands.

2. **Create a new repository on the command line**

   C'est en substance ce que nous allons faire. Mais je vais vous guider pas à pas en vous expliquant à quoi tout ça correspond.

3. **Push an existing repository**

   Si vous regardez bien, la proposition précédente inclut celle là.

4. **Import code from another repository**

   Uniquement si vous souhaitez faire un import d'un autre repository existant. Je n'ai pas encore eu de cas de figure où je trouvais cela utile... Je complèterais ce tutoriel si un jour je trouve le temps.



Pour le moment nous n'allons donc rien faire... Vous pourrez toujours revenir à cette page plus tard si vous le souhaitez. Je vous conseille de la laisser ouverte par simplicité, mais libre à vous.



##### Créez votre premier répertoire de travail avec git <a id="PremierRepo"></a>

Bien. Assez perdu de temps sur internet. 

Sur votre ordinateur : ouvrez créez un dossier, n'importe lequel. Nommez le avec le même nom que le repository GitHub que vous venez de créer. C'est conseillé pour pouvoir s'y retrouver. Bien sûr, vous n'y êtes pas obligé.

Puis ouvrez git bash : ![02github_07](/pictures/02github_07.png)



Placez vous à l'aide de la commande `cd` dans le répertoire que vous venez de créer. 

Puis, exécutez la commande suivante : 

```shell
git init
```

Cela initialisera git. En substance, vous êtes en train de dire à git : ok à partir de maintenant observe tout ce qu'il se passe dans ce répertoire.

Votre terminal vous répond avec le message ``Initialized empty Git repository in D:/VotreCheminDAcces/.git/`

Commençons donc par créer ce fameux Readme.md, pourquoi pas ? Pour les fans de l'invite de commande vous pouvez exécuter : 

```shell
touch Readme.md
```

Pour les autres, créez-le de la manière souhaitée.



Laissons ce fichier vide pour le moment, et exécutons la commande : 

```shell
git status
```

Cela devrait vous donner le résultat suivant : 

```shell
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        Readme.md

nothing added to commit but untracked files present (use "git add" to track)
```

Parfait ! Votre fichier est créé et git vous répond : "ok j'ai vu que vous aviez créé un nouveau fichier, mais pour l'instant je ne m'en occupe pas."



On va lui demander de s'en occuper justement. Exécutez la commande  

```shell
git add Readme.md
```

Normalement : rien ne se passe dans votre terminal. C'est normal.

Mais refaites la commande `git status` et vous verrez que le message de git change : 

```shell
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   Readme.md
```

Cette fois, git vous dit : "Ok je surveille ce fichier, je suis prêt à le sauvegarder (commit) quand ce sera le moment."

Cela me paraît être une bonne idée. Car même si le fichier est bel et bien créé sur votre ordinateur, il n'est pas encore sauvegardé en terme de git... Nous allons le sauvegarder (commit) dans son état actuel : vide.

Exécutez alors la commande : 

```shell
git commit -m "Création du fichier Readme"
```

Ici, vous demandez à git, de **"commit"** (sauvegarder) le fichier, avec **"-m"** le message : **"Création du fichier Readme"**. Git vous répondra avec des statistiques d'ajout et suppression, le numéro d'identifiant de ce commit et d'autres choses, mais surtout, il aura sauvegardé l'état de votre fichier avec ce message. Plus tard lorsque vous voudrez retourner à l'état de votre répertoire lors de la création de ce fichier, ce message sera là pour aider.



Super !!
Bon mais c'est bien gentil tout ça... mais alors ? Quand est-ce qu'on met ça sur GitHub ?

Maintenant : 

##### Relier votre espace de travail à GitHub <a id="RelierGitHub"></a>

Vous vous souvenez des différentes options que vous proposait GitHub lorsque vous avez créé votre repository ?

Il y avait : la création du fichier Readme.md (avec du texte dedans contrairement à nous), l'initialisation du repository git à l'aide de `git init` puis l'ajout du fichier Readme.md avec `git add Readme.md` et enfin le commit avec `git commit -m "Votre message"`... 

On en est là.

Il ne reste plus qu'à ajouter un dépôt distant grâce à la commande : 

```shell
git remote add origin git@github.com:Nicolas-Hermet/rep_test_Git_GitHub.git
```

puis à envoyer votre travail dessus : 

```shell
git push -u origin master
```


Maintenant, retournez sur la page GitHub de votre repository, et rafraichissez là : 

![02github_08](/pictures/02github_08.png)



##### Modifiez votre fichier <a id="ModifFichier"></a>

Tout à l'air d'être bon ! Maintenant on va pouvoir modifier le fichier. Sur votre ordinateur, ouvrez le fichier Readme.md avec l'éditeur de texte de votre choix.

Ecrivez n'importe quoi dedans et sauvegardez le.

Maintenant, dans votre terminal git bash, exécutez la commande : 

```shell
git status
```

Vous devriez voir ceci apparaître : 

```shell
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   Readme.md

no changes added to commit (use "git add" and/or "git commit -a")
```

Cela signifie encore une fois, que git a bien repéré que ce fichier avait changé depuis le dernier commit... mais il ne sait pas s'il devra tenir compte de ces changements pour le prochain commit.

Dites lui que oui !

```shell
git add Readme.md
```

Puis dites lui que vous voulez commit et donnez le message que vous souhaitez. Pour moi ce sera donc : 

```shell
git commit -m "Ajout des premières lignes"
```

git me signale : 

`[master 8d68e77] Ajout des premières lignes                                     
1 file changed, 2 insertions(+)`

Mais ceci pourrait être différent en fonction de l'inspiration que vous avez eu en écrivant dans votre fichier.



Maintenant il faut mettre ça à jour sur GitHub !!

```shell
git push origin master
```



Lorsque vous rafraichirez la page de votre repository GitHub, celle-ci aura encore changée : 

![02github_09](/pictures/02github_09.png)

Vous pouvez désormais ajouter, modifier et même supprimer tous les fichiers que vous voulez dans votre répertoire sur votre ordinateur. Mais chaque changement, ou étape que vous voudrez "enregistrer" (et donc commit) devra être indiqué à git.

Quelques tuyaux : 

1. Ajout d'un fichier ou Modification d'un Fichier Existant : 

   ```shell
   git add LeFichierModifieOuCree.***
   git commit -m "Dites ici ce que vous avez fait et pourquoi"
   git push origin master
   ```

2. Suppression d'un fichier : 

   ```shell
   git rm LeFichierASupprimer.***
   git commit -m "Votre message de suppression"
   git push origin master
   ```



##### Points importants : <a id="PointImportant"></a>

1. La commande push

`git push origin master`. C'est génial, mais attention : la commande est `git push` ; `origin` est le nom donné au dépôt distant, c'est à dire le nom donné à GitHub. Mais vous pourriez très bien le changer. `master` est le nom donné à votre branche principale. Ce n'est pas une bonne chose de travailler dans votre branche principale. Bien sûr vous pouvez très bien configurer GitHub, pour que "master" ne soit plus la branche principale, mais c'est n'est pas non plus une bonne pratique.

Pour le moment je vous fais faire cela de cette manière par simplicité. Mais dans la partie **Collaboration** je vous donnerai les bonnes habitudes à avoir.



2. La commande pull : 

Comme vous vous en doutez, s'il existe une commande pour envoyer (`push`) votre travail sur GitHub, il en existe une, `pull` pour récupérer votre travail depuis GitHub.

Seulement, depuis votre ordinateur, il faut être situé dans un dossier relié à votre repository GitHub. C'est ce qu'on a fait lorsqu'on a exécuté la commande : 

```shell
git remote add origin git@github.com:Nicolas-Hermet/rep_test_Git_GitHub.git
```



La commande git pull s'exécute comme suit : 

```shell
git pull origin master
```

Encore une fois on indique `origin` et `master` mais on verra plus tard la gestion des branches. 



### Exercice : <a id="Exercice"></a>

Je vous propose donc l'exercice suivant.

Dans GitHub, cliquez sur le bouton suivant : 

![02github_10](/pictures/02github_10.png)

Cela ouvrira la fenêtre suivante que vous pourrez remplir comme moi : 

![02github_11](/pictures/02github_11.png)

En bas de cette page vous allez retrouver un formulaire relativement familier : 

![02github_12](/pictures/02github_12.png)

Le premier champ sera le message de commit que vous avez l'habitude de donner lorsque vous faites `git commit -m "C'est ce message là !"`

Le deuxième champ, optionnel, est là pour écrire plus de texte si vous en avez besoin. Bien sûr on pourrait faire ça aussi en invite de commande en faisant simplement `git commit` sans le `-m 'message'` mais je ne voyais pas l'intérêt de vous le dire avant.

Laissez cochée la case **commit directly to the master branche** et décochée la case **Create a new branch...**. 

Puis cliquez sur **Commit New File**.



Vous venez de faire votre premier commit directement sur le web !!! Félicitations.

Vous retombez normalement sur la page de votre repository. Vous pouvez constater que votre deuxième fichier est bien ajouté ! Son contenu est bien celui que vous aviez prévu.



Mais dans votre dossier, sur votre ordinateur, il n'existe pas. Faites donc : 

```shell
git pull origin master
```



Oh miracle !! Il devrait apparaitre.

Fastoche comme exercice n'est-ce pas ?



Vous vous demandez sûrement qu'est ce qu'il se serait passé, si vous aviez aussi créé ce même fichier sur votre ordinateur ? Et si le contenu de celui-ci avait été différent ? Ce sont d'excellentes questions. Je les aborde dans le chapitre dédié à la collaboration.


------


| <a href="03-Git.md">Chapitre précédent</a>  | <a href="05-GitAdvanced.md">Chapitre suivant</a> | 
|:-------------------:|:----------------:|
