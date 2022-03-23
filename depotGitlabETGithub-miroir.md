---
date: 2022-03-11
author: Marie Plessz
title: "Un projet Gitlab synchronisé sur github - miroir"
---

J'utilise Gitlab (forgemia) pour la recherche, mais j'ai aussi une page github.  
Je voudrais que mes projets puissent apparaître sur les deux, et se synchronisent automatiquement.

## La solution : le miroir. Comment faire?

Paramétrer le dépot sur forgemia pour qu'il soit maintenu synchronisé sur github.

Sur forgemia seule la synchronisation "push" est permise cad qu'il faut travailler sur forgemia, et github n'en est qu'une copie.

Voici les conseils que m'a donnés Élise Maigné (INRAE, (https://forgemia.inra.fr/elisemaigne)). 

>Sur github tu peux avoir des projets privés (idem sur gitlab), et ça n'est pas limité en nombre de projets. 
>Et pour ton cas des projets git "recherche" il me semble que comme tu dis c'est préférable d'avoir un projet sur une forge institutionnelle. 

>Si tu veux avoir une "copie" de tes projets sur github (ou gitlab) pour une meilleure visibilité ou pour centraliser tout au même endroit, tu as par exemple la fonctionnalité miroir : un projet de github est en fait un miroir de ce que tu fais sur forgemia, mis en jour en temps réel, la synchronisation se fait toute seule (en 5 minutes). ça revient au même que la solution de Valérie sauf que t'as pas besoin de faire la mise à jour à la main. 

## Voici le pas à pas que m'a indiqué Elise :

- dans Github : tu crées un projet VIDE, dont le nom est clair
- dans Github, tu crées un token si tu n'en as pas déjà un, avec les autorisations  "repo" and "workflow". tu le copie-colles précieusement quelque part. Voir ici https://github.com/settings/tokens  
- Dans le projet forgemia, tu vas  dans settings > repository et tu mets l'url de ton projet github. 
- Par défaut (et c'est la seule direction autorisée sur forgemia), le miroir est en push = le dépôt de forgemia va pusher sur le dépôt github. 
- Préparer l'url: à partir de github. **Elle doit être de cette forme là : `https://emaigne@github.com/emaigne/renv_package.git` .** où `emaigne` est ton identifiant github, et `emaigne/renv_package.git` est le bout de chemin vers le dépôt sur github.
- dans le champ "password" coller le token de Github.
- cliquer sur `Mirror Repository`
- attends quelques minutes: reviens sur la page du mirroring : la synchro va se faire.
- vas dans la section "about" sur la bage d'accueil du repo sur Github et écrit que c'est un projet miroir, avec un lien vers la source.

Et voilà !

Je me suis aussi appuyée sur https://docs.gitlab.com/ee/user/project/repository/mirror/push.html, mais il ne faut pas mettre le mot de passe dans le champ de l'url. Il faut respecter la forme donnée par Elise :  
https:// nom_github @github.com/nom_github/nom_repo.git

