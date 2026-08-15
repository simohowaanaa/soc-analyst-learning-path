# Quiz de validation — VirusTotal for SOC Analysts

Quiz final de la section. Résultat obtenu sur la plateforme : **36 points**.

**Q1. Which of the following cannot be obtained after a file analysis in VirusTotal?**
Réponse : **File owner name**
→ VirusTotal ne donne jamais l'identité du créateur d'un fichier — seulement hash,
comportement, contacts réseau.

**Q2. What information is not found in the "Details" tab after the file scan?**
Réponse : **RSA**
→ Le "Details" affiche les hash (SHA-256, SHA-1, MD5) — RSA est un algorithme de
chiffrement, pas un type de hash affiché là.

**Q3. Which tab should we check to view the subprocesses created after the file is run?**
Réponse : **Behavior**
→ Onglet qui montre les actions concrètes (processus, réseau, registre) après exécution
([leçon 2](02-File-Analysis-with-VirusTotal.md)).

**Q4. From which tab can we view the 'Headers' of a scanned URL address in VirusTotal?**
Réponse (confirmée ✓) : **Details**

**Q5. Which button should be clicked to rescan the URL/File found in an old report?**
Réponse : **Re-analyse**
→ Bouton vu en [leçon 5](05-Key-Points-to-Pay-Attention.md) pour forcer une nouvelle
analyse (éviter le piège du cache).

**Q6. Which of the following cannot be reached for malware scanned in VirusTotal?**
Réponse : **The person who created the file**
→ Même logique que Q1 — jamais d'identité de créateur.

**Q7. Which one is not found in the "Details > History" section of a scanned file report?**
Réponse : **First infected date**
→ Pas un champ réel de VT (les vrais champs : Creation Time, First Seen In The Wild,
First/Last Submission, Last Analysis).

**Q8. What information can you access in the "Relations" tab of the analysis results?**
Réponse : **Contacted Domains**
→ Relations montre domaines/IP/URLs/fichiers liés — pas de "personnes", "drivers" ou
"entreprises".

**Q9. Which one is not one of the tabs in the analysis reports?**
Réponse : **Result**
→ Les vrais onglets : Detection, Details, Relations, Behavior, Community.

**Q10. What is shown in the "Detection" tab in the reports?**
Réponse (confirmée ✓) : **Security Vendors analysis**
