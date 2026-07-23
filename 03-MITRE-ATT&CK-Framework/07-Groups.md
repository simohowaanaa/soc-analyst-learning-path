# Groups

## Qu'est-ce qu'un groupe APT ?

Les groupes APT (Advanced Persistent Threat) sont des groupes de hackers — parfois soutenus
par des gouvernements — qui mènent des cyberattaques de façon ciblée et systématique. Leurs
motivations varient : mission spécifique, appât du gain, ou objectifs géopolitiques/nationaux
au service d'un État.

## Ce que MITRE ATT&CK documente sur eux

Le framework collecte des infos permettant d'identifier quel groupe APT cible quels systèmes
et quelles techniques il utilise. En croisant ces infos avec la matrice, on peut reconstituer
la cartographie d'attaque (attack map) propre à chaque groupe.

**135 groupes** recensés (chiffre au moment du cours) → https://attack.mitre.org/groups/

## Structure d'une fiche groupe (ex : Lazarus Group, ID G0032)

- ID unique, nom, description
- **Associated Groups** (alias/autres noms utilisés pour désigner le même groupe ou des
  sous-groupes proches)
- **Techniques Used** — tableau détaillant, pour chaque technique employée, comment le
  groupe l'a utilisée concrètement (ex : Lazarus Group a utilisé `CreateProcessAsUserA` pour
  exécuter son keylogger KiloAlfa via la technique *Access Token Manipulation*)
- **Software** — les outils/malwares associés au groupe, chacun avec ses propres techniques

## Questions de la leçon (vérifiées sur attack.mitre.org)

- Logiciel du groupe **OilRig** associé uniquement à la technique "System Information
  Discovery" → **Systeminfo** (S0096)
- Groupe APT dont les "Associated Groups" incluent GOLD NIAGARA, ITG14 et Carbon Spider →
  **FIN7**

## Point clé

La section "Groups" transforme le framework théorique en renseignement exploitable (Threat
Intelligence) — identifier des techniques/outils correspondant à un groupe connu lors d'une
investigation permet d'anticiper la suite probable de l'attaque en se basant sur son
historique documenté.
