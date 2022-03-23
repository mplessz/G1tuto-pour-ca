---
date: 2022-03-11
author: Marie Plessz
title: "Un projet Gitlab synchronisé sur github - miroir"
---

J'utilise Gitlab (forgemia) pour la recherche, mais j'ai aussi une page github.  
Je voudrais que mes projets puissent apparaître sur les deux, et se synchronisent automatiquement.

La solution : le miroir. Comment faire?

Paramétrer le dépot sur forgemia pour qu'il soit maintenu synchronisé sur github.

Sur forgemia seul la synchronisation "push" est permise cad qu'il faut travailler sur forgemia, et github n'en est qu'une copie.

Voici les conseils que m'a donnés Élise Maigné (INRAE, (https://forgemia.inra.fr/elisemaigne)). 

>Je confirme ce que dit Valérie sur forgemia, il ya qqs problèmes de connexion en cours de résolution mais ça n'est pas bloquant. 
>Par contre si, sur github tu peux avoir des projets privés (idem sur gitlab), et ça n'est pas limité en nombre de projets. 
>Et pour ton cas des projets git "recherche" il me semble que comme tu dis c'est préférable d'avoir un projet sur une forge institutionnelle. 
>Si tu veux avoir une "copie" de tes projets sur github (ou gitlab) pour une meilleure visibilité ou pour centraliser tout au même endroit, tu as par exemple la fonctionnalité miroir : un projet de github est en fait un miroir de ce que tu fais sur forgemia, mis en jour en temps réel, la synchronisation se fait toute seule (en 5 minutes). ça revient au même que la solution de Valérie sauf que t'as pas besoin de faire la mise à jour à la main. 
>J'ai fais un essai sur ça : (attention autopromo) 
>https://forgemia.inra.fr/elisemaigne/2021_package_renv et mon projet miroir : https://github.com/emaigne/renv_package
>Dans ton projet forgemia, tu vas dans settings > repository et tu mets l'url de ton projet github. 
>Par défaut (et c'est la seule direction autorisée sur forgemia), le miroir est en push = le dépôt de forgemia va pusher sur le dépôt github. 
>J'ai mis le nom de mon projet de cette forme là 
>https://emaigne@github.com/emaigne/renv_package.git
>Et j'ai du générer un token sur github à rentrer dans le champ mot de passe. Voir ici https://github.com/settings/tokens (don't forget to enable the "repo" and "workflow" permissions when generating it)
>Et je suis allée dans la section "about" sur la bage d'accueil pour dire que c'était un projet miroir, avec un lien.
>Et voilà !

Je me suis aussi appuyée sur https://docs.gitlab.com/ee/user/project/repository/mirror/push.html, mais il ne faut pas mettre le mot de passe dans le champ de l'url.

