# Software

## Qu'est-ce que "Software" dans MITRE ATT&CK ?

Ce sont les programmes/outils (malwares, RATs, backdoors...) utilisés par les groupes APT
pour mener leurs attaques. C'est le dernier maillon de la chaîne : après avoir vu qui
(Groups) utilise quoi (Techniques) pourquoi (Tactics), "Software" détaille précisément avec
quel outil concret.

## Structure d'une fiche logiciel

- ID unique (ex : S0066), nom, description
- Type (ex : MALWARE)
- Platforms (ex : Windows, macOS, Android...)
- Techniques Used — les techniques précises que ce logiciel met en œuvre (ex : 3PARA RAT
  utilise T1071.001 pour son C2 via HTTP, et chiffre ses communications en DES via T1573.001)
- Le ou les groupe(s) APT qui l'utilisent

**718 logiciels** recensés (chiffre au moment du cours) → https://attack.mitre.org/software/

## Questions de la leçon (vérifiées sur attack.mitre.org)

- Plateforme visée par **Cryptoistic** (utilisé par Lazarus Group) → **macOS**
- Type du logiciel **Rotexy** (Android) → **MALWARE**
- Groupe APT utilisant **PUNCHBUGGY** (cible les réseaux POS/point de vente, secteur
  hôtelier) → **FIN8**

## Point clé

Cette leçon boucle la chaîne complète du framework : Tactic (pourquoi) → Technique
(comment) → Mitigation (comment se défendre) → Group (qui) → Software (avec quel outil
précis). C'est cette chaîne complète qui permet à un analyste de transformer une observation
technique isolée (ex : un hash de malware) en une attribution potentielle et une
anticipation de la suite de l'attaque.
