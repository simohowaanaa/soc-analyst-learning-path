# Dynamic Analysis

## Pourquoi analyser en dynamique ?

Les URLs et fichiers d'un email suspect doivent être testés sans risquer sa propre machine.
On les exécute/visite dans un environnement sandbox (isolé) et on observe les changements
causés sur le système pour juger de leur dangerosité.

## Tester des URLs sans risque — Browserling

Service permettant de visiter un site suspect via un navigateur distant, sans toucher sa
propre machine.
- Avantage : pas d'exposition à une éventuelle vulnérabilité zero-day du navigateur, puisque
  ce n'est pas sa propre machine qui visite le site.
- Inconvénient : si le fichier malveillant se télécharge depuis le site, impossible de
  l'exécuter dans Browserling → peut interrompre l'analyse à ce stade.

## Réflexe essentiel avant de cliquer : nettoyer l'URL

Vérifier si le lien contient des infos sensibles dans les paramètres — ex :
`popularshoppingsite.com/email=personal_email@gmail.com`. Même sans saisir de mot de passe
sur la page de phishing, visiter le lien avec son email en paramètre confirme à l'attaquant
que cette adresse est valide et active → il pourra cibler cette personne avec du social
engineering plus poussé dans de futures attaques. Retirer/modifier ces infos avant d'accéder
au site pendant l'analyse.

## Environnements sandbox (fichiers ET sites)

- VMRay
- JoeSandbox
- AnyRun
- Hybrid Analysis (Falcon Sandbox)

## Piège : le malware peut jouer la montre

Certains malwares attendent volontairement un certain temps avant d'agir, pour rendre la
détection plus difficile (rappel de la leçon "Common Mistakes", section 1). Laisser tourner
l'analyse suffisamment longtemps avant de conclure qu'un fichier est sain.

## Piège : l'absence d'URL/fichier ne veut rien dire

Un email peut ne contenir ni lien ni pièce jointe et être quand même malveillant —
l'attaquant peut envoyer le malware caché dans une image pour échapper aux outils d'analyse
automatiques.

## Point clé

L'analyse dynamique complète l'analyse statique en observant le comportement réel
(exécution en sandbox), mais demande de la patience (attendre le déclenchement du malware)
et de la prudence (nettoyer les URLs avant de les visiter pour ne pas confirmer sa propre
identité à l'attaquant).
