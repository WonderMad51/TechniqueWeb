# Quoi le versioning ?

Versioning, gestion de version, permet de suivre et gérer des changements apportés au code source au fil du temps.<br>
Cela consiste à garder un trace de chauqe modification apporté au code.<br>
Pour chaque modification le système enregistre qui a fait le changement, pourquoi il a été fait et les détails de la modification.

On peut donc : 
- revenir à une version entérieur
- travailler en parallèle sur différentes fonctionnalités sans perturber le travail des autres

**Importance du versioning**
- Tracabilité
- Collaboration
- Backup et rétablissement
- Branching et merging : les dévs peuvents créer des branchs pour travailler sur des fonctionnalités ou des corrections séparément (branching) , puis intégrer ces changements dans la ligne principale de développement (mergin)

**Exemples de nomenclature de versioning :**
- MAJEUR
- MINEURE
- CORRECTIF

Un exemple de version peut être : `2.1.3`

Les deux principaux systèmes de contrôle de version sont :
- Git
- Subversion (SVN)

**Opération et fonctionnalités SVN**
- checkout/commit/update, est une opération locale
- branching/merging, permet le travail à plusieurs


**Opération et fonctionnalités Git**
- branching/merging, système plus simple et plus rapides
- stagging area, permet de préparer et de réviser les modifications avant de les commettres
- flexibilité, git support de nombreux workflow  

Contrairement à SVN, Git est distribué, signifiant que chaque développeurs a une copie complète du dépôt avec tout l'historique des versions.

**Diférence entre SVN et Git**
![Alt text](/img/svngit.png)

**On efface SVN de notre cerveau !!!**