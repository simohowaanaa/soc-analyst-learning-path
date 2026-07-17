# Matrix

## Qu'est-ce que la Matrix MITRE ATT&CK ?

Méthode de visualisation utilisée pour classer et voir les méthodes d'attaque des
cybercriminels. MITRE a créé ces matrices pour visualiser en détail le comportement des
attaquants (tactiques en colonnes, techniques en dessous).

## 3 types de matrices (selon le type de plateforme ciblée)

1. **Enterprise Matrix** — la première créée par MITRE, la plus riche en informations
   (systèmes numériques les plus courants en entreprise). Utilisée pour comprendre les
   cyberattaques contre les grandes organisations. 7 sous-matrices : PRE, Windows, macOS,
   Linux, Cloud, Network, Containers.
   → https://attack.mitre.org/matrices/enterprise/
2. **Mobile Matrix** — dédiée aux appareils mobiles, moins d'informations que l'Enterprise
   Matrix. 2 sous-matrices : Android, iOS.
   → https://attack.mitre.org/matrices/mobile/
3. **ICS Matrix** — dédiée aux systèmes de contrôle industriel (Industrial Control Systems).
   → https://attack.mitre.org/matrices/ics/

## Questions de la leçon

- Comment appelle-t-on les images représentant tactiques et techniques dans MITRE ATT&CK ?
  → **Matrix / Matrices**
- Quelle matrice couvre Windows, Linux, macOS, Azure AD et Office 365 ?
  → **Enterprise Matrix**
- Quelle matrice couvre Android et iOS ?
  → **Mobile Matrix**

## Point clé

Dans une matrice, les colonnes = **Tactics** (l'objectif de l'attaquant, ex : Initial Access,
Persistence...) et les cases sous chaque colonne = **Techniques** (le moyen concret utilisé).
Les deux prochaines leçons détaillent chacun de ces deux niveaux.
