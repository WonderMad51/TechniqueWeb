# **Git**

La différence entre Git et les autres SCMs, sont dans la façon dont Git considère les données.<br>
La plupart des autres SCMs stockent les informations sous forme d'une liste de modifs apportés à chaque fichier au fil du temps.<br>
Alors que Git, considère les données comme un ensemble de snapshots d'un mini système de fichier.<br>
Git ne stocke pas le fichier à nouveau, mais un len vers le fichier identique précédement stocké.

![Alt text](/img/gitgestion.png)

Git gère l'intégriter des données.<br>
Impossible de modifier un fichier sans que Git ne le sache pas.<br>
Le mécanisme qu'utilise Git est appelé une empreinte `SHA-1`. Un chaine de caractères composées de 40 caractères hexdécimaux qui ressemble à ça :
```sh
24b9da655589155aa489562fe151982
```
**Avec Git très peu d'opérations sont destructives**<br>

Git a troid état principaux dans lesquels peuvent se trouver vos fichiers :
- Working directory
- Staring area
- .git directory (Repository)

### Le première utilisation de Git
Git possède un un outil : Git config.<br>
Il permet de configurer les paramètres de Git sur notre système.  Ils peuvent être stocké dans 3 ednroits différents :
- [chemin]/etc/config
- fichier ~/.gitconfig
- fichier config dans le répertoire Git d'un dépôt en cours d'utilisation (specifique au dépôt en local) donc les valeurs .gi/config écrasent celles de /etc/config

Sur OS Windows, Git recherché fichier `.gitconfig`.<br>
Le fichier ne peut être modifié qu'avec la commande `git config -f` en tant qu'administrateur.

#### Pour en savoir plus, entrer la commande :
```sh
git config --list --show-origin
```
#### Configurez son identité
```sh
git config --global user.name "JohnDoe"
git config --global user.email "mon@mail.com"
```
#### VIM
i -> pour passer en mode instertion
echap -> pour sortie dans le mode dans lequel on se trouve
:wq -> pour quitter et sauvegarder (w pour write et q quitter)
:q! -> pour quitter sans sauvegarder

On doit passer le nom de la branch principal de "master" à "main" pour remplacer la notion de mâitre-esclave.
```sh
git config --global init.defaultBranch main
```

#### Vérifier ses paramètres
```sh
git config --list
git config user.name
```

#### Obtenir à l'aide
```sh
git help config
```

### Base de Git
/!\Pas d'espace ni de caractère spéciaux dans les noms/!\
**Pour cloner un dépôt existant :** 
```sh
git clone 'https du dépôt distant'
```

**Pour consulter l'état du dépôt:** 
```sh
git status
```

**Premier push:** 
```sh
git push --orgin master
```

**Ignorer des fichiers**<br>
Il suffit créer un fichier .gitignore et d'y ajouter les élèments a ignorer.<br>
`vim .gitignore` et ajouter ce qu'il y a à ignorer

**Consulter l'état d'un fichier**
```sh
git status
git diff
```
`git status` présente l'état global du dépôt , modifié ou non et `git diff` présente les modifications apportées aux fichiers.<br>
On peut utiliser `git diff` de façon plus précise :
```sh
git diff --staged
```

**Valider des modifications**
```sh
git commit -m "message"
```

**Effacer des fichiers**
```sh
rm <fichier>
git status
git rm <fichier>
```
Dernière forme va supprimer le fichier au prochain commit.
```sh
git rm --cached <fichier>
```  
Cette commande va supp le fichier de l'index mais pas du disque dur.

**La commande log est très puissante et possède de nombreuses options. En voici quelques-unes :**

```sh
git log -p -2
```
Cette commande affiche les deux derniers commits avec les différences introduites.

```sh
git log --stat
```
Cette commande affiche des statistiques sur les fichiers modifiés à chaque commit.

```sh
git log --pretty=oneline
```
Cette commande affiche chaque commit sur une seule ligne.

```sh
git log --pretty=format:"%h %s" --graph
```
Cette commande affiche l’historique sous forme d’un graphe.

**Annuler des modifications**
```sh

git commit --amend
```
Cette commande permet de modifier le dernier commit.

```sh
git reset HEAD <fichier>
```
Cette commande permet de retirer un fichier de l'index.

![Alt text](/img/gitcyclevie.png)

**Quel types d'accès utiliser:**
- https : pour un accès en lecture seule (read-only)
- ssh : pour un accès lecture/écriture (read/write)
- personnal access token (PAT) :

#### Desindexer des elements deja commits

TODO: A completer

#### La creation de tags (ou etiquettes)
En plus d'identier les commits par des identifiants uniques, Git vous permet aussi d'etiqueter un certain etat de l'historique (commit) comme etant important. Cela peut etre utile pour marquer des versions de votre code source.
```sh
git tag -a v1.0 -m "Version 1.0"
```

On peut lister les tags avec la commande suivante :
```sh
git tag
```
On peut aussi filtrer les tags avec la commande suivante :

```sh
git tag -l "v1.8.5*"
```
Pour visualier une etiquette, on utilise la commande suivante :

```sh

git show v1.4
```

![Alt text](/img/image-4.png)

#### Sur Github :
>-> setting
>>    -> Dev Setting
>>> -> Personnal Access Token
>>>>-> Token Classic <br>
Configurer un token avec ses autorisations et ça durée de validitée


## Les branches

Lorsque vous faites un commit, Git enregistre un objet de commit qui contient un pointeur vers l’arbre de contenu qui représente l’état de votre projet à ce moment-là. Ce pointeur de commit contient le nom SHA-1 du commit parent ou des commits parents qui ont précédé ce commit (il peut y avoir plus d’un parent dans le cas d’un commit de fusion). Par conséquent, à partir d’un commit, Git peut remonter toute l’histoire de votre projet.

