# File Analysis with VirusTotal

## Point de départ

Face à un fichier suspect repéré via une alerte SIEM/EDR, on l'upload sur VirusTotal pour
voir si les moteurs antivirus le détectent comme malveillant.

⚠️ **Attention avant d'uploader** : les fichiers uploadés peuvent être téléchargés par les
utilisateurs VirusTotal premium. Si le fichier contient des informations sensibles (données
internes de l'entreprise, PII...), ne pas l'uploader sur VirusTotal.

## Les onglets d'un rapport VirusTotal

**1. Detection** — score global (ex : `42/58` moteurs détectent le fichier comme
malveillant) + le libellé donné par chaque éditeur antivirus. Les tags (`macro`,
`obfuscated`, `hide-app`...) donnent une classification rapide du comportement du fichier.

**2. Details** — infos de base : hash (MD5, SHA-1, SHA-256), type de fichier, et le champ
"History" avec les dates de première et dernière soumission.
→ Point clé : si un fichier a déjà été analysé avant soi, ça suggère (pas une certitude)
que le malware n'a pas été écrit spécifiquement pour son organisation — il a probablement
déjà touché d'autres cibles.

**3. Relations** — domaines/IP/URLs/autres fichiers avec lesquels le fichier suspect
communique, scannés eux aussi par VirusTotal.
⚠️ Limite : les malwares modernes n'ont pas toujours le même comportement partout — ils
peuvent varier leurs actions selon l'environnement pour échapper à la détection. La liste
de "Relations" peut donc être incomplète.

**4. Behavior** — actions concrètes effectuées par le fichier (connexions réseau, requêtes
DNS, lecture/suppression de fichiers, actions registre, activité de processus), selon
différents moteurs d'analyse comportementale (ex : Lastline).
⚠️ Piège : si le serveur C2 du malware n'est plus actif au moment de l'analyse, le malware
peut ne pas s'activer du tout → analyse statique/dynamique sans résultat clair. Il faut
alors chercher d'anciens rapports d'analyse (faits quand le C2 était encore actif).

**5. Community** — commentaires de la communauté (règles YARA, analyses Joe Sandbox
partagées...). Souvent des infos précieuses sur comment le fichier a été obtenu.

## Questions de la leçon (confirmées correctes sur la plateforme, 100%)

- Date de création du fichier (onglet Details) → **2020-08-20**
  (la capture partielle laissait penser au 19, mais la vraie date affichée sur VT est le 20)
- Nombre d'URLs contactées (onglet Relations) → **14**
  (la table "Contacted URLs" affichée n'en montrait que 5, la liste complète en contient 14
  — bon rappel que les captures partielles peuvent tronquer l'info)
- Compilation Timestamp (autre hash `6c745b8c...`) → **2022-07-17 22:57:46 UTC**

## Point clé

Un rapport VirusTotal ne se résume pas au score `X/58` — les onglets History, Relations,
Behavior et Community apportent chacun un angle d'analyse différent, et les résultats
peuvent être incomplets (comportement variable du malware, C2 inactif...).
