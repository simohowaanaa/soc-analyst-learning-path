# What is an Email Header and How to Read Them?

## Qu'est-ce qu'un header d'email ?

Section de l'email contenant les métadonnées : expéditeur, destinataire, date, et d'autres
champs techniques (`Return-Path`, `Reply-To`, `Received`...). Invisible dans l'interface
normale d'un client mail, mais accessible en quelques clics.

## À quoi ça sert (3 usages)

1. **Identifier expéditeur/destinataire** via `From` et `To`.
2. **Filtrer le spam** — l'analyse du header permet de détecter des emails indésirables.
3. **Tracer le trajet de l'email** — vérifier s'il vient vraiment du bon domaine, ou d'un
   serveur qui imite ce nom de domaine (lien direct avec le spoofing,
   [leçon 2](02-Information-Gathering.md)).

## Champs importants

| Champ | Rôle |
|---|---|
| From | Nom + adresse email de l'expéditeur |
| To | Destinataire(s) — inclut aussi CC et BCC |
| Date | Horodatage d'envoi (format Gmail : jour jj mois aaaa hh:mm:ss) |
| Subject | Résumé/objet de l'email |
| Return-Path (= Reply-To) | Adresse où part réellement la réponse si on clique "Répondre" — peut différer du From affiché, signal important |
| DKIM-Signature | Signature qui authentifie l'email |
| Message-ID | Identifiant unique de l'email — jamais deux emails avec le même |
| MIME-Version | Standard qui permet d'attacher du contenu non-textuel (images, pièces jointes) via SMTP |
| Received | Liste des serveurs traversés, en ordre chronologique **inversé** : en haut = dernier serveur traversé, en bas = origine de l'email. Très utile pour tracer le vrai chemin. |
| X-Spam Status | Score de spam de l'email + seuil de la boîte mail |

## Comment accéder au header

- **Gmail** : ouvrir l'email → menu "⋮" → "Download message" → ouvrir le fichier `.eml` avec
  un éditeur de texte.
- **Outlook** : ouvrir l'email → File → Info → Properties → Internet headers.

## Questions du labo (exercice pratique LetsDefend)

Basées sur le fichier fourni dans l'environnement de lab (`Challenge+Mail.zip`, mot de passe
`infected`) — email "Top 3 Blog Posts for SOC Teams" envoyé à `ogunal@letsdefend.io` :

- **Adresse de réponse** (champ `Reply-To`) → **info@letsdefend.io**
- **Année d'envoi** (champ `Date: Mon, 21 Mar 2022 20:45:17 +0000`) → **2022**
- **Message-ID** (sans `< >`) →
  `74bda5edf824cea8aad36e707.675c34a61f.20220321204512.a02caaccf3.a268ce5a@mail41.suw13.rsgsv.net`

**Observation intéressante** : l'email vient en fait d'une plateforme d'emailing
(**Mailchimp**, visible via `X-Mailer: Mailchimp Mailer`, le domaine réel
`mail41.suw13.rsgsv.net`, et le header `List-Unsubscribe`), pas directement du serveur de
LetsDefend. Légitime ici (newsletter marketing), mais bon exemple de pourquoi il faut
toujours vérifier le vrai chemin technique (`Received`, domaine réel) plutôt que de se fier
uniquement au nom affiché dans `From`.

## Point clé

Le champ `Received` est la clé pour tracer le vrai parcours d'un email : lu de bas en haut,
il révèle si l'email vient vraiment du serveur qu'il prétend, ou d'ailleurs.
