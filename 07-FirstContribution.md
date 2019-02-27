# Votre première collaboration en ligne


<div id="toc_container" style="background-color: #f7faff;">
<div id="toc-wrapper" style="margin-left: auto;margin-right: auto; width: 40%;">
<p class="toc_title"><strong>Sommaire du chapitre</strong></p>
<p><a href="Readme.md">Retour au sommaire</a></p>
<ol class="toc_list" start="1">
  <li><a href="06-Workflow.md">Workflow - travailler en équipe</a></li>
  <li><a href="07-FirstContribution.md">Votre première collaboration en ligne</a></li>
  <ol>
    <li><a href="07-FirstContribution.md/#notions">Quelques notions rapide</a></li>
    <ol>
    <li><a href="07-FirstContribution.md/#Clone">Clone</a></li>
    <li><a href="07-FirstContribution.md/#Fork">Fork</a></li>
    <li><a href="07-FirstContribution.md/#Pull">Pull Request</a></li>
    </ol>
    <li><a href="07-FirstContribution.md/#ExerciceG">Exercice Guidé</a></li>
    <li><a href="07-FirstContribution.md/#ExerciceNG">Exercice Non Guidé</a></li>
  </ol>
  <li><a href="08-AdditionnalTricks.md">Trucs et astuces supplémentaires</a></li>
</ol>
</div>
</div>


------


## Quelques notions rapide <a id="notions"></a>

### Clone <a id="Clone"></a>

1. **Qu'est ce que c'est ?**

La copie intégrale du repo (dans la branche spécifiée) sur votre ordinateur (espace de travail) avec un lien direct vers votre repo. Git est donc déjà initialisé et vous aurez accès, depuis votre ordinateur, aux `git log`, `git blame` etc.

Seulement il faut avoir les droits d'accès à ce repo : être collaborateur dessus ou faire parti de l'organisation ou de l'équipe qui maintient le code. C'est le cas pour votre propres repositories.

2. **Comment on fait ?**

Rendez-vous sur un de vos repository, et cherchez le bouton *Clone or Download* : 



![03Collab_01](D:/ADN/Formation/Git/pictures/03Collab_01.png)

Comme vous le voyez le menu qui s'affiche, vous avez 4 possibilités. La première est de l'ouvrir dans l'application GitHub Desktop (si vous l'avez téléchargée) : **Open in Desktop**, la deuxième est de **Download Zip** qui téléchargera la copie de la branche sur laquelle vous vous trouvez au format zip sur votre ordinateur. Cependant vous perdrez toute notions de git, pas d'init, pas de commit possible, pas de push ni de pull...

