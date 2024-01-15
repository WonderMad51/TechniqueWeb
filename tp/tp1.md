# **TP1**
![Alt text](/img/tp1.png)

## ***Tâche 1***
J'ai `git fork` le repository sur mon profil pour ensuite faire :
```sh
git clone https://github.com/WonderMad51/vscode.git
```  
![Alt text](/img/Tp1Tache1.png)

## ***Tâche 2***
Je me déplacer dans le dossier 'vscode' et j'utilise la commande :
```sh
git log --oneline
```  
Qui me donne la liste de tous les commits.<br>
On   retrouve des fix :
![Alt text](/img/Tp1Tache2.png)
Et de nouvel feature comme :
![Alt text](/img/Tp1Tache22.png)

## ***Tâche 3***
J'utilise 'q' pour sortir de ma liste de commit.<br>
Je crée une nouvelle branch et me déplace dessus avec :
```sh
git checkout -b "branchTp"
```  
Je modifie le fichier README.md :
![Alt text](/img/Tp1Tache3.png)
Mon fichier est racké et est bien modifié :
![Alt text](/img/Tp1Tache32.png.png)
Je procède au commit de ma modification :
```sh
git add .
```
>Pour prendre l'ensemble des fichiers modifiés, en l'occurence, uniquement le README.md
```sh
git commit -m "Commit du TP1 Tache 3"
```
Et la finalité :
![Alt text](/img/Tp1Tache33.png)