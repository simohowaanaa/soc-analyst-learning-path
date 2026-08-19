# Result

## Objectif

Derniere etape de l'investigation : fermer proprement l'alerte, documenter les conclusions,
et consulter le rapport officiel.

## Fermer l'alerte

Retourner sur la page **Monitoring** dans l'Investigation Channel pour fermer l'alerte.

### Determiner True Positive ou False Positive

- **True Positive** : l'alerte est legitime, menace reelle confirmee
- **False Positive** : fausse alarme, rien de malveillant

Pour notre investigation EventID 257 : **True Positive** — l'email de phishing a ete
delivre, Felix a telecharge `free-coffee.zip`, le malware `coffee.exe` (PID 6697) s'est
execute et a communique avec le C2 `37.120.233.226:3451`.

### Documenter dans l'Analyst Note

Avant de fermer, ecrire un resume dans la section "Analyst Note" :
- Justification de la decision (pourquoi True Positive)
- Preuves trouvees (IOCs, timeline)
- Actions prises (suppression de l'email, containment)

## Apres la fermeture

### Closed Alerts

L'alerte fermee est consultable dans les **Closed Alerts** (page Monitoring). On y retrouve :
- Les reponses donnees au playbook
- Le rapport officiel de l'incident (incident report)
- Le walkthrough communautaire

### Case Management

La section **Case Management** permet de revoir les alertes fermees : details de l'alerte,
options choisies pendant l'analyse, et resultats.

## Question de la lecon (EventID: 257)

- Channel pour acceder au rapport officiel → **Closed Alerts**

## Recapitulatif de l'investigation complete

| Etape | Outil | Resultat |
|-------|-------|----------|
| Detection | Monitoring/SIEM | Alerte SOC282, phishing, severity Medium |
| Case Creation | Case Management + Playbook | Playbook phishing initie |
| Email Analysis | Email Security | Email delivre, piece jointe `free-coffee.zip` |
| Network Analysis | Log Management + Threat Intel | Telechargement confirme, C2 = 37.120.233.226:3451 |
| Endpoint Analysis | Endpoint Security (EDR) | coffee.exe (PID 6697), 7 child processes cmd.exe |
| Result | Monitoring | True Positive, alerte fermee |
