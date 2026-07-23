# Techniques and Sub-Techniques

## Qu'est-ce qu'une Technique / Sub-Technique ?

Les tactiques montrent seulement ce que vise l'attaquant (le pourquoi), sans détailler
comment il s'y prend. Les techniques et sub-techniques montrent la méthode concrète utilisée
pour atteindre l'objectif de la tactique. Chaque technique est rattachée à une tactique
précise dans la matrice.

## Comment repérer les sub-techniques

Dans la matrice, une zone grise à côté du nom d'une technique indique qu'elle a des
sub-techniques (version plus précise/détaillée de la technique). Ex : sous la tactique
"Reconnaissance", la technique "Active Scanning" a 3 sub-techniques : Scanning IP Blocks,
Vulnerability Scanning, Wordlist Scanning.

## Volume par matrice (chiffres au 10/05/2023, en constante évolution)

| Matrice | Techniques | Sub-techniques |
|---|---|---|
| Enterprise | 193 | 401 |
| Mobile | 66 | 41 |
| ICS | 79 | 0 |

Liens : https://attack.mitre.org/techniques/enterprise/ ·
https://attack.mitre.org/techniques/mobile/ · https://attack.mitre.org/techniques/ics/

## Qu'est-ce qu'une Procedure ?

Une Procedure = un exemple concret d'utilisation d'une technique/sub-technique dans la vraie
vie — quel outil/logiciel/groupe l'a utilisée. Ex : le groupe APT39 a utilisé différentes
versions de Mimikatz pour la technique "OS Credential Dumping".

## Questions de la leçon (100% — confirmées correctes sur LetsDefend et sur attack.mitre.org)

- Technique **T1055** → **Process Injection**
- Technique **T1112** (Enterprise) → plateforme : **Windows** (technique = *Modify Registry*)
- Tactique de la technique "Supply Chain Compromise" → **Initial Access**

## Point clé

Hiérarchie complète du framework : **Tactic → Technique → Sub-Technique → Procedure**. Plus
on descend, plus c'est concret : la tactique dit pourquoi, la technique dit comment en
général, la sub-technique dit comment précisément, et la procedure dit qui l'a fait, avec
quel outil, dans la vraie vie.
