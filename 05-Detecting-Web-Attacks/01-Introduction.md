# Introduction (Detecting Web Attacks)

## Pourquoi ce cours compte

Selon une étude d'Acunetix, **75% de toutes les cyberattaques** visent le niveau applicatif
web — la surface d'attaque la plus exploitée aujourd'hui.

## Qu'est-ce qu'une application web ?

Une application accessible via un navigateur pour fournir un service — Google, Facebook,
YouTube (hors apps mobiles) sont en réalité des applications web. Comme elles servent
d'interface principale entre une organisation et internet, elles sont une cible de choix
pour accéder à des systèmes internes, voler des données, ou causer des interruptions de
service, avec des conséquences financières potentiellement lourdes.

## Techniques d'attaque couvertes dans ce cours

- SQL Injection
- Cross Site Scripting (XSS)
- Command Injection
- IDOR (Insecure Direct Object Reference)
- RFI & LFI (Remote/Local File Inclusion)
- File Upload (Web Shell)

## Compétences visées en fin de cours

Comprendre ce qu'est chaque vulnérabilité, pourquoi les attaquants les utilisent, et savoir
les identifier en tant qu'analyste (dans des logs, des requêtes HTTP...).

## Point clé

Ce cours change de logique par rapport aux précédents — jusqu'ici concepts/frameworks (SOC,
Kill Chain, MITRE, phishing), maintenant la mécanique technique concrète du web (requêtes
HTTP, paramètres, injections), nécessaire pour comprendre comment une attaque se manifeste
dans les logs qu'un SOC Analyst surveille au quotidien.

## Référence

[1] https://www.acunetix.com/websitesecurity/web-application-attack/
