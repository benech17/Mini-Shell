SYSTÈME
=======

**L3 Informatique**


## Sujet : `dumsh`, un petit shell qui joue sur les sorties

Le projet à faire est un mini-shell (merci de bien lire la suite car
on ne lui demande pas tout à fait la même chose qu'aux shells
courants).

Votre `dumsh` doit être capable d'exécuter toute commande externe
(y compris en tenant compte du `PATH`), avec toutes ses options et
arguments possibles. Les seules commandes internes que nous vous demandons
d'implémenter sont `cd` et `exit`.

**Il n'est pas demandé d'enchaînement de
commandes (d'aucun type : `;`, `|`, `&&`, `||` ou tout autre
enchaînement que nous avons pu oublier)**.

Les **redirections** de `dumsh` sont **redéfinies**
ci-dessous. **Les redirections habituelles de vos shells préférés ne
sont pas demandées**.

En l'absence de redirection de sortie, `dumsh` affichera la sortie
standard en vert et la sortie erreur en rouge. L'invite du shell dans
ce cas ne devra pas revenir avant la fin de l'affichage des deux
sorties. Pour vous aider :

```C
    #define RED "0;31"
    #define GREEN "0;32"

    /* ... */
        printf("\033[%sm%s", color, msg);
    /* ... */
```

Les affichages doivent se faire dans la mesure du possible dans
l'ordre où ils ont été produits. En particulier, la sortie standard et
l'erreur standard sont a priori entremêlées. (Ce point particulier
peut être testé par exemple avec un `ls -R /` en s'arrangeant pour que
certains fichiers de l'arborescence ne puissent pas être listés.)

Le shell `dumsh` admet également deux redirections :

* `>1` suivi d'une chaîne de caractères qui est un nom de fichier
  admissible (fichier existant ou non); la sortie standard et la sortie
  erreur doivent alors être écrites dans ce fichier, dans l'ordre suivant
  : d'abord toute la sortie standard, puis un retour à la ligne, un trait
  de 80 `#`, un retour à la ligne, puis toute la sortie erreur. Si le
  fichier préexistait, son contenu doit être écrasé.
* `>2` suivi d'une chaîne de caractères qui est un nom de fichier
  admissible, par exemple `fic`; la sortie standard devra être écrite
  dans ce fichier (dans notre exemple `fic`) et la sortie erreur dans un
  deuxième fichier dont le nom est déduit du premier en lui concaténant
  `.err` (dans notre exemple `fic.err`). Les contenus des deux fichiers,
  s'ils préexistaient, doivent être écrasés.

En cas de redirection, `dumsh` doit reprendre immédiatement la main
dans le terminal.

Nous vous imposons par ailleurs la contrainte suivante : toutes les
lectures/écritures autres que les messages d'erreurs doivent être
réalisées en bas niveau (appels système `read`, `write`, etc).


## Modalités d'exécution (et de test)

Pour éviter toute contestation de type "mais si madame, chez moi ça
marche", la règle est que ce mini-projet doit fonctionner correctement
sur une machine virtuelle exécutant l'image ISO fournie.

L'image iso que nous vous proposons est la suivante :
[ubuntu-18.04.3-desktop-amd64.iso](http://releases.ubuntu.com/18.04.3/ubuntu-18.04.3-desktop-amd64.iso). Vous
pouvez tester que le téléchargement s'est bien passé ici :
[sums](http://releases.ubuntu.com/18.04.3/).

Ce sujet étant assez court, nous serons d'autant plus attentifs au fait
que le programme proposé soit bien finalisé : notamment exécution
correcte en toutes circonstances, et code propre, élégant et bien
structuré.


## Modalités de rendu

Ce mini-projet est à faire individuellement. Aucune exception ne sera
tolérée.

Chacun doit créer un dépôt `git` privé sur
le [gitlab de l'UFR](https://gaufre.informatique.univ-paris-diderot.fr/) **dès
le début de la phase de codage** et y donner accès en tant que `Reporter` à
tous les enseignants du cours de Système : Ines Klimann, Dominique Poulalhon,
Claude Stolze et Stefano Zacchiroli. Le dépôt devra contenir un fichier
`AUTHORS` donnant vos coordonnées (nom, prénom, numéro
étudiant et pseudo(s) sur le gitlab). Vous devez également envoyer un
mail à `klimann@irif.fr` pour donner l'url de ce dépôt (très important
car les mails de `gaufre` ne sont plus relayés par le serveur de l'ufr).

En plus du programme demandé, vous devez fournir un `Makefile`
utilisable, un `README`, et un fichier `ARCHITECTURE` (idéalement en
format Markdown, donc avec extensions `.md`) expliquant les stratégies
adoptées pour répondre au sujet.

En cas de question et si la réponse n'est pas contenue dans le présent
document, merci de poser la question sur le forum `moodle` dédié du
cours de systèmes. Seules les réponses postées sur ce forum feront foi
au moment de la correction.

Les seules interdictions strictes sont les suivantes : plagiat (d'un
autre projet ou d'une source extérieure à la licence), utilisation de
la fonction `system` de la `stdlib`, utilisation de lectures/écritures
haut niveau (sauf `perror`).


## Rendu

On attend de tous les mini-projets qu'ils puissent se lancer sur une
machine virtuelle avec l'image ISO fournie. La date limite de rendu
est le 28 juin. Il n'y aura pas de soutenance, mais nous ne nous
interdisons pas de contacter certains d'entre vous par mail ou de
demander une visio pour des explications.
