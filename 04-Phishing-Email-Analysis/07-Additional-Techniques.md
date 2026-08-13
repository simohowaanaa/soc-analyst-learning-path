# Additional Techniques

Dernière leçon théorique de la section — comment les attaquants détournent des services
légitimes pour contourner la détection, plutôt que d'utiliser leur propre infrastructure
suspecte.

## 1) Services de stockage cloud légitimes (Google Drive, Microsoft OneDrive...)

L'attaquant piège la victime via un lien Google Drive / OneDrive qui semble inoffensif
(vrai lien Google/Microsoft), mais qui pointe vers un fichier malveillant hébergé sur ce
service. Le domaine étant légitime et de confiance, les filtres anti-phishing basés sur la
réputation du domaine ne se déclenchent pas.

## 2) Sous-domaines gratuits (Microsoft, WordPress, Blogspot, Wix...)

L'attaquant crée un sous-domaine gratuit sur ces plateformes (ex : `monsite.wordpress.com`).
Piège : les infos Whois d'un sous-domaine ne peuvent pas être recherchées séparément —
elles renvoient les infos du domaine principal. Un analyste vérifiant le Whois peut croire à
tort que cette adresse appartient depuis longtemps à une institution connue, alors que le
sous-domaine vient d'être créé par l'attaquant quelques minutes plus tôt.

## 3) Services de création de formulaires (ex : Google Forms)

Plutôt que de créer son propre site de phishing, l'attaquant utilise un service comme Google
Forms pour collecter les identifiants de la victime directement. Le domaine restant
`forms.google.com`, il ne déclenche pas les antivirus/filtres, et le Whois montre "Google"
comme propriétaire → l'analyste est trompé une deuxième fois par la réputation du domaine
parent.

## Point commun aux 3 techniques

L'attaquant exploite la confiance accordée aux grandes plateformes légitimes — ni la
réputation du domaine, ni le Whois ne suffisent alors à juger de la fiabilité d'un lien. Il
faut toujours regarder le contenu réel de la page/du fichier final, pas seulement le nom de
domaine affiché.

## Point clé

Cette leçon boucle la partie théorique de la section : aucune vérification isolée (domaine,
Whois, réputation) n'est suffisante seule — l'analyse doit toujours être globale et
contextuelle (rappel de la leçon [Email Header Analysis](04-Email-Header-Analysis.md)).
