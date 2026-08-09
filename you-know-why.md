# Guide pour Unowhy Y13
Après l'obtention du Bac, il est possible de devenir administrateur sur les PC de la région Île-de-France.
Il est alors recommandé de le réinstaller et/ou d'y installer Linux, afin de le rendre plus fluide notamment.

## Admin / BIOS
Le BIOS est grossièrement ce qui démarre en tout premier sur l'ordi, et qui détermine où démarrer.
Par défaut c'est sur les stockage interne de l'ordi, mais là où il est intéressant, c'est qu'il permet de faire démareer sur les clés USB (utiles pour débugger ou réinstaller un OS).
Malheureusement sur les ordis Unowhy il vient avec un mot de passe inconnu : il est donc nécessaire de le retirer.

### Manière legit
Cette méthode requiert l'obtention des droits administrateur à la fin du cursus de Terminale.
Toutes les informations sont retrouvables ici : https://iledefrance-unowhy.com/fin-de-cursus-2026/
Enfin, sur la session admin, il suffira de se rendre sur `C:\Sortie_Parc\BIOS\` afin de prendre connaissance du PDF `Lisez-moi.pdf` et d'appliquer ce qui y est indiqué.
Remarque : n'hésitez pas à me repartager le dossier `C:\Sortie_Parc` !

### Manière illegit
Si vous ne souhaitez/pouvez pas pour une raison quelconque suivre la méthode précédente, un autre moyen existe : il est possible de débloquer le BIOS en suivant ce tuto : https://blog.sty1001.com/2024/07/29/unlock-le-bios-nimporte-quel-y13-gen-1-2023-et-avant-avec-la-methode-du-court-circuit/
Ce moyen contourne la nécessité d'obtenir les droits admin pour flasher un BIOS sans mot de passe. Ainsi vous êtes libres de réinstaller d'emblée l'ordi par exemple. En revanche, si vous voulez profiter des droits admin sur la configuration actuelle, il suffira de démarrer à nouveau sur UTPE et de conférer les droits admin à l'utilisateur `defaultuser0`, de l'activer et de reset son mot de passe (ainsi, depuis votre session, lorsque les identifiants d'un compte administrateur est demandé, entrez ceux de `.\defaultuser0`).

## Sauvegarder les drivers Windows
Étape facultative mais recommandée (droits admin obligatoires): si d'aventures vous souhaitez réinstaller un Windows, cette sauvegarde sera utile car Unowhy dépend de drivers assez spécifiques pour bien fonctionner. Si cette section n'est pas suivie, ce n'est pas grave, [Unowhy Tools](https://github.com/STY1001/Unowhy-Tools) a déjà des sauvegardes pour votre version de PC.
Deux méthodes pour les sauvegarder :
* En utilisant justement l'utilitaire [Unowhy Tools](https://github.com/STY1001/Unowhy-Tools) ; la sauvegarde est assez bien fléchée, mais je ne sais pas si ça vaut le coup de l'installer juste pour ça…
* En utiisant la ligne de commande :
  * Créer un dossier `Drivers` (par exemple) à la racine de l'ordi.
  * Ouvrir un CMD avec les droits administrateur (clic droit sur CMD)
  * Exécuter la commande `DISM /online /export-driver /destination:C:\Drivers`
  * Sauvegarder le dossier `C:\Drivers` quelque part.
Remarque : Unowhy Tools vous permet bien d'autres choses sur l'ordi Unowhy si vous souhaitez ne rien réinstaller.

## Préparer une clé USB
C'est grâce à une clé USB que vous pourrez (ré)installer un OS sur un ordi. Sur un ordinateur avec droits admin (par forcément le Unowhy), je vous recommande de lancer [Ventoy](https://ventoy.net/en/download.html) : sa particularité est qu'il y aura juste à télécharger l'ISO (le fichier qui contient l'OS à installer) et à le déplacer sur la clé, sans plus.

## Télécharger un OS
Après l'installation de Ventoy, vous aurez simplement à vous rendre sur la page de téléchargement d'un OS, d'où vous acquérerez un fichier ISO à déplacer sur la clé Ventoy.
**Astuce** : un des gros avantages de Ventoy, est qu'avec une clé suffisamment grosse, on peut y télécharger plusieurs ISO, et ainsi démarrer sur celui de son choix. Profitez-en pour tester les différents Linux qui existent ! les ISO ayant généralement une version de démo.

### Windows
Si par hasard vous ne pouvez vous défaire de Windows et/ou que vous souhaitez avoir Windows et un Linux en même temps (configuration nommée « dual-boot » : vous choisissez sur lequel démarrer en allumant l'ordi), il est tout à fait possible de le réinstaller :

* [Windows 11 classique](https://www.microsoft.com/software-download/windows11) : vers le bas de la page, vous trouverez une section pour télécharger le fichier ISO.
**Remarque 1** : Votre ordinateur a une clé Windows édition Pro de pré-intégrée, qui normalement s'activera à l'installation.

* ♥️ [Windows 11 IoT Enterprise LTSC](https://www.microsoft.com/evalcenter/download-windows-11-iot-enterprise-ltsc-eval) : c'est un peu mon coup de cœur, car c'est un Windows officiel qui vient déjà activé pour 3 mois d'emblée (renouvelable), et qui n'a pas tant d'applis préinstallées que ça (seulement Microsoft Edge), ce qui le rend plus léger (et je peux au moins installer des applis open-source style Firefox, VLC, etc.). Par ailleurs, les mises à jour peuvent tenir longtemps. Sélectionnez l'éditioin *x64 / AMD64* pour télécharger l'ISO à mettre sur la clé Ventoy.
**Remarque 2** : Il reste possible de coder en C sur Windows nativement et/ou d'installer Linux directement dans Windows, mais ce n'est pas recommandé !

### Linux Mint
C'est l'OS recommandé pour les gens qui débutent dans Linux. Ça a en effet une interface similaire à celle de Windows 10 ((n'hésitez pas à regarder les captures d'écran ou à le tester). Voilà le lien vers la page du projet : https://www.linuxmint.com/
**Astuce** : activer les Gestes afin de mieux prendre en main l'OS avec le trackpad.

### Ubuntu/Debian/Fedora
D'autres Linux réuptés peuvent être testés : j'en ai sélectionné 3 gros.
* [Ubuntu](https://ubuntu.com/) : le Linux le plus répandu dans le monde de Linux. Il est dérivé de Debian.
* [Debian](https://www.debian.org/) : Sur [la page "live-boot" de Debian](https://www.debian.org/CD/live/index.fr.html), vous avez plusieurs variantes de bureau que vous pouvez tester (KDE, Gnome, Cinnamon, XFCE, etc.), n'hésitez pas à tous les télécharger [sur cette page](https://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/) et les tester !
* ♥️ [Fedora](https://fedoraproject.org/) : La particularité de ce Linux est qu'il utilise par défaut le système de fichier BTRFS, qui notamment compresse/décompresse les fichiers de manière instantanée et fluide, et a je crois de mises à jour plus tôt que Debian.
**Remarque** : Comme vous le remarquerez en essayant Debian Gnome ou Fedora Workstation, vous ne verrez aucune différence visuellement : ils sont effectivement basés sur [le bureau Gnome](https://www.gnome.org/) qui est le même pour tous. L'avantage avec ce bureau est qu'il prend d'emblée en charge la gestuelle du trackpad. Enfin des extensions peuvent rendre l'expérience Gnome plus agréable.

### Arch Linux
Arch Linux est un Linux « DIY », dans le sens où vous l'installez entièrement à la main en suivant le guide. C'est très formateur (vous comprendrez mieux l'envers du décor Linux), et permet une meilleure optimisation de l'ordi. N'hésitez pas à me demander mon propre guide Arch Linux, créé en l'installant sur mon propre Unowhy Y13 😉

## Installer un OS
Vous n'aurez simplement qu'à suivre les instructions au démarrage de l'ISO, si l'interface vous convient. Enjoy !