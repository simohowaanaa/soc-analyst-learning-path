# Mitigations

## Qu'est-ce qu'une Mitigation ?

Les Mitigations sont les mesures et actions qu'on peut mettre en place en réponse aux
techniques listées dans la matrice MITRE ATT&CK. Chaque mitigation a un ID unique, un nom et
une description claire. C'est la partie du framework qui répond à : "comment on se défend
contre cette technique précise ?"

## 3 types de mitigations

| Matrice | Nombre de mitigations |
|---|---|
| Enterprise | 43 |
| Mobile | 11 |
| ICS | 51 |

Liens : https://attack.mitre.org/mitigations/enterprise/ ·
https://attack.mitre.org/mitigations/mobile/ · https://attack.mitre.org/mitigations/ics/

## Lien direct avec les Techniques

Chaque page de mitigation liste aussi les "Techniques Addressed by Mitigation" — pour une
mesure de défense donnée, quelles techniques précises (avec ID, ex : T1557) elle permet de
contrer, et comment l'appliquer concrètement (ex : *Filter Network Traffic* (M1037) bloque
le trafic réseau inutile pour contrer l'Adversary-in-the-Middle).

## Questions de la leçon (vérifiées sur attack.mitre.org)

- Mitigation **M1032** (Enterprise) → **Multi-factor Authentication**
- Mitigation Enterprise recommandant la vérification de signature numérique pour empêcher
  l'exécution de code non fiable → **Code Signing (M1045)**

## Point clé

Avec cette leçon, la chaîne devient : **Tactic → Technique/Sub-Technique → Mitigation** — le
pourquoi, le comment de l'attaquant, et le comment se défendre. Il reste "qui" (les groupes)
et "avec quoi" (les logiciels), couverts dans les 2 prochaines leçons.
