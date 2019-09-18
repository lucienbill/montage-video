# montage-video
Vous souhaitez monter des best-of pour votre streameur préféré, et mettre vos montages sur YouTube ? Voici quelques infos pour bien démarrer.

Note : 
* je ne suis pas un expert, je ne suis pas un professionnel, mais j'ai fait quelques trucs et j'ai bien galéré à trouver certaines infos. Je les écrits ici pour permettre à d'autres de moins perdre de temps sur tout un tas de choses techniques qui n'ont, au final, pas grand chose à voir avec le montage à proprement parler.
* Avant de mettre une vidéo en ligne, je la regarde pour vérifier que je n'ai pas loupé un truc (exemple : il peut m'arriver d'exporter avec les mauvais régalges et d'avoir de la bouillie de pixels : je ne mets pas ça directement en ligne !)

# Les logiciels
## Mac ou PC ?
Peu importe. J'utilise Windows, donc je ne connais pas les logiciels pour mac.
Cependant les logiciels que j'utilise sont cross-platform.
Autrement dit : vous pouvez utiliser les logiciels que je propose, peu importe le système d'exploitation de votre machine.

## Quels logiciels utiliser ?
Si vous avez une licence pour un logiciel que vous maîtrisez déjà (exemple : Adobe Première), la question ne se pose pas : utilisez ce que vous avez déjà.
Si vous n'avez rien, surtout ne piratez pas : 
* c'est illégal
* il existe des options gratuites et légales qui fonctionnent très bien : c'est ce que j'utilise.

