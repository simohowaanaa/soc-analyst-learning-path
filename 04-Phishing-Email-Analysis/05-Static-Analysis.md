# Static Analysis

## Le piège du HTML dans les emails

Les emails HTML permettent un contenu plus attractif (boutons, mise en forme), mais
permettent aussi de cacher une URL malveillante derrière un texte/bouton d'apparence
anodine. Ex : texte affiché `http://popularshoppingsite.com`, mais URL réelle (visible au
survol, sans cliquer) : `https://maliciousaddress.com/email=personal_email@gmail.com`.
Réflexe de base : toujours survoler un lien avant de cliquer.

## Indice n°1 : l'âge du domaine

Dans la plupart des attaques de phishing, l'attaquant enregistre un nouveau nom de domaine
et mène son attaque en quelques jours. Un domaine récent dans un email suspect = signal
d'alerte fort.

## Le piège du cache VirusTotal

Si quelqu'un a déjà analysé une adresse/fichier sur VirusTotal, l'outil ne réanalyse pas
automatiquement — il montre le résultat en cache, potentiellement vieux de plusieurs mois.

**Exemple** : `umuttosun.com` apparaît "0/71 - harmless", mais la date du scan indique
**9 mois**. Il faut cliquer sur le bouton de rescan pour relancer une analyse fraîche.

**Pourquoi c'est important** : un attaquant peut avoir soumis son domaine à VirusTotal
*avant* de le rendre malveillant, pour voir son taux de détection pendant la préparation,
sachant que ce résultat "propre" reste visible en cache. En relançant l'analyse, le moteur
antivirus peut alors détecter le phishing.

## Analyse statique vs dynamique

L'analyse statique des fichiers de l'email donne des infos sur les capacités du fichier,
mais prend du temps. L'analyse dynamique ([leçon 6](06-Dynamic-Analysis.md)) donne
l'information nécessaire plus rapidement.

## Réputation de l'IP/SMTP — Cisco Talos Intelligence

Rechercher l'adresse SMTP sur Talos Intelligence donne sa réputation et son statut de
blacklist.

**Exemple** : IP `185.10.68.76`, hébergée aux Seychelles chez Flokinet Ltd (hébergeur connu
pour tolérer du contenu controversé), Email Reputation "Poor", blacklistée chez Talos (bien
que "Not Listed" sur Spamhaus/SpamCop — d'où l'intérêt de croiser plusieurs sources).

Si l'IP est blacklistée → peut signifier que l'attaque a été menée depuis un serveur
compromis plutôt qu'une infrastructure dédiée à l'attaquant.

Croiser aussi l'IP SMTP sur VirusTotal et AbuseIPDB pour confirmer une activité malveillante
passée.

## Point clé

L'analyse statique = inspecter sans exécuter : survoler les liens, vérifier l'âge du
domaine, forcer un nouveau scan VirusTotal (ne jamais se fier au cache), et croiser la
réputation IP sur plusieurs sources (Talos, VirusTotal, AbuseIPDB) avant de conclure.
