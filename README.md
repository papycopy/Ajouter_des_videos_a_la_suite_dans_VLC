**Ajouter des vidéos à la suite dans VLC directement depuis un clic droit sur un fichier ou un dossier sous cachyOS**
*(ou toute distribution Linux utilisant un environnement de bureau comme KDE, GNOME, XFCE, etc.),*
﻿
1. Configuration préalable dans VLC
Avant de créer le raccourci, assurez-vous que VLC est configuré pour accepter les ajouts à la file d'attente :
﻿
Ouvrez VLC.
 Allez dans Outils > Préférences (ou Ctrl + P). 
 Dans l'onglet Interface, cochez les cases :
 N'autoriser qu'une seule instance
 Mettre en file d'attente dans le mode une seule instance (si disponible). 
 Cliquez sur Enregistrer et redémarrez VLC.
﻿
2. Créer l'entrée de menu contextuel (Fichiers)
Cette méthode fonctionne pour la plupart des gestionnaires de fichiers (Nautilus, Dolphin, Thunar, etc.) via un fichier .desktop.
﻿
Ouvrez un terminal et créez le fichier suivant :
﻿
`nano ~/.local/share/applications/vlc-queue.desktop`
﻿
Collez le contenu suivant dans le fichier :
﻿
`[Desktop Entry]
Type=Application
Name=Ajouter à la file d'attente VLC
Exec=vlc --playlist-enqueue %F
Icon=vlc
NoDisplay=true
MimeType=video/x-ms-wmv;video/mp4;video/x-matroska;video/x-msvideo;video/quicktime;video/webm;   `
﻿
Enregistrez le fichier (Ctrl + O, Entrée, Ctrl + X) et rendez-le exécutable :
﻿
`chmod +x ~/.local/share/applications/vlc-queue.desktop`

**3. Pour les dossiers **
Si vous souhaitez ajouter tout le contenu d'un dossier d'un coup :
﻿
La méthode varie selon votre gestionnaire de fichiers :
﻿
**Pour Thunar (XFCE) :**
Allez dans Édition > Configurer les actions personnalisées.
Ajoutez une nouvelle action :
Nom : `Ajouter à VLC`
Commande :` vlc --playlist-enqueue %F`
Type de fichier : Cochez **Dossiers**. 
﻿
**Pour Nautilus (GNOME) :**
Il est souvent nécessaire d'installer une extension comme `nautilus-actions `(ou `filemanager-actions`) pour créer des menus contextuels personnalisés pour les dossiers, car le fichier `.desktop` seul ne suffit pas toujours pour les répertoires. 
**Pour Dolphin (KDE) :**
Allez dans Paramètres > Configurer Dolphin > Menu contextuel > Services.
Créez un nouveau service avec la commande `vlc --playlist-enqueue %F `et l'onglet "Conditions d'apparition" réglé sur "Fichiers et dossiers". 
﻿
**Utilisation**
Une fois configuré :
﻿
Sélectionnez un ou plusieurs fichiers vidéo (ou un dossier).
Faites un clic droit. 
Cherchez l'option Ouvrir avec ou directement Ajouter à la file d'attente VLC (selon votre configuration). 
Les vidéos s'ajouteront à la liste de lecture de l'instance VLC déjà ouverte et se liront à la suite.

Pour ajouter des vidéos à la file d'attente de VLC via le clic droit dans Nemo (le gestionnaire de fichiers par défaut de Cinnamon, la méthode la plus propre consiste à créer un fichier d'action personnalisé (`.nemo_action`). 
﻿
Contrairement aux autres gestionnaires de fichiers, Nemo utilise un format de configuration spécifique situé dans votre dossier personnel.
﻿
**1. Création de l'action Nemo**
Ouvrez un terminal et créez le fichier d'action dans le dossier dédié de votre utilisateur (pas besoin de droits root) :
﻿
`mkdir -p ~/.local/share/nemo/actions
nano ~/.local/share/nemo/actions/vlc-enqueue.nemo_action `  
﻿
Collez exactement le contenu suivant dans le fichier :
﻿
`[Nemo Action]
Active=true
Name=Ajouter à la file d'attente VLC
Comment=Ajoute les fichiers sélectionnés à la playlist VLC en cours
Exec=vlc --playlist-enqueue %F
Icon-Name=vlc
Selection=notnone
Extensions=mkv;mp4;avi;mov;webm;flv;wmv;mpeg;mpg;
Mimetypes=video/x-matroska;video/mp4;video/x-msvideo;video/quicktime;video/webm;   `
﻿
Enregistrez le fichier (Ctrl+O, Entrée) et quittez (Ctrl+X).
﻿
2. Activation
Pour que le changement prenne effet immédiatement, redémarrez Nemo avec cette commande :
`nemo -q`
﻿
Cela ferme toutes les fenêtres Nemo ouvertes ; rouvrez simplement votre gestionnaire de fichiers


