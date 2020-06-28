Afin de developper ce shell, j'ai tout d'abord commencé par implémenter un prompt.
Ainsi, c'etait nécessaire pour tester aisement la fonction chdir et rester dans le shell.
Il m'a fallu donc implémenter deux fonctions principales, une pour lire une ligne entrée par l'utilisateur et une autre pour split la ligne par argument où le 1er argument est la commande et les autres sont ses arguments.

Ensuite, afin de simplifier mon code, j'ai séparer les fonctions et prototypes dans des Headers et Sources.

Aussi pour accompagner ces fichiers, un fichier string_utils qui permet de me simplifier l'utilisage de strings dans certains cas.

Ainsi, l'essentiel du sujet se situe dans le dumsh.c / dumsh.h 

J'ai pensé egalement que le moyen le plus efficace et le plus approprié de créer des tableaux de fonctions facilement executables contenant l'adresse de chacune des commandes implémentées 

Afin d'executer les commandes, J'ai créé la fonction dumsh_execute qui verifie si la commande entrée appartient aux fonctions implémentées ou si c'est un programme des commandes bash ou autres (comme bin/bash).


A l'interieur de celle ci, j'ai créer une fonction dumsh_launch qui lance un autre programme et si il y a une redirection alors ca attend un pid pour finir ou sinon on n'attend pas et on reprend la main sur le terminal.

Pour la premiere redirection, comme on avait besoin d'ecrire la sortie erreur à la fin du fichier separé par #, J'ai pensé qu'il serait interressant de sauvegarder la sortie erreur pour les commandes implémentées. Mais, J'ai eu un problème pour sauvegarder la sortie erreur appartenenant à un forked pid. 
Cependant, je l'ai juste sauvegarder dans un fichier err.tmp et j'ajoute  fichier avec le contenu de err.tmp et ensuite je le supprime lors de l'exit.

Pour la seconde redirection, c'etait plus simple.J'ai juste redirigé la sortie standard dans un fichier et sauvegarde le nom concaténé avec l'extension .err et redirigé la sortie erreur dedans.