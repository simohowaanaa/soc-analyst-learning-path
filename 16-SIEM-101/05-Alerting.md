# Alerting

## Le but final de toute la chaîne

On a collecté, traité et stocké les logs — reste à détecter les comportements anormaux et
générer des alertes. La rapidité de recherche (stockage) impacte directement la rapidité des
alertes : un log d'aujourd'hui doit générer une alerte immédiatement, pas 2 jours plus tard.

## Deux façons de créer une alerte

1. En recherchant dans les données déjà stockées
2. En créant l'alarme directement à l'arrivée du log (temps réel)

Exemples : "nouvel utilisateur ajouté en administrateur global", "15 échecs de connexion en
3 minutes depuis la même IP".

## Principe important : la qualité avant la quantité

Une alerte doit être optimisée — pas déclenchée en masse, sauf cas exceptionnel. Trop
d'alertes = fatigue de l'analyste, vraies menaces noyées dans le bruit.

## 3 techniques pour créer des alertes de qualité

**1) Blacklist** — lister ce qui est interdit (ex : `mimikatz.exe`, une IP bannie). Alerte
si ça apparaît dans les logs.
- Facile à gérer et implémenter
- Très facile à contourner — renommer `mimikatz.exe` en `mimikatz2.exe` suffit à passer
  inaperçu

**2) Whitelist** — l'inverse : lister ce qui est autorisé/normal (ex : IPs de communication
légitime). Alerte si quelque chose en dehors de cette liste apparaît.
- Très efficace
- Difficile à maintenir — la liste doit être constamment mise à jour

**3) Long Tail Log Analysis** — part du principe que ce qui se produit constamment est
normal (ex : Event ID 4624 de connexion réussie, très fréquent). On se méfie plutôt des logs
les moins fréquents — les événements rares sont statistiquement les plus suspects.

## Questions de la leçon

- Deux IPs définitivement malveillantes connues → quelle méthode pour alerter à leur accès ?
  → **Blacklist** (élément précis déjà connu à interdire, cas d'usage typique)
- "La méthode whitelist est efficace ET facile à gérer" → **False** (efficace, mais
  difficile à gérer)

## Point clé

Ces 3 techniques ne s'excluent pas — un bon SIEM combine Blacklist (menaces connues),
Whitelist (environnements très contrôlés) et Long Tail Analysis (détection de l'inhabituel,
proche du threat hunting) selon le contexte.
