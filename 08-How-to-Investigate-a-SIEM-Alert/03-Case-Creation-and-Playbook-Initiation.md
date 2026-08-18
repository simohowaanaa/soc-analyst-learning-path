# Case Creation and Playbook Initiation

## Le principe de cette leçon — pratique guidée

Contrairement aux leçons précédentes, ici on suit un cas concret réel : l'alerte
`EventID: 257 - SOC282 - Phishing Alert - Deceptive Mail Detected`, du début à la fin.

## Étape 1 : Take Ownership

On prend possession de l'alerte spécifique (`EventID: 257`) pour se l'assigner.

## Étape 2 : Créer un cas

Depuis l'Investigation Channel, on sélectionne l'alerte assignée et on clique "Create a
Case" pour formaliser l'investigation (documentation, assignation, lancement du playbook).

## Étape 3 : Lancer le Playbook

Depuis Case Management, on voit les "Incident Details" puis on clique "Start Playbook".
Première étape du playbook pour ce type d'alerte : "Parse Email" — récupérer les infos clés
de l'email reçu :
- Quand a-t-il été envoyé ?
- Quelle est l'adresse SMTP de l'email ?
- Quelle est l'adresse de l'expéditeur ?
- Quelle est l'adresse du destinataire ?
- Le contenu est-il suspect ?
- Y a-t-il des pièces jointes ?

## Astuce méthodologique

Garder l'onglet du playbook ouvert en permanence sur le côté, ouvrir un nouvel onglet pour
consulter la page Alert Details (Monitoring → Investigation Channel), et noter ses
observations dans un fichier texte à part au fur et à mesure.

## Questions de la leçon (EventID: 257)

Détails réels de l'alerte (page "Alert Details", Investigation Channel) :

- Type de l'alerte → **Exchange**
- Date de génération → **May, 13, 2024, 09:22 AM**
- Adresse SMTP de l'email → **103.80.134.63**
- Adresse source → **free@coffeeshooop.com**
- Adresse destination → **Felix@letsdefend.io**

**Bonus — tags MITRE ATT&CK de l'alerte** : `T1566` (Phishing), `T1566.002` (Spearphishing
Link), `T1059` (Command and Scripting Interpreter), `T1204` (User Execution) — lien direct
avec le framework vu en [section 3](../03-MITRE-ATT&CK-Framework/README.md), qui donne déjà
une idée du déroulé probable : phishing → lien malveillant → exécution de commande →
nécessite une action de l'utilisateur.

Sujet de l'email : "Free Coffee Voucher" — appât classique type "offre gratuite" (rappel de
la mécanique psychologique vue en [section 4](../04-Phishing-Email-Analysis/01-Introduction-to-Phishing.md)).

## Point clé

Cette leçon inaugure une investigation pratique complète qui se poursuit sur les leçons
suivantes (Email Analysis, Network and Log Analysis, Endpoint Analysis, Result) — le même
EventID: 257 sera suivi de bout en bout.
