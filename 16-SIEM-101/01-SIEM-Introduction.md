# SIEM Introduction

## Définition (rappel et approfondissement)

Le SIEM collecte et interprète les données de l'organisation pour détecter des menaces
potentielles, avec une surveillance en temps réel. Déjà vu côté usage (section 1) ; ici,
l'objectif est de comprendre ce qui se passe "derrière" l'outil — pas devenir ingénieur
SIEM, juste avoir une bonne vision d'ensemble utile à un analyste.

## Les 4 sujets couverts dans cette section

1. Comment fonctionne un SIEM ?
2. Comment collecte-t-il les logs ?
3. Le stockage des logs
4. La création d'alertes

## Les solutions SIEM sur le marché

Selon le rapport Gartner 2021 (Magic Quadrant), les solutions SIEM commerciales se
répartissent en 4 catégories :
- **Leaders** (meilleure exécution + vision complète) : Exabeam, IBM, Securonix, Splunk
- **Visionaries** : LogRhythm, Gurucul, Microsoft, Sumo Logic, Fortinet, Rapid7
- **Challengers** : peu représentés dans ce rapport
- **Niche Players** : Elastic, LogPoint, NetWitness, Venustech, FireEye, McAfee, Huawei,
  Odyssey, Micro Focus, ManageEngine

(Méthodologie Gartner classique pour comparer des solutions logicielles — utile pour situer
des outils déjà croisés, comme Splunk, vu en détail plus tard dans le path.)

## Relation SIEM ↔ SOC Analyst

Les menaces potentielles détectées par le SIEM sont examinées par les analystes SOC.
Exemple concret : la page "Monitoring" de LetsDefend, ce sont les alertes générées par le
SIEM.

## Point clé

Cette leçon pose le cadre — les 4 prochaines leçons détaillent chacun des 4 sujets annoncés
(collecte, agrégation/parsing, stockage, alerting), dans l'ordre logique du cycle de vie
d'un log : de sa collecte jusqu'à la génération d'une alerte exploitable par l'analyste.
