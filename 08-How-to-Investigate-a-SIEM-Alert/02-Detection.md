# Detection

## Qu'est-ce qu'une alerte SIEM ?

Notification générée par le SIEM sur la base de règles prédéfinies et d'algorithmes de
corrélation, personnalisés selon les besoins de sécurité de l'organisation. Quand un
événement correspond aux critères définis, une alerte se déclenche. Sur LetsDefend, ces
règles sont préparées et mises à jour en continu par des experts, couvrant des attaques
courantes jusqu'aux exploits zero-day.

## La page "Monitoring" — 3 sections

**1) Main Channel** — vue par défaut, liste tous les incidents ouverts disponibles à
prendre. Champs affichés :
- Severity (Low / Medium / High / Critical)
- Date (fuseau UTC+0)
- Rule Name (règle déclenchée)
- EventID (identifiant unique)
- Type (type d'alerte)
- Action → c'est ici qu'on prend possession de l'alerte

Filtrage possible par Severity, Type et Role via le bouton "Filter".

**2) Take Ownership** — en cliquant sur une alerte puis "Take ownership", elle est
assignée. Elle part automatiquement vers l'Investigation Channel.

**3) Investigation Channel** — gestion des alertes actives assignées. Possibilité d'y créer
un cas ("Create Case") pour l'analyser en détail → ouvre la page Case Management, avec le
bouton "Start Playbook!".

## Les Playbooks

Workflow d'instructions préétabli guidant l'analyste selon le type d'alerte (web attack,
ransomware, malware, phishing...). Chaque type d'alerte a sa propre logique d'investigation.

Exemple pour "Phishing Mail Detected - Excel 4.0 Macros" : "Check If Mail Delivered to
User?", "Analyze Url/Attachment" (outils suggérés : AnyRun, VirusTotal, URLHouse, URLScan,
HybridAnalysis), "Check If Someone Opened the Malicious File/URL?"...

**Pourquoi les playbooks sont importants** : un analyste ne connaît pas toujours par cœur
toutes les étapes pour chaque type d'alerte — le playbook donne un processus clair,
étape par étape, particulièrement utile pour les analystes débutants.

## Clôturer l'alerte

Une fois le playbook terminé, retour dans l'Investigation Channel de la page Monitoring pour
fermer officiellement l'alerte, en la classant :
- **True Positive** — l'alerte est légitime, nécessite une action
- **False Positive** — fausse alerte

Documenter ses conclusions dans le champ "Analyst Note" (raisonnement, données observées,
étapes suivies) — historique exploitable plus tard.

Une fois fermée, l'alerte apparaît dans **Closed Alerts**, avec les réponses données au
playbook, l'Analyst Note, et parfois un rapport officiel d'incident ou un community
walkthrough pour du contexte supplémentaire.

## Questions de la leçon

- Dans quel canal peut-on prendre possession d'une alerte ? → **Main Channel**
- Une fois l'analyse terminée, dans quel canal peut-on fermer l'alerte ? →
  **Investigation Channel**

## Point clé

Le parcours d'une alerte suit toujours ce flux : Main Channel (repérage) → Take Ownership →
Investigation Channel (analyse + fermeture) → Closed Alerts (archivage). Ce cycle est la
colonne vertébrale du travail quotidien d'un analyste SOC.
