# Email Header Analysis

Mise en pratique de la leçon précédente. Deux questions clés à toujours se poser en analysant
un header suspect.

## 1) L'email vient-il vraiment du bon serveur SMTP ?

Méthode :
1. Regarder le champ `Received` pour voir le vrai chemin technique de l'email.
2. Regarder le champ `From` (affiché à l'utilisateur) pour voir le domaine prétendu.
3. Vérifier via MXToolbox quels serveurs mail sont réellement utilisés par ce domaine.
4. Comparer : si aucune correspondance entre l'IP réelle et les serveurs légitimes du
   domaine → l'email est spoofé.

**Exemple** : email prétendant venir de `letsdefend.io` (From), mais `Received` montre qu'il
vient de `emkei.cz` (IP `101.99.94.116`). Or `letsdefend.io` n'utilise que des serveurs
Google (aspmx.l.google.com...) — aucune correspondance → email spoofé.

`emkei.cz` est un site connu permettant d'envoyer de faux emails à des fins de
test/démonstration — classique en pédagogie/CTF.

## 2) Les champs `From` et `Return-Path`/`Reply-To` sont-ils identiques ?

En temps normal, l'expéditeur affiché et l'adresse qui recevra les réponses devraient être
identiques. Une différence est un signal d'alerte classique.

**Scénario type (fraude au président / BEC)** : un attaquant usurpe le nom d'un employé,
prétend qu'une facture doit être payée, et place sa propre adresse dans `Reply-To`. La
réponse de la victime part alors directement chez l'attaquant, sans que ça saute aux yeux
dans l'interface normale du client mail.

⚠️ Une différence From/Reply-To ne prouve pas à elle seule le phishing — il faut regarder
l'ensemble (pièce jointe malveillante, URL louche, contenu trompeur...), voir
[Static Analysis](05-Static-Analysis.md).

## Questions du labo (Header-Challenge.zip, email "May God Bless You...eml")

Header réel analysé : `Return-Path: <mrs.dara@jcom.home.ne.jp>`,
`Received: from mgw1.mx.zaq.ne.jp (snd01105-jc.im.kddi.ne.jp. [222.227.81.181])` — un
schéma classique d'arnaque (romance scam / avance de fonds) plutôt qu'un spoofing technique
de domaine d'entreprise, mais la méthode d'analyse est identique.

- Adresses différentes entre expéditeur et Reply-To ? → **Y** (confirmé correct)
- Adresse de réponse si on répond → **mrs.dara@daum.net** (confirmé correct)
- IP d'envoi de l'email → **222.227.81.181** (confirmé correct)

## Point clé

Ces 2 vérifications (bon serveur SMTP + cohérence From/Reply-To) sont les 2 premiers
réflexes d'un analyste face à un email suspect — rapides à faire, et souvent suffisantes pour
confirmer un spoofing évident.