Pour creer une branche il suffit d'utiliser la commande suivante :
```sh
git branch <nom-de-branche>
```
Pour basculer vers une branche il suffit d'utiliser la commande suivante :
```sh
git checkout <nom-de-branche>
```
Pour créer et basculer directement sur une branch :
```sh
git checkout -b <nom-de-branche>
```

### Fusionner des branches
***Situations***
![Alxt Text](/img/image.png)
On va commencer à travailler sur l'issue 53 et effetcuer un 1er commit :
```sh
git checkout -b iss53
```
![Alt text](/img/image-1.png)
On a commencer à travailler dessus et décide de réaliser notre premier commit :
```sh
git commit -m "commit 3"
```
![Alt text](/img/image-2.png)
On va ensuite rebasculer sur la branche msater afin d'effectuer un hotfix :
```sh
git checkout master
```
![Alt text](/img/image-3.png)
```sh
git branch hotfix
git commit -m "commit 4"
```
Nous sommes satisfait du hotfix et nous allons le valider :
```sh
git checkout master
git merge hotfix
```
On note la stratégie de merge utilisée par Git: Fast-forward
![Alt text](/img/image-44.png)
La branch hotfix n'a plus lieu d'être et nous allons la supp :
```sh
git branch -d hotfix
```
On va retourner sur iss et conitnuer de travailler dessus :
```sh
git checkout iss53
```
On effectue un nouveau commit afin de valider notre travail :
```sh
git commit -m "commit 5"
```
![Alt text](/img/image-5.png)
On va maintenant retourner sur master et effectuer un merge avec iss53 :
```sh
git checkout master
git merge iss53
```
La stratégie de merge est alors différente de celle uilisée précedement: Merge commit
![Alt text](/img/image-6.png)
Au lieu d'avancer la branch master, Git crée un nouveau commit qui contient les différences entre les 2 branches.
![Alt text](/img/image-7.png)
On peut supprimer la branch iss53 :
```sh
git branch -d iss53
```

### Resoudre des conflits

Un conflit a lieu lorsque deux branches differentes ont modifiees la meme partie du meme fichier, ou si un fichier a ete supprime dans une branche alors qu'il a ete modifie dans une autre.

![Alt text](/img/image-8.png)

Physiquement, un conflit est represente par des caracteres speciaux qui apparaissent dans le fichier.

![Alt text](/img/image-9.png)

Apres resolution du conflit il suffit de commit.

Vous avez un outil qui permet de resoudre les conflits avec git :

```sh
git mergetool
```

Pour afficher toutes les bramches :

```sh

git branch -a
git branch --all
```

Parlons un peu de la commande `git fetch <distant>` : elle permet de synchroniser vos travaux, elle va rechercher le serveur qui heberge `<distant>` et va recuperer les modifications qui ont ete effectuees sur le serveur distant.

#### Pousser des modifications
```sh
git push <distant> <branche>
git push origin master
git push -u origin master

```
Pour recuperer les modifications effectuees sur le serveur distant a propos de nouvelles branches ou de branches existantes :
```sh
git fetch <distant>
```
Pour recuperer des modifications et les fusionner avec vos branches locales :
```sh
git pull <distant> <branche>
```
La regle d'or lorsqu'on debute avec Git:
`commit` -> `pull` -> `push`<br>
Lorsque vous recuperez des branches distantes avec la commande fetch, vous ne creez pas automatiquement une branche locale qui suit la branche distante.<br>
Vous devez creer une branche locale et la lier a la branche distante.
```sh
git checkout -b <nom-de-branche> <distant>/<nom-de-branche>
Branch <nom-de-branche> set up to track remote branch
<nom-de-branche> from <distant>.
```
On a un raccourci pour cette commande :
```sh
git checkout --track <distant>/<nom-de-branche>
```
Il y a meme encore plus court, si la branche locale n'existe pas encore :
```sh
git checkout <nom-de-branche>
```
Afin de visualiser tout ça on peut utiliser la commande suivante :
```sh
git fetch --all
git branch -vv
```
Analysons un peu la commande suivante :
```sh
git push origin --delete une-branche
```

### Rebaser votre travail
Avec Git il y deux manieres d'integrer les modifications d'une branche dans une autre :

- La fusion (merge)
- Le rebasage (rebase)

![Alt text](/img/image-10.png)

Apres un merge on obtient cela:
```
git checkout master

git merge experiment
```
![Alt text](/img/image-11.png)
Avec le rebase on aurait entré les commandes suivantes :
```sh
git checkout experiment
git rebase master
```
Et voici ce qui se passe :<br>
![Alt text](/img/image-12.png)
Et voici le resultat final:<br>
![Alt text](/img/image-13.png)

### Rebaser votre travail (avancé)
![Alt text](/img/image-14.png)
La commande qui correspond au rebase cité en cours :
```sh
git rebase --onto master server client
```
Essaye d'extraire la branche client de la branche server et de la rebaser sur la branche master.
![Alt text](/img/image-15.png)
```sh
git checkout master
git merge client
```
![Alt text](/img/image-16.png)
On peut aussi rebaser la branche server sur la branche master :
```sh
git rebase master server
```
![Alt text](/img/image-17.png)
Vous pouvez ensuite merge server dans master:
```sh
git checkout master
git merge server
```
![Alt text](/img/image-18.png)

### Rebase or not Rebase ?

La seule regle a respecter avec la commande Rebase: ne jamais rebase des modifications qui ont ete publiees sur un serveur distant (push).