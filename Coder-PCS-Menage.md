---
title: "Coder-PCS-Menage"
author: "Marie Plessz"
date: "04/02/2022"
output: 
  html_document: 
    keep_md: yes
---

# Coder la PCS ménage selon la PCS 2020

Tiré de mes échanges avec Joanie Cayouette-Remblière et avec Pierre Mercklé (que je remercie).

## La PCS ménage dans la réforme des PCS

La PCS 2020 prévoit une nomenclature à 1 ou 2 chiffres pour les ménages, qui s'appuie sur la PCS de l'adulte ou les deux PCS du couple à la tête du ménage.

### Documentation : 

Amossé Thomas, Chardon Olivier, Eidelman Alexis et Groupe de travail du Cnis, [La rénovation de la nomenclature socio-professionnelle (2018-2019)](https://www.cnis.fr/wp-content/uploads/2018/01/Rapport-n%C2%B0-156.pdf), Paris, Conseil national de l’information statistique, 2019. p 42 sq.

###  nomenclature

Tableau 5 : les 7 groupes et 16 sous-groupes de la PCS Ménage (Amossé Chardon p 46)

- I. Ménages à dominante cadre
  - A. Cadre avec cadre
  - B. Cadre avec profession intermédiaire
- II. Ménages à dominante intermédiaire ou cadre
  - A. Cadre avec employé ou ouvrier
  - B. Cadre avec inactif ou sans conjoint
  - C. Profession intermédiaire ou cadre avec petit indépendant
  - D. Profession intermédiaire avec profession intermédiaire
- III. Ménages à dominante employée ou intermédiaire
  - A. Profession intermédiaire avec employé ou ouvrier
  - B. Profession intermédiaire avec inactif ou sans conjoint
  - C. Employé avec employé
- IV. Ménages à dominante petit indépendant
  - A. Petit indépendant avec petit indépendant, avec inactif ou sans conjoint
  - B. Petit indépendant avec employé ou ouvrier
- V. Ménages à dominante ouvrière
  - A. Ouvrier avec employé
  - B. Ouvrier avec ouvrier
- VI. Ménages mono-actifs d’employé ou d’ouvrier
  - A. Employé avec inactif ou sans conjoint
  - B. Ouvrier avec inactif ou sans conjoint
- VII. Ménages inactifs
  - A. Inactif avec inactif ou sans conjoint

### Mise en oeuvre dans R

Il faut utiliser les fonctions `cs_household()` et `gs_household()` du
package `datatools` [porté par Pierre Mercklé](https://github.com/pmerckle/datatools#readme). Elle prend en arguments les PCS à deux chiffres (ou plus) des deux 
conjoints.



```r
library(devtools)
install_github("pmerckle/datatools")
library(datatools)
csind1 <- c(32, 67, 21)
csind2 <- c(35, 54, NA)
cs_household(csind1, csind2)
```

```
## [1] "I-A"  "V-A"  "IV-B"
```

```r
gs_household(csind1, csind2)
```

```
## [1] "I"  "V"  "IV"
```

### Si l'installation de `datatools` échoue.

Chez moi elle a échoué, avec le message d'erreur suivant : 

> Error: le chargement du package ou de l'espace de noms a échoué pour 'datatools' in library.dynam(lib, package, package.lib) :  
>La DLL 'fansi' est introuvable : elle n'est peut-être pas installée pour cette architecture ?  
>Erreur : loading failed  
>Exécution arrêtée  
>*** arch - x64
>ERROR: loading failed for 'i386'


En m'appuyant sur [cette page d'aide](https://stackoverflow.com/questions/56585706/force-devtoolsinstall-github-to-install-only-32-bit-versions-of-packages), voici comment j'ai procédé:



```r
remotes::install_github("pmerckle/datatools",
                        INSTALL_opts = "--no-multiarch")
```


## La position sociale des ménages, au-delà de la PCS

Une proposition pour saisir la position sociale, sans se limiter à la profession : 

Cayouette-Remblière Joanie et Ichou Mathieu, « Saisir la position sociale des ménages : une approche par configurations », Revue francaise de sociologie, 2019, Vol. 60, nᵒ 3, p. 385‑427.

