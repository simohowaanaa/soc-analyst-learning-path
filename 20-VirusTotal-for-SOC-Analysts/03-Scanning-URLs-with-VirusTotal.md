# Scanning URLs with VirusTotal

## Principe

Même logique que l'analyse de fichiers, mais pour une URL — onglet "URL" sur VirusTotal.
Interface quasi identique (Detection, Details déjà vus en
[leçon 2](02-File-Analysis-with-VirusTotal.md)), avec un onglet spécifique en plus : Links.

⚠️ Ne jamais accéder directement à une adresse malveillante étudiée en exemple — toujours
passer par le lien VirusTotal fourni.

## L'onglet Links

Liste les liens sortants que l'URL analysée pointe vers l'extérieur. Exemple : une URL
malveillante étudiée pointait vers `strato.de`. Autre exemple : scanner `letsdefend.io`
révèle des liens vers ses réseaux sociaux (Twitter, Discord, YouTube, Facebook, LinkedIn).

**Utilité pour l'analyste** : même si une URL ne contient pas directement de contenu
malveillant, elle peut pointer vers des adresses malveillantes → l'investigation doit
continuer au-delà de la première page.

## Questions de la leçon

- Catégorie de `google.com` selon Sophos → **search engines**
- Nom du fichier associé au hash `349d13ca99ab03869548d75b99e5a1d0` → **1word.doc**
- Catégorie de `letsdefend.io` selon Forcepoint ThreatSeeker → **information technology**

## Point clé

Au-delà du score de détection malveillant/propre, les catégories attribuées par les
fournisseurs (search engines, information technology...) aident aussi à contextualiser
rapidement la nature d'un site — utile pour distinguer un site légitime mal classé d'un vrai
site malveillant.
