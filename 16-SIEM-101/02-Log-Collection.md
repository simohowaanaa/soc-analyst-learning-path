# Log Collection

## Pourquoi c'est fondamental

Sans logs, un SIEM ne sert à rien — c'est la matière première de toute détection. La
collecte est l'une des étapes les plus critiques de l'architecture SIEM.

## Qu'est-ce qu'un log ?

Un fichier qui enregistre des événements d'un système/logiciel, ou des messages entre
utilisateurs. Structure basique : timestamp, système source, message. Exemple :
`/var/log/auth.log` sur Ubuntu montre les sessions CRON ouvertes/fermées avec horodatage.

## L'objectif de la collecte

Transférer les logs de toutes les sources (hosts, firewall, serveurs, proxy...) vers le
SIEM, pour tout traiter et détecter les menaces depuis un point central.

## 2 méthodes de collecte

### 1) Log Agents (via un logiciel agent)

Logiciel installé sur la source qui peut parser, faire tourner (rotation) les logs, mettre
en buffer, chiffrer, convertir avant l'envoi. Exemple : un agent peut découper un log
`"username: LetsDefend; account: Administrator"` en 2 messages distincts avant transmission.

- Avantages : logiciel testé/éprouvé, fonctionnalités riches (parsing auto, chiffrement,
  intégrité des logs...)
- Inconvénients : plus de fonctionnalités = plus de consommation de ressources (CPU/RAM) →
  coût plus élevé

**Syslog** — protocole populaire pour le transfert de logs :
- Fonctionne en UDP ou TCP, chiffrable en option via TLS
- Supporté nativement par : switch, routeur, IDS, firewall, Linux, Mac (Windows nécessite un
  logiciel additionnel)
- Format : `Timestamp - Source Device - Facility - Severity - Message Number - Message Text`
- Limite de taille de paquet : 1024 octets en UDP, 4096 octets en TCP

**Agents tiers** — chaque produit SIEM a souvent son propre agent, plus riche que syslog :
- Splunk → agent = **Universal Forwarder**
- ArcSight → agent = ArcSight Connectors
- Agents open source populaires : Beats (Elastic), NXLog

### 2) Agentless (sans agent)

Pas d'installation ni de maintenance logicielle — connexion directe à la cible via SSH ou
WMI.
- Avantage : plus simple à préparer et gérer qu'un agent
- Inconvénients : capacités limitées, et les identifiants (username/password) circulent sur
  le réseau → risque de vol de credentials

### 3) Collecte manuelle (Manual Collection)

Pour les cas où aucun agent existant ne suffit (ex : logs d'une appli cloud non compatible)
→ il faut écrire son propre script.

## Questions de la leçon

- Meilleure méthode pour ceux qui ne veulent pas gérer de logiciel agent → **Agentless**
- Produit dont l'agent s'appelle "Universal Forwarder" → **Splunk**

## Point clé

Le choix Agent vs Agentless est un compromis entre richesse fonctionnelle (parsing,
chiffrement) et simplicité/coût de gestion — une organisation combine souvent les 3 méthodes
selon les sources à couvrir.
