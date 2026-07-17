# 01 - SOC Fundamentals

**Statut :** 🟨 en cours (9 leçons, 11 questions, 1 quiz — ~30 min)

## Résumé

Cours d'introduction au métier de SOC Analyst : types de SOC, rôles et responsabilités,
relation avec le SIEM, gestion des logs, outils (EDR, SOAR), threat intelligence, et
erreurs courantes à éviter. Base indispensable avant les sections techniques suivantes.

## Leçons

1. [x] [Introduction to SOC](01-Introduction-to-SOC.md)
2. [x] [SOC Types and Roles](02-SOC-Types-and-Roles.md)
3. [x] [SOC Analyst and Their Responsibilities](03-SOC-Analyst-and-Their-Responsibilities.md)
4. [x] [SIEM and Analyst Relationship](04-SIEM-and-Analyst-Relationship.md)
5. [x] [Log Management](05-Log-Management.md)
6. [x] [EDR - Endpoint Detection and Response](06-EDR-Endpoint-Detection-and-Response.md)
7. [ ] [SOAR - Security Orchestration Automation and Response](07-SOAR.md)
8. [ ] [Threat Intelligence Feed](08-Threat-Intelligence-Feed.md)
9. [ ] [Common Mistakes made by SOC Analysts](09-Common-Mistakes-made-by-SOC-Analysts.md)
10. [ ] Quiz de validation

## Points clés à retenir

### Log Management vs EDR

| | Log Management | EDR |
|---|---|---|
| Niveau | Réseau / infrastructure globale | Endpoint (poste/serveur individuel) |
| Collecte | Logs de toutes sources (proxy, firewall, exchange, DNS...) — trafic qui transite | Données propres à une machine : processus, terminal history, browser history, connexions réseau |
| Question typique | "Qui d'autre a communiqué avec cette IP/domaine ?" | "Qu'est-ce qui s'est exécuté sur cette machine précise ?" |
| Action | Recherche/consultation uniquement | Recherche + action directe (Live Investigation, Containment) |

En pratique : SIEM alerte → EDR pour voir ce qui s'exécute sur la machine concernée →
Log Management pour vérifier si d'autres machines ont été exposées au même IOC → EDR pour
isoler (Containment) les machines confirmées compromises.
