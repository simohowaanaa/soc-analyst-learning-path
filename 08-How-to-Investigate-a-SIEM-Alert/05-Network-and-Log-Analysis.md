# Network and Log Analysis

## Objectif

Apres avoir confirme que l'email de phishing a ete delivre (lecon 4), il faut determiner si
l'utilisateur a ouvert le fichier/URL malveillant. Pour cela, on analyse les **logs reseau**
afin de detecter toute connexion suspecte, notamment vers un serveur C2 (Command & Control).

## Etape 1 — Trouver l'IP de la machine affectee

Avant de fouiller les logs, il faut connaitre l'IP de la machine cible.

- Aller dans **Endpoint Security** (menu lateral)
- Chercher le hostname (ici "Felix") dans la barre de recherche
- Relever l'adresse IP dans la section "Host Information"

## Etape 2 — Rechercher dans Log Management

- Aller dans **Log Management** (menu lateral)
- Passer en mode **Basic** (bouton en haut a droite)
- Rechercher l'adresse IP de la machine dans la barre de recherche
- Analyser les colonnes :
  - **SRC ADDRESS** : d'ou part la connexion
  - **DEST ADDRESS** : ou elle va
  - **DEST PORT** : le port utilise (un port inhabituel = suspect)

## Etape 3 — Identifier les connexions suspectes

Ce qu'on cherche : des connexions **sortantes** de la machine vers des IPs inconnues,
surtout sur des **ports non standard** (ni 80/HTTP ni 443/HTTPS). Les malwares utilisent
des ports inhabituels pour communiquer avec leur C2 et eviter la detection.

- Cliquer sur **Raw Data** (icone loupe) pour voir les details : URL, processus, timestamp
- Les logs **Proxy** montrent les telechargements web (URL complete, processus)
- Les logs **Firewall** montrent les connexions reseau brutes (IP, port)

## Etape 4 — Verifier avec Threat Intel

Une fois une IP suspecte identifiee :

- Aller dans l'onglet **Threat Intel** (menu lateral)
- Rechercher l'IP pour verifier si elle est connue comme malveillante
- Cet outil agregue les donnees de plusieurs sources de threat intelligence

Meme principe que VirusTotal ([section 20](../20-VirusTotal-for-SOC-Analysts/README.md))
mais integre directement dans LetsDefend.

## Repondre au playbook

Selon les resultats :
- Connexions suspectes confirmees → cliquer **"Opened"** dans le playbook
- Rien de suspect → cliquer **"Not Opened"**

## Questions de la lecon (EventID: 257)

- IP address of Felix host → **172.16.20.151** (via Endpoint Security)
- When did Felix download the malicious file → **May, 13, 2024, 12:59 PM**
  (log Proxy : telechargement de `free-coffee.zip` via chrome.exe depuis un bucket S3)
- C2 address → **37.120.233.226** (connexions Firewall sur port non standard)
- Process that communicated with C2 → **coffee.exe** (visible dans le Raw Data Firewall)
- Port used by malware → **3451** (port non standard, confirme dans les logs Firewall)

## Point cle

La logique de cette etape : email delivre → est-ce que le fichier a ete ouvert ? → on
cherche dans les logs reseau → si on trouve des connexions C2, c'est que le malware a ete
execute. Log Management donne la **vision reseau** ; la prochaine lecon (Endpoint Analysis)
donnera la **vision endpoint** pour confirmer exactement ce qui s'est passe sur la machine.
