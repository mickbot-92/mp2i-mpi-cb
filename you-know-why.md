# Guide pour Unowhy Y13

Après l'obtention du Bac, il est possible de devenir administrateur sur les PC de la région Île-de-France.

Il est alors recommandé de le réinstaller et/ou d'y installer Linux, afin de le rendre plus fluide notamment.


## Admin / BIOS

Le BIOS est grossièrement ce qui démarre en tout premier sur l'ordi à son allumage, et qui détermine quoi démarrer comme OS.

Par défaut c'est sur le stockage interne de l'ordi, mais là où c'est intéressant, c'est qu'il permet de faire démarrer temporairement sur les clés USB (utiles pour débugger ou ré-installer un OS).

Malheureusement sur les ordis Unowhy il vient avec un mot de passe inconnu : il est donc nécessaire de le retirer.


### Manière legit

Cette méthode requiert l'obtention des droits administrateur à la fin du cursus de Terminale.

[Toutes les informations sont retrouvables ici](https://iledefrance-unowhy.com/fin-de-cursus-2026/).

Enfin, sur la session admin, il suffira de se rendre sur `C:\Sortie_Parc\BIOS` afin de prendre connaissance du PDF `Lisez-moi.pdf` et d'appliquer ce qui y est indiqué.

Remarque : n'hésitez pas à me repartager le dossier `C:\Sortie_Parc` !


### Manière illegit

Si vous ne souhaitez/pouvez pas pour une raison quelconque suivre la méthode précédente, un autre moyen existe : il est possible de débloquer le BIOS [en suivant ce tuto](https://blog.sty1001.com/2024/07/29/unlock-le-bios-nimporte-quel-y13-gen-1-2023-et-avant-avec-la-methode-du-court-circuit/).

Néanmoins, le guide exige un autre PC admin où faire les manipulations concernant la clé USB. Alternativement, voici ce que je vous propose pour tout faire sur votre Y13 (sans droits admin) :
* Télécharger UTPE (le lien est dans son guide)
* Connecter une clé USB (dont le contenu sera supprimé !)
* Dans Explorateur de fichiers, faire un clic droit sur la clé, puis sélectionner Formater, en FAT32
* Une fois UTPE téléchargé, copier-coller son contenu sur la clé USB

Ce moyen contourne la nécessité d'obtenir les droits admin pour flasher un BIOS sans mot de passe. Ainsi vous êtes libres de réinstaller d'emblée l'ordi par exemple. En revanche, si vous voulez profiter des droits admin sur la configuration actuelle, il suffira de démarrer à nouveau sur UTPE et de conférer les droits admin à l'utilisateur `defaultuser0`, de l'activer et de reset son mot de passe (ainsi, depuis votre session, lorsque les identifiants d'un compte administrateur est demandé, entrez ceux de `.\defaultuser0`).


## Sauvegarder les drivers Windows

Étape facultative mais recommandée (droits admin obligatoires) : si d'aventures vous souhaitez réinstaller un Windows, cette sauvegarde sera utile car Unowhy dépend de drivers assez spécifiques pour bien fonctionner. Si cette section n'est pas suivie, ce n'est pas grave, [Unowhy Tools](https://github.com/STY1001/Unowhy-Tools) a déjà des sauvegardes pour votre version de PC.

Deux méthodes pour les sauvegarder :

* En utilisant justement l'utilitaire [Unowhy Tools](https://github.com/STY1001/Unowhy-Tools) ; la sauvegarde est assez bien fléchée, mais je ne sais pas si ça vaut le coup de l'installer juste pour ça…

* En utilisant la ligne de commande :
  * Créer un dossier `Drivers` (par exemple) à la racine de l'ordi.
  * Ouvrir un CMD avec les droits administrateur (clic droit sur CMD).
  * Exécuter la commande `DISM /online /export-driver /destination:C:\Drivers`
  * Sauvegarder le dossier `C:\Drivers` quelque part.

Remarque : Unowhy Tools vous permet bien d'autres choses sur l'ordi Unowhy si vous souhaitez ne rien réinstaller.

## Préparer une clé USB
C'est grâce à une clé USB que vous pourrez (ré)installer un OS sur un ordi. Sur un ordinateur avec droits admin (par forcément le Unowhy), je vous recommande de lancer [Ventoy](https://ventoy.net/en/download.html) afin de l'installer sur une clé : sa particularité est qu'il y aura juste à télécharger l'ISO (le fichier qui contient l'OS à installer) et à le déplacer sur la clé, sans plus.

## Télécharger un OS

Après l'installation de Ventoy, vous aurez simplement à vous rendre sur la page de téléchargement d'un OS, d'où vous acquérerez un fichier ISO à déplacer sur la clé Ventoy.

**Astuce** : un des gros avantages de Ventoy, est qu'avec une clé suffisamment grosse, on peut y télécharger plusieurs ISO, et ainsi démarrer sur celui de son choix. Profitez-en pour tester les différents Linux qui existent ! les ISO ayant généralement une version de démo.


### Windows
Si par hasard vous ne pouvez vous défaire de Windows et/ou que vous souhaitez avoir Windows et un Linux en même temps (configuration nommée « dual-boot » : vous choisissez sur lequel démarrer en allumant l'ordi), il est tout à fait possible de le réinstaller :

* [Windows 11 classique](https://www.microsoft.com/software-download/windows11) : vers le bas de la page, vous trouverez une section pour télécharger le fichier ISO.

**Remarque 1** : Votre ordinateur a une clé Windows édition Pro de pré-intégrée, qui normalement s'activera après installation.

* [Windows 11 IoT Enterprise LTSC](https://www.microsoft.com/evalcenter/download-windows-11-iot-enterprise-ltsc-eval) : c'est un Windows officiel qui vient déjà activé pour 3 mois d'emblée (renouvelable), et qui n'a pas tant d'applis préinstallées que ça (seulement Microsoft Edge), ce qui le rend plus léger (et je peux au moins installer des applis open-source style Firefox, VLC, etc.). Par ailleurs, les mises à jour peuvent tenir longtemps. Sélectionnez l'édition *x64 / AMD64* pour télécharger l'ISO à mettre sur la clé Ventoy.

**Remarque 2** : Il reste possible de coder en C sur Windows nativement et/ou d'installer Linux directement dans Windows, mais ce n'est pas recommandé !

**_Attention_** : BitLocker risque de compromettre une bonne expérience de dual-boot, il est vivement recommandé de le désactiver !

### [Linux](choix-linux)
Cliquez sur le titre pour avoir ma liste !

## Installer un OS
* Éteindre l'ordi si ce n'est fait.
* Brancher la clé Ventoy avec le ou les ISO.
* Allumer l'ordi en spammant la touche Échap
* S'assurer qu'il n'y a aucun mot de passe de demandé, puis se rendre sur le menu tout à droite en cliquant plusieurs fois sur →.
* Dans le menu des disques, sélectionner la clé USB.
* Après démarrage de Ventoy, sélectionner l'ISO voulu.
* (Leur lancement prend un peu de temps.)
* Tester l'OS, puis s'il convient, l'installer en suivant les instructions. Enjoy !
