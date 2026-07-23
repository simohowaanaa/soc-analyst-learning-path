# Information Gathering

## 1) Le Spoofing

Le protocole email n'a pas d'authentification native — un attaquant peut envoyer un email
en usurpant l'identité de quelqu'un d'autre ("spoofing"), pour paraître fiable aux yeux de
la victime.

**Protocoles créés pour contrer ça :**
- SPF (Sender Policy Framework)
- DKIM (DomainKeys Identified Mail)
- DMARC

⚠️ Ces protocoles ne sont pas obligatoires — un domaine peut ne pas les avoir configurés
(signal de vulnérabilité au spoofing).

**Comment vérifier manuellement si un email est spoofé :**
1. Identifier l'adresse SMTP de l'email.
2. Récupérer les enregistrements SPF, DKIM, DMARC et MX du domaine (outil : MXToolbox
   SuperTool — MX Lookup, Blacklist Check, DNS Lookup, SPF/DKIM/DMARC Lookup...).
3. Comparer ces infos entre elles pour juger de la légitimité.
4. Pour les grandes organisations avec leur propre serveur mail : vérifier via un Whois si
   l'IP SMTP appartient bien à l'organisation.

⚠️ **Piège** : même si l'adresse de l'expéditeur n'est pas spoofée, l'email n'est pas
forcément sûr — un compte email légitime peut avoir été piraté et servir à envoyer des
emails malveillants sous une identité de confiance (déjà arrivé dans de vraies attaques).

## 2) Analyse du trafic email (Email Traffic Analysis)

Paramètres à rechercher dans la passerelle mail pour évaluer l'ampleur et la cible d'une
attaque :
- Adresse de l'expéditeur (ex : `info@letsdefend.io`)
- IP SMTP (ex : `127.0.0.1`)
- Domaine seul (`@letsdefend.io`)
- Nom seul, sans domaine (`letsdefend`) — l'attaquant peut avoir envoyé depuis plusieurs
  fournisseurs (Gmail, Hotmail...) avec un nom similaire
- Objet de l'email (utile car l'adresse expéditeur/SMTP peut changer constamment)

**Autres pistes :**
- Regarder les destinataires et l'horodatage : si les mêmes personnes reçoivent sans cesse
  des emails malveillants, leur adresse a peut-être fuité (ex : publiée sur PasteBin).
- Les attaquants utilisent des outils comme theHarvester (Kali Linux) pour trouver des
  adresses email publiques → ne pas exposer son email publiquement.
- Emails envoyés hors des heures de bureau → l'attaquant est peut-être dans un fuseau
  horaire différent (indice utile pour profiler l'attaque).

## Point clé

Cette leçon est la phase d'enquête préliminaire avant même d'ouvrir techniquement l'email —
comprendre le "qui, combien, quand" pour évaluer l'ampleur de la campagne de phishing, avant
de plonger dans l'analyse technique du header (prochaine leçon).