Je recommande ces 2 programmes : 
* [Shotcut](https://shotcut.org/download/)
* [Da Vinci Resolve](https://www.blackmagicdesign.com/fr/products/davinciresolve/)

Note : je recommande des les installer en anglais, parce qu'on trouve plein de tutos en anglais sur youtube.
Pour avoir essayé d'utiliser Shotcut en français : quand un tuto parle de "Rotate and scale" et que la fonctionnalité s'appelle en vrai "Mise à l'échelle et rotation", c'est pas pratique du tout.

## Shotcut
Pour monter des vidéos, il est simple et efficace, je l'utilise pour 90% de mes montages.
Shotcut se base sur la librairie "ffmpeg" qui est ultra flexible : il sait lire et écrire dans plein de codec différents.

Concrètement, cela signifie qu'on peut donner à peu près ce qu'on veut à Shotcut, il arrivera à intérpréter les signaux, et à exporter notre montage dans le codec que l'on veut (99% du temps, h264).

## Da Vinci Resolve
Ca, c'est l'artillerie lourde. Très puissant et polyvalent, permet de faire des effets spéciaux avancées et de bien retravailler les couleurs, parfait pour faire des court-métrages. 

Il est capricieux sur les codec : Resolve n'aime pas travailler avec des vidéos fortement compressées.
Il m'est déjà arrivé de faire un montage à base de vidéos compressées : tout semblait bien fonctionner jusqu'à ce que j'exporte la vidéo : il y avait quelques soucis d'images bien pénibles qui n'étaient pas visible dans l'aperçu, mais dont je ne parvenais pas à me débarraser.
Autrement dit : avec Resolve, ne travaillez jamais avec des vidéos très compressées !

**Comment régler ce soucis :** Il faut demander à Resolve de transcoder les sources vidéos vers un autre codec, puis travailler à partir des fichiers transcodés. [Cette vidéo](https://www.youtube.com/watch?v=XQ1xF0ZmltU) explique bien comment faire.

# Les codec
C'est, en bref, la façon dont est gérée le flux vidéo.
Spécifiquement : un codec correspond à une façon de compresser la vidéo.
Une bonne compression permet d'avoir une belle vidéo qui ne prend pas trop de place sur le disque dur.
Globalement, on va surtout exporter "h264", qui est très commun, et on streame aussi en h264 sur Twitch.

Peu importe le logiciel que j'utilise pour monter, je passe toujours par Shotcut pour transcoder la vidéo vers le bon codec avec les bon paramètres pour la plateforme que je vise (youtube, twitter, facebook...).
Transcoder = écrire une vidéo dans un autre fichier (généralement dans un autre codec, et/ou avec un autre bitrate. Exemple : prendre un DivX en 1080p et le transformer en .mp4 h264 en 720p)

## Compresser une vidéo
Quand je transcode une vidéo pour Youtube, Twitter ou autre, je la compresse, car ces plateformes préfèrent les fichiers avec un débit de données limité.
Pour compresser, je dis à Shotcut "écris ma vidéo dans ce fichier, avec ce bitrate".

La compression n'est pas magique : si on compresse trop fort ou trop vite, on fera de la bouillie de pixels. Généralement, je sais quel débit de données (alias **bitrate**) je ne dois pas dépasser. Je règle ensuite Shotcut pour qu'il compresse plus ou moins vite :
* si je veux la meilleur qualité possible, je lui dis "prends tout ton temps"
* si j'ai une grosse vidéo, que je veux l'exporter plutôt rapidement, et que j'accepte qu'il y ait une légère perte de qualité visuelle par moments, je lui dits "prends du temps pour compresser, mais reste raisonnable"

C'est la [vitesse d'encodage](https://trac.ffmpeg.org/wiki/Encode/H.264#a2.Chooseapresetandtune).
**\[To do\]** : mieux expliquer

### le principe des réglages dans Shotcut
Dans Shotcut, voici comment accéder à la fenêtre de réglage de l'export : 
![Shotcut où trouver la fenêtre Export](https://github.com/lucienbill/montage-video/blob/master/images/shotcut_ouTrouverExport.PNG)

Elle ressemble à ceci :
![](https://github.com/lucienbill/montage-video/blob/master/images/shotcut_MenuExport.PNG)
Sur la partie gauche, on voit des "presets", qui sont des pré-réglages. Ils ne correspondent pas tout à fait à ce que l'on veut faire ici, nous utiliserons donc nos propres presets (qui seront stockés dans "Custom").

Sur la partie droite, on voit :
* un texte et une case à cocher qui parle de "hardware encoder" : on ignore ça. Le "hardware encoder", c'est la carte graphique, c'est parfois compliqué à configurer sur shotcut, et globalement ça encode plus vite mais avec une moins bonne qualité que le processeur (alias "encodeur logiciel"). Si vous avez le temps, expérimentez, sinon oubliez.
* le bouton "Export file", qui sert à exporter le fichier (ça y est, vous êtes bilingue)
* Le bouton "Advanced", qui va nous permettre d'afficher les réglages avancées.

En cliquant sur "Advanced", on accède à de nouveaux onglets :

**Video**
![](https://github.com/lucienbill/montage-video/blob/master/images/shotcut_ExportAdvanced_Video.PNG)
Selon ce qu'on veut faire, on touchera à Resolution et Frames/sec.
Pour le reste, je recommande de rester sur :
* Aspect ratio = on ne touche pas (sauf rares cas)
* Scan mode = Progressive
* Deinterlacer = YADIF - temporal + spatial (best)
* Interpolation = Bicubic ; *"Lanczos" est mieux noté : il gère mieux quand on agrandit une image... mais quand on la rétrécit (exemple : on a une vidéo en 1080p, on l'exporte en 720p), "Bicubic" semble mieux s'en sortir.*
* Parallel processing : activé
**Codec**
![](https://github.com/lucienbill/montage-video/blob/master/images/shotcut_ExportAdvanced_Codec.PNG)
C'est ici qu'on dit "on choisit l'encordeur libx264, qui encodre en h264".
* Tous mes presets sont en "Average Bitrate", et j'indique le bitrate maximum recommandé pour la plateforme que je vise. *Note : Je peux potentiellement obtenir de meilleurs résultats en passant sur du "constant bitrate", mais je n'ai pas pris le temps de tester.*
* Je fixe le "[GOP](https://fr.wikipedia.org/wiki/Group_of_pictures)" à la moitié du framerate : si j'exporte à 30 images par secondes, mon "GOP" vaudra 15.
* J'utilise toujours 2 [B-frames](https://fr.wikipedia.org/wiki/Inter-trame)
* Par défaut "Dual pass" est désactivé. Quand j'ai vraiment un bitrate très limité et veux une belle vidéo, je l'active. En résumé très grossier : le compresseur fait 2 passes, pour essayer de tout optimiser.
**Audio**
![](https://github.com/lucienbill/montage-video/blob/master/images/shotcut_ExportAdvanced_AudioPNG)
Je laisse généralement les valeurs par défaut : 
* un "Sample rate" à 44.1 kHz, c'est bien. 48 kHz, c'est souvent mieux (mais pas toujours)
* un bitrate supérieur à 220 kb/s, c'est bien.
* le codec aac, c'est bien. Mais si vous exportez votre vidéo et que vous remarquez que le son est dégeulasse, particulièrement dans les aigus (on a l'impression que ça crache, que es aigus bavent, c'est désagréable), alors vous n'avez pas de chance : c'est un bug d'encodage. Refaites l'export, en choisissant "libmp3lame".
**Other**
![](https://github.com/lucienbill/montage-video/blob/master/images/shotcut_ExportAdvanced_Other.PNG)
C'est dans cet onglet qu'on définit la [vitesse le l'encodage](https://trac.ffmpeg.org/wiki/Encode/H.264#a2.Chooseapresetandtune). Plus on encode lentement, meilleur sera le résultat, mais plus il faudra être patient.
**Enregistrer un preset**
[](https://github.com/lucienbill/montage-video/blob/master/images/shotcut_Export_SavePreset.PNG)
N'hésitez pas à enregistrer les presets que vous utilisez souvent. C'est ce que je fais (on les voit dans "Custom")

## Youtube
Pour obtenir une bonne qualité de vidéo pour Youtube, en théorie il suffit de respecter les [guidelines officielles](https://support.google.com/youtube/answer/1722171?hl=fr).
Bien sûr en pratique, il faut faire plus que ça.
voici les réglages d'export spéciaux que j'utilise dans Shotcut :

### 720p 30FPS
Onglet Video (ça, ce n'est pas une déviation, ça illustre juste ce que "720p 30FPS" signifie):
* Resolution = 1280x720
* Frames/sec = 30
Onglet Other :
* preset=faster
Pour du 720p à 30 images/seconde, avec un débit maximum de 5Mb, on peut se permetre de compresser relativement vite.
### 720p 60FPS
Onglet Other :
* preset=faster
### 1080p 60FPS
Là, c'est compliqué. J'essaie d'abord d'encoder avec les réglages des guidelines officielles, et un "preset=fast" ou "preset=medium". Ensuite je la vérifie : la qualité est bonne.
Puis j'exporte sur Youtube... et là, Youtube à beau me dire qu'il lit en 1080p à 60FPS, c'est ultra moche.
Une vraie bouillie de pixels.

C'est "normal".
En bref, Youtube a un encodeur de bonne qualité (VP9), et un de moins bonne qualité, et tout n'est pas sytématiquement encodé en VP9 (détails [ici](https://www.reddit.com/r/youtube/comments/7cbcpm/guide_if_your_videos_are_not_popular_youtube/)).
Si votre video est massacrée par youtube, trichez : exportez en résolution 2560x1440 (bitrate=24Mb/s).
Et là, magie : Youtube utilisera le bon encodeur !

## Twitter
**\[To do\]**
Twitter est relou aussi, mais différemment. La doc officielle se contredit, la bonne info est, en bref : "utiliser le codec + bitrate le plus relou à gérer"

## Facebok
**\[To do\]**
Facebook est relou aussi : la doc dit "faites ce que vous voulez, on gère ça va être bien", et il ne faut surtout pas les écouter. Pour facebook, j'utilise exactement les mêmes réglages que pour twitter : ça marche bien la plupart du temps, mais même comme ça il m'arrive d'avoir des problèmes parce que publier des vidéos sur facebook, c'est vraiment atroce.

# Exemple de "workflow"
**\[To do\]**
2 exemples : 
* J'ai un montage 'simple' à faire. Je veux faire un best of, mais je n'ai pas d'effets 3D du futur à ajouter : juste des images et des textes : j'utilise shotcut.
* J'ai un montage de ouf à faire, avec des transitions exotiques, des fonds verts compliqués, je veux retravailler à fond les couleurs et faire des effets 3D du futur de l'espace : d'abord je dérushe avec shotcut pour ne garder que les bouts de vidéos qui m'intéressent (je peux tout exporter dans un seul fichier pour gagner du temps), puis je passe sur resolve, puis je transcode le montage final avec Shotcut.

# Quelques concepts de base
**\[To do\]**
* Plusieurs pistes vidéo = pratique (pour inscruster des bouts de vidéos, des images etc)
* Les keyframes
* Mesurer le son (vite fait)
* Mesurer le son de façon plus précise
