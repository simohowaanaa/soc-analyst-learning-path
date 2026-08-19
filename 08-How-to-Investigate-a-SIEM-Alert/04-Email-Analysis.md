# Email Analysis

## Où chercher l'email — l'onglet "Email Security"

Outil du menu latéral dédié aux emails, avec une recherche détaillée par : Sender,
Recipient, Subject, Sender IP Address, Attachment Name, Email Body, Date, Action.

## Examiner le contenu de l'email

En cliquant sur l'email trouvé, on répond aux 2 dernières questions de l'étape 1 du
playbook ("Parse Email", [leçon 3](03-Case-Creation-and-Playbook-Initiation.md)) :
- Le contenu est-il suspect ?
- Y a-t-il des pièces jointes ?

## Étape suivante du playbook : pièces jointes / URLs

Vérifier en bas de l'email pour les fichiers attachés, et dans le corps du texte pour des
hyperliens (potentiellement malveillants).

## Analyser URLs/Pièces jointes — via sandbox tiers

Ne jamais tester un fichier/lien suspect sur sa propre machine — utiliser des sandboxes
tierces (rappel de la section VirusTotal + [Dynamic Analysis](../04-Phishing-Email-Analysis/06-Dynamic-Analysis.md)) :
- AnyRun, VirusTotal, URLHouse, URLScan, HybridAnalysis

⚠️ Le mot de passe des fichiers zip fournis en exercice est toujours "infected" sauf
indication contraire. Utiliser une VM pour télécharger ces pièces jointes.

Selon le résultat → cliquer "Malicious" ou "Non-malicious" dans le playbook. Alternative :
Sandbox intégré à LetsDefend (`app.letsdefend.io/sandbox`) pour une analyse statique en
sécurité.

## Étape suivante : l'email a-t-il été délivré à l'utilisateur ?

Retour à la page Alert Details (Investigation Channel), champ "Device Action" :
- "Allowed" → l'email a atteint l'utilisateur → réponse playbook : "Delivered"
- "Blocked" / "Quarantined" → intercepté → réponse playbook : "Not Delivered"

## Dernière étape : supprimer l'email malveillant

Retour dans Email Security, retrouver l'email, l'ouvrir, cliquer "Delete" en haut à droite
du panneau — pour empêcher tout dommage si l'utilisateur venait à y accéder plus tard.

## Ce qui suit

La prochaine leçon (Network and Log Analysis) vérifie si quelqu'un a accédé au
fichier/URL malveillant, et recherche des connexions vers un éventuel C2.

## Questions de la leçon (EventID: 257)

D'après les infos déjà obtenues en leçon 3 (`Device Action: Allowed`,
`E-mail Subject: Free Coffee Voucher`) :

- Sujet de l'email → **Free Coffee Voucher** (validé Correct)
- Nom de la pièce jointe → **free-coffee.zip** (validé Correct)
- Date d'envoi de l'email → **May, 13, 2024, 09:22 AM** (validé Correct)

## Point clé

Le workflow Email Analysis suit une logique stricte : examiner le contenu → analyser
pièces jointes/URLs en sandbox → vérifier la délivrance (Device Action) → supprimer l'email
si malveillant. Chaque étape correspond à une question précise du playbook.
