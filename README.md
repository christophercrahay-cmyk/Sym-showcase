# SYM

> Projet expérimental d'IA incarnée : relier perception, voix, agents logiciels et robotique dans un système capable d'interagir avec son environnement.

**Statut : vitrine technique.** Le dépôt de développement de SYM reste privé. Cette vitrine présente les objectifs, les briques du système et la démarche d'intégration sans publier les mécanismes internes, configurations, prompts ou documents de travail.

> **Technical review:** [Architecture evidence and limitations](AUDIT.md) — perception, decision and physical action.

**[Voir la démonstration vidéo SYM sur le portfolio](https://christopher-crahay.vercel.app/work/sym)** — prototype physique, réponse vocale et animation de la mâchoire. Cette vidéo ne valide pas à elle seule tous les chemins matériels et logiciels décrits.

**[TikTok du projet SYM : @symrobot](https://www.tiktok.com/@symrobot)** — vidéos publiques du projet. Ces publications donnent un aperçu du prototype, sans constituer des tests techniques reproductibles.

## Exemples de code commentés

[Consulter les exemples techniques](CODE_EXAMPLES.md) — extraits **illustratifs**, volontairement simplifiés, distincts du code privé. Ils montrent des frontières d'architecture et leurs limites, sans prétendre constituer une preuve de fonctionnement.


## L'idée

Un assistant IA classique reste essentiellement enfermé dans une interface logicielle. SYM explore le problème inverse : **comment relier une intelligence logicielle au monde physique ?**

Le projet sert de terrain d'intégration entre plusieurs disciplines :

- agents et modèles de langage ;
- perception visuelle ;
- entrée et sortie vocales ;
- électronique embarquée ;
- robotique ;
- orchestration entre services cloud et traitements locaux ;
- fabrication et intégration physique.

## Architecture — vue publique

```text
                   ┌─────────────────┐
                   │   Utilisateur   │
                   └────────┬────────┘
                            │
              voix / image / interaction
                            │
                            v
                 ┌───────────────────┐
                 │ Couche perception │
                 │  audio + vision   │
                 └─────────┬─────────┘
                           │
                           v
                 ┌───────────────────┐
                 │ Couche IA / agents│
                 │ contexte + décision│
                 └─────────┬─────────┘
                           │
                  actions / réponses
                           │
             ┌─────────────┴─────────────┐
             v                           v
      Interaction vocale          Système physique
                                  robot / capteurs
                                  actionneurs
```

Le diagramme décrit uniquement les grandes responsabilités. Les protocoles internes, règles d'orchestration et configurations détaillées ne sont pas publiés.

## Prototype physique

SYM s'appuie notamment sur une plateforme humanoïde **InMoov** fabriquée progressivement par impression 3D et intégration électronique.

Le prototype permet d'aborder l'IA comme un **système complet**, et pas uniquement comme un appel à un modèle : alimentation, calcul, réseau, capteurs, audio, caméra, contraintes mécaniques et latence font partie du problème.

Parmi les briques matérielles explorées :

- structure humanoïde imprimée en 3D ;
- microcontrôleurs **ESP32-S3** ;
- module caméra compact ;
- chaîne audio pour interaction vocale ;
- capteurs et actionneurs nécessaires aux expérimentations robotiques.

## Voix

La chaîne vocale est pensée comme un pipeline :

```text
Microphone
    ↓
Capture audio
    ↓
Détection / préparation
    ↓
Speech-to-Text
    ↓
Traitement par le système IA
    ↓
Réponse
    ↓
Text-to-Speech / action
```

Le projet permet également d'expérimenter la migration progressive de certaines fonctions du cloud vers du traitement local lorsque cela apporte un intérêt en matière de latence, de disponibilité ou de contrôle.

## Vision

La caméra n'est pas conçue comme un simple flux vidéo destiné à l'utilisateur. Elle constitue une entrée potentielle du système de perception.

L'objectif architectural est de pouvoir transformer une observation en information exploitable par les autres composants du système, tout en gardant séparées les responsabilités de capture, interprétation et décision.

## Agents et orchestration

SYM est aussi un banc d'essai pour l'intégration d'agents IA.

Le problème intéressant n'est pas seulement de produire une réponse textuelle, mais de déterminer :

```text
perception
    ↓
contexte
    ↓
raisonnement / sélection d'une capacité
    ↓
action logicielle ou physique
    ↓
retour d'état
```

Cette boucle impose des contraintes différentes d'un chatbot : une action physique doit rester observable, contrôlable et compatible avec l'état réel du système.

## Démarche de construction

SYM suit une logique de prototypage incrémental :

**1. Faire fonctionner une brique isolée.**  
Audio, caméra, modèle, microcontrôleur ou mécanisme.

**2. Définir une interface claire.**  
Éviter qu'un composant dépende inutilement de tous les autres.

**3. Intégrer.**  
Relier les briques dans un flux utilisable.

**4. Observer les défaillances.**  
Latence, perte de contexte, erreurs de perception, problèmes réseau ou limites physiques.

**5. Renforcer l'architecture.**  
Déplacer ou remplacer les composants lorsque les essais montrent leurs limites.

## Ce que ce projet démontre

SYM représente particulièrement mon approche d'**AI Builder / intégrateur de systèmes IA** : je ne travaille pas uniquement sur le modèle.

Le projet oblige à faire communiquer :

| Domaine | Exemples |
| --- | --- |
| IA | LLM, agents, contexte |
| Audio | capture, STT, TTS |
| Vision | caméra, perception |
| Edge | ESP32-S3 et composants embarqués |
| Robotique | structure, capteurs, actionneurs |
| Fabrication | impression 3D, assemblage |
| Intégration | protocoles, services, orchestration |

L'intérêt du projet est précisément situé **aux interfaces entre ces briques**.

## Démonstration

La [vidéo de SYM est disponible sur le portfolio](https://christopher-crahay.vercel.app/work/sym), accompagnée d'une description du fonctionnement, des protocoles et des limites actuelles.

## Limites de cette vitrine

Ce dépôt ne contient volontairement pas :

- le dépôt source de SYM ;
- les prompts système et instructions internes ;
- les configurations d'agents ;
- les documents d'audit et journaux de développement ;
- les clés, secrets ou variables d'environnement ;
- les données privées ;
- les détails d'orchestration propriétaires ;
- les configurations réseau ou matérielles sensibles.

L'objectif est de rendre **le travail d'intégration vérifiable et compréhensible**, sans transformer la publication du portfolio en publication du système lui-même.

---

**Christopher Crahay**  
AI Builder — Intégrateur de systèmes IA


<!-- audit-sequence: 01 | perception is not evidence; follow the system boundary -->
