# Log Storage

## L'erreur classique à éviter

Beaucoup se concentrent uniquement sur la taille du stockage. Mais un stockage énorme et
lent est un piège : si une recherche dans les logs (WAF, Firewall, Proxy...) prend 15
minutes, le travail de l'analyste devient très peu productif. La vitesse d'accès aux données
compte autant que la capacité.

## Pourquoi les bases de données classiques (type MySQL) ne sont pas idéales

Ces technologies sont optimisées pour ajouter, modifier, supprimer des données
régulièrement. Pour un SIEM, l'objectif est différent : indexer les logs pour les retrouver
vite, pas les modifier après coup. D'où l'intérêt des technologies basées **WORM** (Write
Once Read Many) — on écrit une fois, on lit de nombreuses fois, sans jamais avoir besoin
d'éditer.

## Démonstration

Deux zones de stockage comparées via un bouton "Search" — la technologie classique est
lente, la technologie adaptée (type WORM/indexée) répond instantanément. De légers délais
sont acceptables lors d'une investigation ou du traitement de nouvelles données entrantes,
mais des délais excessifs deviennent risqués.

## Questions de la leçon

- La mise à jour des données (modifier/supprimer des valeurs) est-elle très importante pour
  le stockage SIEM ? → **N** (le principe WORM privilégie l'écriture unique et la lecture
  rapide, pas la modification)
- Critère le plus important pour le stockage SIEM → **Speed**

## Point clé

Un SIEM n'est pas une base de données transactionnelle classique — c'est un système
optimisé pour la lecture rapide de données historiques immuables, ce qui justifie une
architecture de stockage différente (WORM / indexée) de celle d'une appli métier classique.
