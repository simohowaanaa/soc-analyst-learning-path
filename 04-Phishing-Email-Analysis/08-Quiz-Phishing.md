# Quiz de validation — Phishing Email Analysis

Quiz final de la section. Résultat obtenu sur la plateforme : **30 points**.

**Q1. At what stage of the Cyber Kill Chain are phishing attacks carried out?**
Réponse : **Delivery**
→ Le phishing correspond à la transmission de l'arme à la victime
([leçon 1](01-Introduction-to-Phishing.md)).

**Q2. Where should you check to see if an email is spoofed?**
Réponse : **Email header**
→ C'est là qu'on trouve `Received`, `Return-Path` pour tracer le vrai chemin
([leçons 3](03-What-is-an-Email-Header.md)-[4](04-Email-Header-Analysis.md)).

**Q3. Which protocol does not help you to determine whether an e-mail has been spoofed or
not?**
Réponse : **UDP**
→ Simple protocole de transport réseau, sans rapport avec l'authentification email
(contrairement à SPF/DKIM/DMARC, [leçon 2](02-Information-Gathering.md)).

**Q4. What does SMTP stand for?**
Réponse : **Simple Mail Transfer Protocol**

**Q5. Which of these are not part of the header of an e-mail?**
Réponse : **Check**
→ "From", "To" et "SPF" existent bien comme champs/résultats de header ; "Check" n'est pas
un champ réel ([leçon 3](03-What-is-an-Email-Header.md)).

**Q6. Which of the following cannot be achieved through a phishing attack?**
Réponse : **SQL injection**
→ Le phishing délivre URL/fichier malveillant et exploite l'humain (social engineering) — la
SQL injection est une attaque web technique, pas un résultat direct du phishing.
