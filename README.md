# montage-video
Vous souhaitez monter des best-of pour votre streameur préféré, et mettre vos montages sur YouTube ? Voici quelques infos pour bien démarrer.

Note : je ne suis pas un expert, je ne suis pas un professionnel, mais j'ai fait quelques trucs et j'ai bien galéré à trouver certaines infos. 
Je les écrits ici pour permettre à d'autres de moins perdre de temps sur tout un tas de choses techniques qui n'ont, au final, pas grand chose à voir avec le montage à proprement parler.

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
* [Shotcut](https://shotcut.org/download/) : très flexible au niveau des codec, simple mais efficace, je l'utilise presque tout le temps.
* [Da Vinci Resolve](https://www.blackmagicdesign.com/fr/products/davinciresolve/) : c'est l'artillerie lourde. Très puissant et polyvalent, mais capricieux sur les codec

Note : je recommande des les installer en anglais, parce qu'on trouve plein de tutos en anglais sur youtube.
Pour avoir essayé d'utiliser Shotcut en français : quand un tuto parle de "Rotate and scale" et que la fonctionnalité s'appelle en vrai "Mise à l'échelle et rotation", c'est pas pratique du tout.

# Les codec
C'est, en bref, la façon dont est gérée le flux vidéo.
Spécifiquement : un codec correspond à une façon de compresser la vidéo.
Une bonne compression permet d'avoir une belle vidéo qui ne prend pas trop de place sur le disque dur.
Globalement, on va surtout utiliser le "h264", qui est très commun.

## Shotcut
Shotcut se base sur la librairie "ffmpeg" qui est ultra flexible.
En bref : cette librairie sait lire et écrire dans plein de codec différents.
Concrètement, cela signifie qu'on peut donner à peu près ce qu'on veut à Shotcut, il arrivera à intérpréter les signaux, et à exporter notre montage dans le codec que l'on veut (99% du temps, h264).
J'utilise toujours Shotcut pour transcoder mon montage vers le bon codec avec les bon paramètres pour la plateforme que je vise (youtube, twitter, facebook...).

Transcoder = lire une vidéo, puis l'écrire dans un autre fichier (généralement dans un autre codec, et/ou avec un autre bitrate. Exemple : prendre un DivX en 1080p et le transformer en .mp4 h264 en 720p)

## Da Vinci Resolve
Resolve n'aime pas travailler avec des vidéos compressées.
Il m'est déjà arrivé de faire un montage à base de vidéos compressée : tout semblait bien fonctionner jusqu'à ce que j'exporte la vidéo : il y avait quelques soucis d'images bien pénibles qui n'étaient pas visible dans l'aperçu, mais dont je ne parvenais pas à me débarraser.
Autrement dit : avec Resolve, ne travaillez jamais avec des vidéos compressées !
**To do :** Expliquer comment régler ce problème. Resolve sait "transcoder" les vidéos. L'idée est : j'importe les vidéos source dans resolve, puis je vais dans le gestionnaire de média pour les transcoder. Une fois l'opération terminée, je vire mes sources, et les remplace par les fichiers transcodés. Attention : resolve transcode vers du .mov non compressé (ou très peu compressé) : les vidéos prennent énormément de place. Mieux vaut dérusher (c'est à dire : ne garder que les morceaux de vidéos qu'on va utiliser) avant de transcoder, sinon on va bouffer beaucoup trop de place sur son disque dur.

## Youtube
**\[To do\]**
outube est relou avec sa façon de gérer les vidéos, expliquer comment s'en sortir (parce qu'il y a la doc officelle de youtube... et la réalité de youtube)

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
