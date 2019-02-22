# Git et GitHub de Noob à God

Vous venez de débarquer dans le monde merveilleux du versionnage de fichiers. Et là : c'est le drâme. Vous vous en sortez bien mieux avec des vieux copiés-collés et des fichiers en pagaille nommé v2 ; v2_corrigé ; v3_final ; v3_final_2019-01-12 etc...

## Bienvenue <a id="Bienvenu"></a>

Ici on va partir de zéro. Oui de zéro. Il suffira de continuer à lire tranquillement, et de faire les exercices demandés. Si vous n'êtes pas complètement manche, ou que vous avez plus de deux neurones qui clapotes dans le fond, tout devrait bien se passer.



[TOC]



### D'accord, mais quelle stack ? <a id="stack"></a>

La stack n'est pas compliquée puisqu'on va faire très simple : 

- Windows 10 (oui je sais, c'est le mal)
- VS Code
- Git
- ... GitHub bien sûr (sinon vous ne seriez pas là). Bien sûr on se connectera en SSH.

Pour installer tout ça je préparerais un document d'installation complet un peu plus tard. Pour le moment je vais considérer que tout cela est bien installé sur votre machine.

## Point sur Git

Oui je l'ai dit : on part vraiment de zéro.

De base lorsque vous mettez à jour un fichier (mettons un document word ou un readme.md), vous enregistrez régulièrement. Du moins j'espère. En tout cas, dans pas mal de cas, votre traitement de texte sauvegarde tout ce que vous faites, de manière à pouvoir utiliser le fameux `Ctrl + Z` lorsque vous souhaitez revenir en arrière. Génial non ?

### Alors pourquoi on s'emm\*\*\*\* avec git ?

Et bien parce qu'une fois que vous fermer votre fichier et que vous le rouvrez, en général vous ne pouvez plus faire `Ctrl + Z`. Pour les malins qui utilisent un traitement de texte capable de le faire malgré tout : éteignez brusquement votre ordinateur et rallumez-le... Ensuite on en reparle.

Bref c'est dommage. 

Un autre cas où le `Ctrl + Z` n'est plus si pratique est le suivant.

#### Le cas de retour vers le futur

Imaginons le cas suivant. Vous modifiez votre fichier au fur et à mesure, et vous le sauvegardez régulièrement. Chaque point ci-dessous représente une sauvegarde de votre fichier (soit par vous, soit par votre éditeur de texte). Les traits reliant les points signifient que vous modifiez le fichier : 

![01whygit_01](/pictures/01whygit_01.png)

A un moment donné, vous ressentez le besoin de revenir en arrière. Via `Ctrl + Z`par exemple ?

Cela donnerai ceci : 

![01whygit_02](/pictures/01whygit_02.png)

où ![01whygit_03](D:\ADN\Formation\Git\pictures\01whygit_03.png) représente un retour en arrière.



Très bien... mais comment revenez vous au point de repère ?

Et bien vous ne pouvez plus, sinon comment savoir si vous souhaitez revenir au point de repère, ou encore plus loin dans le temps ?



#### Le cas avec git

Cette fois-ci, utilisons git. Au lieu de simple points, nous allons leurs donner des noms juste pour nous repérer entre nous.

- Ø : représente un état quelconque et sauvegardé de votre fichier.
- $V_{1}$ : représente un **commit** de votre fichier. Imaginez un commit comme une sauvegarde qui aurait un nom.

![01whygit_04](/pictures/01whygit_04.png)

Cette fois-ci, grâce à git, il vous est tout à fait possible, lorsque vous vous retrouvez en $V_{5}$, de revenir en $V_{1}$, $V_{2}$, $V_{3}$ ou $V_{4}$.  Magique non ?



On peut même imaginer fusionner les différentes version de votre fichier : 

![1550766628198](/pictures/01whygit_05.png)

Et là vous commencez à sentir l'utilité d'un vrai outil de versionnage de fichiers.

Je ne parle même pas de la collaboration à plusieurs ! Tellement plus simple.



## Fonctionnement de Git

### Les différents espaces de travail

Les amis de chez NDP Software ont pondu un outil que je trouve personnellement génial pour comprendre le fonctionnement de git, et ainsi se repérer dans la multitude de commandes en ligne : 

<span style="text-align: centered;"><a href="http://ndpsoftware.com/git-cheatsheet.html">![01whygit_05](/pictures/01whygit_06.png)</a> </span> (lien cliquable)



On y retrouve les éléments suivants : 

- Espace de travail : c'est votre ordinateur, c'est là que vous travaillez, on ne changera pas votre habitude
- Index : un espace intermédiaire dans lequel vous direz à git de mettre les fichiers que vous voulez (ou voudrez) sauvegarder.
- Dépôt local : l'espace dans lequel vous sauvegardez vos modifications, vos fameux **commit**.
- Dépôt distant : l'endroit où vous lisez ces lignes. Oui GitHub. Mais cela peut être aussi un serveur, un disque dur externe, [GitLab](gitlab.com), n'importe. C'est une sauvegarde à l'identique de tous les commits que vous aurez décidé d'y mettre.
- Remise : ou stash pour les intimes. Considérez cela comme un espace temporaire. Nous y reviendrons.