Enfin : soit vous clonez ce repository par la méthode SSH (Vous pouvez normalement le faire si vous avez suivi l'installation), soit en HTTPS.

La différence entre les deux est la suivante : 

- Par HTTPS : vous rentrerez votre login et mot de passe chaque fois que vous ferez un push
- Par SSH : vous rentrerez votre phrase de passe une seule fois par redémarrage de votre ordinateur.

Si vous n'avez pas de phrase de passe, l'option SSH est encore plus rapide.

3. **Et maintenant ?**

Et bien maintenant vous pouvez travailler sur votre ordinateur comme dans le chapitre précédent. 

**Note : ** vous pouvez cloner plusieurs fois le même repository. Vous serez alors dans le schéma suivant, et pourrez mieux simuler les actions de Jean-Claude, ou Jean-Claudine... c'est d'ailleurs ce qui se passe quand votre collègue fera un clone de votre repository de son côté.



### Fork ? <a id="Fork"></a>

1. **Definition**

Un fork est une copie du repository sur votre compte GitHub. Vous devenez le propriétaire de la copie et pouvez faire ce que vous voulez avec : comme un clone par exemple.

Imaginez une fourchette. Le propriétaire du repository possède un des pics de la fourchette. Vous en possédez un autre.

GitHub gardera une trace du lien existant entre votre nouveau repository et celui que vous venez de fork. Cela sera pratique pour les pull request que vous verrez dans un instant.



2. **Comment faire ?**

Cherchez le bouton *Fork* en haut à droite du repository dont vous souhaitez un fork.

![03Collab_02](D:/ADN/Formation/Git/pictures/03Collab_02.png)

Cliquez dessus, le repository sera directement ajouté à vos repositories personnels. GitHub vous demandera peut-être où vous souhaitez ajouter ce repository : chez vous ? ou dans votre organisation (si vous faites partie d'une).

Bien sûr vous ne pouvez pas fork votre propre repository. Cela n'a pas de sens.



3. **Modifier le repository d'origine**

Pour envoyer une modification sur le repo d'origine il faudra faire une pull request, soit via GitHub directement, ou via VS Code. C'est ce que vous allez faire avec ce repository que vous êtes en train de lire :wink:



### Pull Request <a id="Pull"></a>

1. **Définition**

Une pull request est une demande de merge de votre branche, ou de votre fork vers une autre branche de votre repo ou du repo d'origine.

2. **Pourquoi la Pull Request est nécessaire** 

Dans le workflow vous êtes responsable de votre branche.

Mais toute l'équipe est responsable de la branche de Develop et Master. Donc lorsque vous faites un merge de votre travail sur l'une de ces deux branches, il faut que quelqu'un d'autre la valide avant. Les relecteurs (reviewers) doivent regarder votre code, le tester, et valider votre travail. Lorsqu'un nombre suffisant de relecteur à validé votre travail, alors celui-ci peut être merge.

C'est d'ailleurs le cas dans pas mal de projets. Les branches master et Develop sont bloquées en push. Cela signifie que vous ne pourrez pas exécuter `git push origin master` par exemple. Seul le propriétaire du projet peut faire un push sur ces branches. En dehors de lui, tous les autres devront passés par une Pull request.

Cela évite des accidents malencontreux, du style Jean-Claude, qui tente un `git push -f origin master` pour bien péter votre travail.



## Exercice guidé : <a id="ExerciceG"></a>

Nous allons, dans cet exercice, modifier ce repository. Oui, celui que vous êtes en train de lire. Nous le ferons à l'aide de VS Code. Nous pourrions le faire avec l'interface web de GitHub, ou tout autre outils. J'ai choisi de vous guider pas à pas par l'intermédiaire de VS Code pour des raisons purement professionnelles. Si toute fois vous souhaitiez faire autrement, je vous renverrai alors vers l'excellent repository suivant : [First Contribution](https://github.com/firstcontributions/first-contributions). Vous le constaterez, je me suis largement inspiré de sa méthode, et je tiens à remercier le propriétaire de ce repository d'avoir mis ce projet en license MIT. C'est d'ailleurs le cas de ce présent repository.



1. **Faites un Fork de ce repository**
2. **Clonez le repository ainsi créé**

Cliquez simplement sur le bouton ![03Collab_01](D:/ADN/Formation/Git/pictures/03Collab_01.png) et copiez l'adresse HTTPS ou SSH.

3. **Ouvrez VS Code**

Utilisez bien la commande `code` dans un terminal git bash pour ce faire.

![1551188647694](D:/ADN/Formation/Git/pictures/03Collab_06.png)

Normalement, la page d'accueil doit apparaitre comme ci-dessous. 

D'ici : tapez `F1` ou `Ctrl + P` puis `>`. 

<img src="D:/ADN/Formation/Git/pictures/03Collab_03.png" alt="Clone Popup (Command Popup)" />

Entrez `git clone` dans cette barre comme suit : 

<img src="D:/ADN/Formation/Git/pictures/03Collab_04.png" alt="Entrez git clone" />

Et copiez l'URL que vous venez de copier dans GitHub. Cela doit fonctionner aussi bien en SSH qu'en HTTPS.

<img src="D:/ADN/Formation/Git/pictures/03Collab_05.png" alt="Collez le chemin d'accès, ici en HTTPS" />

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

![03Collab_07](D:/ADN/Formation/Git/pictures/03Collab_07.png)



6. **Add et commit**

Vous savez désormais qu'il faut maintenant ajouter ce fichier à l'index, puis le commit. Sous VS Code, rien de plus simple, cherchez l'icone de versionnage sur la gauche de VS Code et cliquez dessus :

![03Collab_08](D:/ADN/Formation/Git/pictures/03Collab_08.png)

Normalement vous devriez avoir la liste des fichiers qui ont été modifiés : 



![03Collab_09](D:/ADN/Formation/Git/pictures/03Collab_09.png)



En passant votre souris sur le fichier Contributors.md vous constaterez que plusieurs symboles apparaissent : 

![03Collab_10](D:/ADN/Formation/Git/pictures/03Collab_10.png)

De gauche à droite : le premier sert à ouvrir le fichier si ce n'est pas déjà le cas. Le deuxième sert à annuler l'intégralité des changements apportés à ce fichier depuis le dernier commit, et enfin le `+` sert à ajouter le fichier à l'index. C'est le strict équivalent à `git add Contributors.md`.



![03Collab_11](D:/ADN/Formation/Git/pictures/03Collab_11.png)

Une fois ce fichier ajouté à l'index, vous pouvez entrer votre message de commit dans le champs situé juste au dessus et appuyer sur `Ctrl + Entrée` lorsque vous aurez fini.

Votre premier commit avec VS Code ! :champagne: :tada:



Maintenant : publiez votre branche. Ce sera fait bien entendu sur votre propre repository. Mais en fonction de votre méthode de clonage, VS Code vous demandera vos identifiants et mot de passe GitHub.

![03Collab_12](D:/ADN/Formation/Git/pictures/03Collab_12.png)



7. **Votre première pull request**

Si vous avez bien suivi la partie installation, vous pouvez la faire directement avec VS Code. En bas à gauche de votre fenêtre, si vous êtes dans la partie versionnage vous trouverez un panel pour la gestion des pull requests : 

![03Collab_13](D:/ADN/Formation/Git/pictures/03Collab_13.png)

Cliquez sur le bouton `+` et sélectionner la branche sur laquelle vous voulez faire votre merge.

**Rappel** : une pull request c'est avant tout un merge.

Dans cette capture d'écran vous ne voyez que la branche master de ce repository. La raison est simple : je ne peux pas fork mon propre repository. Pour vous normalement vous devriez avoir une autre ligne vous présentant la branche master de **mon** repository. C'est celle là qu'il faut choisir.



Une page doit s'ouvrir se présentant à peu près comme suit : 

![03Collab_14](D:/ADN/Formation/Git/pictures/03Collab_14.png)

Remplissez la partie description et éventuellement commentaire, afin de bien décrire au propriétaire du repository ce que vous avez fait et en quoi vous apporter une amélioration.

Dans le cas présent dites moi juste que vous souhaitez faire votre première contribution.



En essence, la pull request à ce stade est déjà créée. C'est pour cette raison qu'il n'y a pas de bouton "Envoyer" ou autre de la sorte. Mais dans l'encadré en bas à gauche, réservé aux pull request, vous verrez que la votre est bien apparue, et est en attente.

En attente de ma validation.



De mon côté je recevrais un mail me disant que vous souhaiter faire un merge de votre travail avec le mien. Je regarderais quels sont les différences de code, et validerais, ou vous demanderais de changer certaines choses.



Si j'accepte : vous venez de faire votre toute première contribution !!!!

Félicitations !! :champagne::tada:



## Exercice non guidé :<a id="ExerciceNG"></a> 

1. Contribuez à ce repository.
2. Faites une contribution, dans le dossier SandBox. Attention : aucun code ne sera autorisé. Seulement du MarkDown, HTML5, Text ou éventuellement du LaTeX. Mais n'oubliez pas que certaines personnes peuvent faire pareil que vous au même moment. Faites donc attention à Jean-Claude ou Jean-Claudine !


------


| <a href="06-Workflow.md">Chapitre précédent</a>  | <a href="08-AdditionnalTricks.md">Chapitre suivant</a> | 
|:-------------------:|:----------------:|
