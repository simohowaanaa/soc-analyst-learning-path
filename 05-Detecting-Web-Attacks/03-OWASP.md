# OWASP

## Qu'est-ce qu'OWASP ?

OWASP = Open Worldwide Application Security Project. Fondation à but non lucratif dédiée à
l'amélioration de la sécurité des logiciels. LA référence en matière de sécurité des
applications web.

## Le OWASP Top 10

Tous les quelques années, OWASP publie un classement des 10 vulnérabilités web les plus
critiques. Dernière édition (au moment du cours) : **2021**.

1. Broken Access Control
2. Cryptographic Failures
3. Injection
4. Insecure Design
5. Security Misconfiguration
6. Vulnerable and Outdated Components
7. Identification and Authentication Failures
8. Software and Data Integrity Failures
9. Security Logging and Monitoring Failures
10. Server-Side Request Forgery (SSRF)

**Évolution 2017 → 2021** : certaines catégories ont fusionné (ex : "Broken Authentication"
2017 absorbée dans "Identification and Authentication Failures"), 2 nouvelles entrées :
Insecure Design et Server-Side Request Forgery.

## Questions de la leçon (vérifiées)

- Outil créé par OWASP pour scanner des applications web → **ZAP** (Zed Attack Proxy)
- Domaine sur lequel OWASP se concentre → **Web Applications**
- Projet d'application web volontairement vulnérable écrit en Node.js par OWASP →
  **juice_shop** (OWASP Juice Shop — réponse attendue par LetsDefend ; NodeGoat existe aussi
  côté OWASP mais n'était pas la réponse attendue ici)
- Ce que révèle le OWASP Top 10 → **Most critical security risks to web applications**

## Point clé

L'OWASP Top 10 n'est pas une liste des vulnérabilités les plus fréquentes, mais des plus
critiques en termes de risque — nuance importante entre fréquence et gravité.

## Référence

[1] https://owasp.org/
