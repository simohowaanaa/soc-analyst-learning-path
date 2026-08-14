# How Web Applications Work

## Où se situe HTTP dans les modèles réseau

HTTP se trouve à la couche 7 (Application) du modèle OSI. Avant qu'une requête HTTP puisse
voyager, elle passe par plusieurs couches inférieures :
- Ethernet (couche Liaison de données / Network Interface en TCP/IP)
- IP (couche Réseau)
- TCP (couche Transport)
- puis HTTP (couche Application, correspond à Application + Presentation + Session en OSI)

## Principe de base de la communication HTTP

Client ↔ Serveur : le client demande une ressource précise, le serveur répond en la
fournissant. Tout écart au format HTTP standard peut générer une erreur, ou être exploité
comme vecteur d'attaque (ex : déni de service).

## HTTP Request — structure complète

Une requête HTTP a 3 parties : Request Line, Request Headers, Request Message Body.

```
GET / HTTP/1.1                                          ← Request Line
Host: letsdefend.io
Cookie: example=hello
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) Chrome/97.0.4692.71
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Connection: close                                       ← Request Headers

parameter1=value1&parameter2=value2                      ← Request Message Body
```

| Élément | Détail |
|---|---|
| Request Line (`GET / HTTP/1.1`) | Méthode HTTP + ressource demandée. `/` seul = page principale du serveur. |
| Host | Identifie à quel domaine appartient la ressource demandée (utile quand plusieurs domaines partagent un même serveur web). |
| Cookie | Stocke des infos côté client, typiquement les infos de session — évite de resaisir identifiant/mot de passe à chaque visite. |
| Upgrade-Insecure-Requests | Indique que le client souhaite communiquer en chiffré (SSL/TLS). |
| User-Agent | Infos sur le navigateur et l'OS du client. Le serveur adapte sa réponse selon ce header. Utile pour repérer des scanners de vulnérabilités automatisés. |
| Accept | Type de données que le client souhaite recevoir. |
| Accept-Encoding | Algorithmes de compression acceptés par le client (ex : gzip). |
| Accept-Language | Langue préférée du client — le serveur adapte le contenu affiché. |
| Connection | `close` = connexion TCP fermée après la réponse ; `keep-alive` = connexion maintenue. |
| *(ligne vide)* | Sépare les headers du corps du message. |
| Request Message Body | Données envoyées au serveur — ex : paramètres d'une requête POST. |

## HTTP Response — structure complète

Une réponse HTTP a 3 parties : Status Line, Response Headers, Response Body.

```
HTTP/1.1 200 OK                                          ← Status Line
Date: Thu, 10 Feb 2022 21:46 GMT
Connection: close
Server: Nginx/1.1
Last-Modified: Tue, 8 Feb 2022 09:34 GMT
Content-Type: text/html
Content-Length: 170                                      ← Response Headers

<html>...<title>Welcome to LetsDefend</title>...</html>  ← Response Body
```

**Status Line** — version HTTP + code de statut, catégorisé par plage :
- 100-199 : réponses informatives
- 200-299 : réponses de succès (ex : `200 OK`)
- 300-399 : redirections
- 400-499 : erreurs côté client
- 500-599 : erreurs côté serveur

**Response Headers courants :**

| Header | Rôle |
|---|---|
| Date | Moment exact où le serveur a envoyé la réponse |
| Connection | Même logique que côté requête |
| Server | OS du serveur + version du serveur web (ex : Nginx/1.1) |
| Last-Modified | Date de dernière modification de la ressource — utilisé par les mécanismes de cache |
| Content-Type | Type de données envoyées |
| Content-Length | Taille des données envoyées |

**Response Body** — la ressource elle-même (ex : code HTML), affichée ensuite par le
navigateur du client.

## Questions de la leçon

- Couche OSI de HTTP → **Layer 7 (Application)**
- Header de requête contenant navigateur + OS → **User-Agent**
- Code de statut HTTP indiquant un succès → **200** (OK)
- Méthode HTTP qui évite que les paramètres apparaissent dans l'URL → **POST**
- Header de requête contenant les jetons de session → **Cookie**

## Point clé

Cette leçon est la base technique indispensable pour comprendre toutes les attaques web à
venir (SQL Injection, XSS, Command Injection...) — elles s'expriment presque toutes via des
paramètres malformés dans la Request Line, les headers, ou le body.
