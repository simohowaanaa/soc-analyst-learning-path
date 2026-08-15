# Searching for IOC

## Le principe de l'onglet "Search"

Le 3e onglet de VirusTotal (après FILE et URL) sert à rechercher directement un indicateur
(IOC) — hash, IP, domaine — sans avoir besoin de le scanner soi-même. Utile quand on reçoit
un IOC pendant une investigation (transmis par un collègue, trouvé dans un rapport de threat
intel) et qu'on veut savoir s'il existe déjà des données dessus.

## Exemple 1 : rechercher un hash

En tapant un SHA256 déjà connu, on retombe sur l'analyse déjà réalisée dans le passé
(cf. [leçon 2](02-File-Analysis-with-VirusTotal.md)) — pas besoin de re-uploader le fichier.

## Exemple 2 : rechercher une IP

Même logique pour une IP (ex : `70.121.172.89`) → réputation immédiate (ex : 7/94
fournisseurs la classent malveillante).

## Le lien avec l'onglet "Relations" — dans les deux sens

En leçon 2, scanner un fichier révèle les IP avec lesquelles il communique (onglet
Relations). Ici, c'est l'inverse : en recherchant une IP, l'onglet Relations montre les
fichiers qui communiquent avec elle. Exemple : une IP étudiée liée à des fichiers comme
`SplitPath` et `TestMfc`, avec leurs scores de détection respectifs.

## Question de la leçon

First Submission du MD5 `b92021ca10aed3046fc3be5ac1c2a094` → **2019-09-16**

## Point clé

L'onglet Search transforme VirusTotal en véritable base de données croisée d'IOCs — on peut
partir de n'importe quel type d'indicateur (fichier, IP, URL) et remonter vers tous les
autres éléments liés, dans n'importe quel sens de la relation.
