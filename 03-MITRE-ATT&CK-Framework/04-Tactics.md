# Tactics

## Qu'est-ce qu'une Tactic ?

Une Tactic exprime le but de l'attaquant et la raison de son action. Composant central du
framework, utilisé pour regrouper les comportements des attaquants et visualiser les étapes
de l'attaque. Les tactiques forment la rangée du haut de chaque matrice (les colonnes).

Particularité : les tactiques sont des énoncés généraux (le "pourquoi"), donc très similaires
d'une matrice à l'autre — contrairement aux techniques, très spécifiques à chaque plateforme.

## Les tactiques par matrice

**Enterprise (14 tactiques)** — https://attack.mitre.org/tactics/enterprise/
Reconnaissance, Resource Development, Initial Access, Execution, Persistence, Privilege
Escalation, Defense Evasion, Credential Access, Discovery, Lateral Movement, Collection,
Command and Control, Exfiltration, Impact.

**Mobile (14 tactiques)** — https://attack.mitre.org/tactics/mobile/
Mêmes tactiques que l'Enterprise (sans Reconnaissance/Resource Development), + 2 spécifiques
mobiles : Network Effects, Remote Service Effects.

**ICS (12 tactiques)** — https://attack.mitre.org/tactics/ics/
Structure proche, avec des tactiques spécifiques à l'industriel : Evasion (au lieu de
Defense Evasion), Inhibit Response Function, Impair Process Control.

## Questions de la leçon (vérifiées sur attack.mitre.org)

- ID de la tactique "Lateral Movement" (Enterprise) : **TA0008**
- Date de création de la tactique "Persistence" (Mobile) : **17 October 2018**
- Tactique commune aux 3 matrices pour obtenir des permissions de plus haut niveau :
  **Privilege Escalation**

## Point clé

Chaque tactique a un ID unique (format `TA00xx`) et une date de création/dernière
modification, ce qui permet de suivre l'évolution du framework dans le temps — utile pour
savoir si une technique/tactique est récente ou établie de longue date.
