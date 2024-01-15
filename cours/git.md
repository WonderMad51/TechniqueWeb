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

**Ignorer des fichiers**
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
