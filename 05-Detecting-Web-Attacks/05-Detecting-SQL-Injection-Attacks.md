# Detecting SQL Injection Attacks

## Qu'est-ce que le SQL Injection (SQLi) ?

Vulnérabilité critique où une application web insère des données utilisateur non filtrées
directement dans une requête SQL. Les frameworks modernes ont des protections intégrées,
mais le SQLi persiste quand des requêtes SQL brutes sont utilisées, le framework a une
faille inhérente, ou il est mal utilisé.

## 3 types de SQL Injection

1. **In-band SQLi (Classic SQLi)** — requête et réponse passent par le même canal. Le plus
   facile à exploiter.
2. **Inferential SQLi (Blind SQLi)** — la réponse n'est pas visible directement ; l'attaquant
   déduit le résultat via le comportement de l'application (vrai/faux...).
3. **Out-of-band SQLi** — la réponse arrive par un autre canal que la requête (ex : via
   requêtes DNS).

## Comment ça fonctionne — exemple du login

```sql
SELECT * FROM users WHERE username = 'USERNAME' AND password = 'USER_PASSWORD'
```

Payload `' OR 1=1 -- -` dans le champ username →

```sql
SELECT * FROM users WHERE username = '' OR 1=1 -- - AND password = 'supersecretpassword'
```

`-- -` commente le reste de la requête. `1=1` est toujours vrai → la condition devient
toujours vraie → connexion sans mot de passe, généralement sur le premier compte de la base.

## Ce qu'un attaquant peut obtenir via SQLi

- Contournement d'authentification
- Exécution de commandes (ex : via `xp_cmdshell`)
- Exfiltration de données sensibles
- Création/suppression/modification d'entrées en base

## Comment prévenir le SQLi

- Utiliser un framework (pas suffisant seul — il faut le suivre correctement)
- Maintenir le framework à jour
- Toujours assainir les données utilisateur (formulaires, headers, URL...)
- Éviter les requêtes SQL brutes

## Comment détecter le SQLi (côté analyste)

- Vérifier toutes les zones venant de l'utilisateur (pas que les formulaires — aussi le
  header `User-Agent`)
- Chercher des mots-clés SQL : `INSERT`, `SELECT`, `WHERE`...
- Chercher des caractères spéciaux : apostrophes, tirets, parenthèses
- Se familiariser avec les payloads SQLi courants
  ([liste de référence](https://github.com/payloadbox/sql-injection-payload-list))

## Détecter les outils automatisés (ex : Sqlmap)

1. Regarder le User-Agent (les outils s'identifient souvent eux-mêmes)
2. Vérifier la fréquence des requêtes — un humain ≈ 1 req/sec, un outil automatisé beaucoup plus
3. Regarder le contenu du payload (ex : `sqlmap' OR 1=1`)
4. La complexité du payload — souvent plus complexe pour un outil qu'un humain en phase initiale

## Analyse pas à pas de l'exemple de log fourni

1. Repérer l'anomalie : requêtes normales (`id=1`, `id=9167`) suivies de requêtes complexes
   truffées de `%XX` (percent-encoding des caractères spéciaux).
2. Décoder l'URL (décodeur en ligne — jamais avec de vraies données sensibles en pro) → on
   voit `UNION`, `SELECT`, `AND`, `CHR`, `EXTRACTVALUE`... = confirmation SQLi.
3. Analyser le timing : toutes les requêtes malveillantes horodatées **19/Feb/2022 11:09:24**,
   plus de 50 requêtes en 1 seconde → attaque automatisée (renforcé par la complexité
   des payloads dès le début, typique d'un outil).
4. Déterminer le succès : normalement via la taille de réponse — variation anormale = attaque
   probablement réussie. Dans cet exemple, pas d'info de taille de réponse dans les logs →
   impossible de conclure → à escalader vers un analyste senior dans un cas réel.

**Synthèse type** : attaque SQLi sur le paramètre `id`, depuis l'IP `192.168.31.174`,
automatisée (>50 req/s, payloads complexes), succès indéterminable faute d'info sur la
taille de réponse.

## Questions du labo (SQL_Injection_Web_Attacks.rar)

D'après l'exemple de log illustré dans la leçon (à confirmer avec le fichier réel du labo) :

- Date de début de la phase d'exploitation → **19/Feb/2022:11:09:24**
- IP de l'attaquant → **192.168.31.174**
- Succès de l'attaque (Y/N) → non déterminable sur cet exemple (pas d'info de taille de
  réponse) — à vérifier dans le fichier réel du labo
- Type de SQLi → mélange de boolean-based blind (`AND X=Y`) et error-based (`EXTRACTVALUE`)
  visible dans l'échantillon — majoritairement **Blind** — à confirmer avec le fichier réel

## Point clé

Le SQLi automatisé se repère à la conjonction de 3 signaux : mots-clés/caractères SQL dans
les paramètres, fréquence de requêtes anormalement élevée, et complexité des payloads dès
les premières tentatives.
