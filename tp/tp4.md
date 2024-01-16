# **TP4: Revue de Code et Collaboration**
![Alt text](/img/tp4.png)

## ***Tâche 1***
Sur les Pull Request ils ajoutent des labels comme `awaiting review`, `ready to pull ` et autre pour ainsi informer de l'état de PR.

## ***Tâche 2***
Pour créer une pull request fictive, je vais créer une nouvelle Branch :
```sh
git checkout -b "branchTp4"
``` 
J'ai apporté des modifications au README.md pour pouvoir `commit` et ainsi `push` des modifications :
![Alt text](/img/Tp4Tache2.png)
Une voici cette étape faite, on passe sur Github.
![Alt text](/img/Tp4Tache22.png)
Si nous avons ce message c'est que notre `push` a bien fonctionné.
![Alt text](/img/Tp4Tache23.png)
Après avoir cliqué sur `Compare & pull request`, ça nous ouvre la fenêtre ci-dessus. On peut donc écricre ce qu'apporte nos modification, dans quel but etc, ajouter des captures du résultat ou du code etc... Détaillé pour qu'un autre utilisateurs puisse comprendre au mieux son utilité.<br>
Pour faire notre review, on va dans `file changed` pour voir les fichiers modifiés et lire le code. On peut y apporter des commentaires. A la suite de la relecture, la PR est accepter ou refuser (merge ou non).
![Alt text](/img/Tp4Tache24.png)
Après ça on peut valider notre PR en `Merge pull request` de notre PR et ainsi incorporer nos modifcations en production.
![Alt text](/img/Tp4Tache25.png)