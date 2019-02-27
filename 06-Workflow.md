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



![02github_15](D:/ADN/Formation/Git/pictures/gitflow.svg)



Ici la branche master représente la version en production, la branche de Develop, la version en cours de développement, et les branches Feature celle en cours d'élaborations par vos collègues



Ainsi, à chaque nouvelle tâche, vous partez de la branche Develop, vous créez votre nouvelle branche Feature, vous développez et ensuite, UNE FOIS SEULEMENT que vous avez vérifier que cela n'ajoutait pas de bug, vous faites un merge sur la branche Develop.

Une fois de temps à autre, avant chaque release : vous faites un merge sur la branche master, afin d'en faire profiter vos utilisateurs.