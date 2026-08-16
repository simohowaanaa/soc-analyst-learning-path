# Log Aggregation and Parsing

## Le rôle du Log Aggregator

Premier point d'arrivée des logs générés. Avant d'envoyer vers la destination finale (le
SIEM), on peut modifier les logs ici — ex : ne garder que les codes de statut d'un log de
serveur web, en filtrant le reste.

## EPS — Events Per Second

Métrique clé pour dimensionner l'infrastructure. Formule : Events / Temps (en secondes).
Exemple : 1000 logs en 5 secondes → EPS = 200. Plus l'EPS augmente, plus il faut de
capacité d'agrégation et de stockage.

## Scaler l'agrégateur

Plusieurs agrégateurs peuvent être ajoutés pour ne pas surcharger le même à chaque fois —
répartition séquentielle ou aléatoire des logs entrants entre eux.

## Le traitement effectué par l'agrégateur — 3 opérations possibles

1. **Parsing** — structurer/découper le log brut en champs identifiables (IP, date,
   méthode/URL, code statut, User-Agent...).
2. **Filtering** — ne garder que ce qui est pertinent.
3. **Enrichment** — enrichir le log avec des infos supplémentaires.

## Log Modification — exemples concrets

- Uniformiser un format de date : la plupart arrivent en `dd-mm-yyyy`, une source isolée en
  `mm-dd-yyyy` → conversion nécessaire pour rester cohérent.
- Convertir un fuseau horaire (ex : UTC+2 → UTC+1) pour aligner tous les logs sur un
  référentiel commun.

## Log Enrichment — 3 exemples

- **Geolocation** — trouver la localisation géographique d'une IP et l'ajouter au log →
  gain de temps pour l'analyste, permet une analyse comportementale basée sur la
  localisation.
- **DNS** — résoudre un domaine en IP, ou l'inverse (reverse DNS, IP → domaine).
- **Add/Remove** — ajouter ou retirer des champs selon les besoins.

## Questions de la leçon

- Fonction qui n'est PAS un rôle du log aggregator → **Analysis**
  (Filtering, Parsing et Enrichment le sont ; l'analyse relève du SIEM/de l'analyste, pas de
  l'agrégateur qui ne fait que préparer la donnée)
- EPS pour un système recevant 150 000 logs/minute → 150 000 ÷ 60 secondes = **2500**

## Point clé

L'agrégateur est une étape de préparation, pas d'analyse — il structure, nettoie et enrichit
la donnée pour que le SIEM (et l'analyste) puisse ensuite travailler efficacement dessus.
