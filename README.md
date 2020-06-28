# DUMSH
---
## Authors: Yaniv Benichou.
---
> Ce programme lance un shell avec des commandes qui ont été implémentés et qui permet de lancer d'autres programmes.<br/>

> Il est écrit en  __Bas niveau C UNIX language__. <br />

---
## Built-in commands:
	> * cd pathToGo [>][1,2][filename] - changer de repertoire
	> * help [>][1,2][filename] - affiche une aide pour le shell
	> * exit - quitte le terminal et retourne au repertoire parent.
---
## Redirections:
> Ce terminal permet aussi de faire 2 redirections:
> * >1 filename - ecrit la sortie standard dans le fichier  et y ajoute  80 '#' avant d'y ecrire la sortie d'erreur.
> * >2 filename - ecrit la sortie standard dans le fichier puis ecrit la sortie d'erreur dans le filename.err.
---
### Example of usage:
	make
	>> cd ..
	>> ls >1 fic.txt
	>> ls
	>> ls -R / >1 fic.txt
	>> exit
