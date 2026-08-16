# Quiz de validation — SIEM 101

Quiz final de la section.

**Q1. Which is not the log collection method?**
Réponse : **Via USB Drive**
→ Pas une méthode mentionnée dans le cours (agents / agentless / scripts manuels,
[leçon 2](02-Log-Collection.md)).

**Q2. Which one is not the cons of agentless log collection?**
Réponse (confirmée ✓) : **No required log collection software**
→ C'est un avantage de l'agentless, pas un inconvénient.

**Q3. Maximum packet size that can be sent with Syslog UDP is ..... bytes**
Réponse (confirmée ✓) : **1024**

**Q4. Which one is not the skill of log aggregator?**
Réponse : **Analysis**
→ Pas une fonction de l'agrégateur (Filtering/Parsing/Enrichment le sont,
[leçon 3](03-Log-Aggregation-and-Parsing.md)).

**Q5. You are using hash blacklist for 'mimikatz.exe'. How can attacker bypass it?**
Réponse (confirmée ✓) : **echo 1 >> mimikatz.exe**
→ Modifie le contenu du fichier → change son hash → contourne une blacklist basée sur hash
(`mv`/`cp`/`tail` ne changent pas le hash, seul le contenu modifié le change).

**Q6. Select correct one about whitelist method**
Réponse (confirmée ✓) : **Highly effective but difficult to manage**
→ Définition exacte vue en [leçon 5](05-Alerting.md).

**Q7. Why indexing is important for storage technology?**
Réponse (confirmée ✓) : **Fast access to data**

**Q8. Which one is correct about long tail analysis?**
Réponse (confirmée ✓) : **Least common events are most useful**

**Q9. Select correlation about brute force attack**
Réponse : **15 Login failed in 1 minute with the same IP address**
→ Signature typique d'un brute force (échecs répétés, même source).

**Q10. Which is one of the features you should pay attention to when storing log?**
Réponse (confirmée ✓) : **Search speed**
