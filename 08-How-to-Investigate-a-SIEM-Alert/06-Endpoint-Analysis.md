# Endpoint Analysis

## Objectif

Apres avoir detecte des connexions C2 dans les logs reseau (lecon 5), on examine
directement la **machine de Felix** via l'EDR (Endpoint Security) pour confirmer l'execution
du malware et identifier les actions qu'il a effectuees.

Rappel ([section 1](../01-SOC-Fundamentals/06-EDR-Endpoint-Detection-and-Response.md)) :
- **Log Management** = vision reseau globale, consultation uniquement
- **EDR** = vision endpoint, recherche + action directe (containment)

## Navigation dans Endpoint Security

- Aller dans **Endpoint Security** (menu lateral)
- Chercher le hostname ou l'IP dans la barre de recherche
- La page affiche les infos de la machine + plusieurs onglets d'analyse

## Les 4 axes d'analyse

### 1. Processes

Liste de tous les processus qui tournent sur la machine. On cherche :
- Des processus **inconnus ou suspects** (ici : `coffee.exe`)
- Le **PID** (Process ID) — identifiant unique du processus
- Le **hash** — empreinte du fichier, a verifier sur Threat Intel / VirusTotal
- L'arbre **parent/enfant** : quel processus a lance quoi
  (ex : `coffee.exe` → lance `cmd.exe` → lance d'autres commandes)

### 2. Network Actions

Les connexions reseau faites par chaque processus. Complete les logs de Log Management
en associant chaque connexion au processus qui l'a initiee.

### 3. Terminal History

Les commandes executees dans le terminal (cmd/PowerShell). Si le malware a execute des
commandes, elles apparaissent ici — correspond a la technique MITRE
[T1059 (Command and Scripting Interpreter)](../03-MITRE-ATT&CK-Framework/05-Techniques-and-Sub-Techniques.md)
taguee sur notre alerte.

### 4. Browser History

L'historique de navigation — pour voir si l'utilisateur a clique sur un lien malveillant,
quand, et quel fichier a ete telecharge.

## Containment

Une fois la compromission confirmee, on peut **isoler la machine du reseau** directement
depuis Endpoint Security (bouton Containment). C'est le gros avantage de l'EDR : on peut
**agir** (isoler, investiguer en live), pas juste observer comme avec Log Management.

Pourquoi isoler :
- Empecher la perte de donnees
- Bloquer les acces non autorises
- Empecher le mouvement lateral (propagation a d'autres machines)
- Empecher l'exfiltration de donnees

## Questions de la lecon (EventID: 257)

- PID of coffee.exe → **6697**
- Image hash of the malicious process → **CD903AD2211CF7D166646D75E57FB866000F4A3B870B5EC759929BE2**
- Child processes of cmd.exe → **7**

## Point cle

L'Endpoint Analysis est le complement indispensable du Network Analysis : les logs reseau
montrent les connexions, l'EDR montre les processus responsables. Ensemble, ils permettent
de reconstituer toute la chaine d'attaque : telechargement du fichier (chrome.exe) →
execution du malware (coffee.exe, PID 6697) → communication C2 (37.120.233.226:3451) →
commandes executees (cmd.exe avec 7 sous-processus). La prochaine etape est de conclure
l'investigation et fermer l'alerte.
