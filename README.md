# Projet Elise : Araignée Robotique

---

## Introduction

Bienvenue sur la présentation de mon projet **Elise** !  
L'objectif est de construire une araignée robotique capable de suivre un émetteur, en s'inspirant du personnage **"Elise"** (forme araignée) du jeu **League of Legends**.

---

## Architecture du Projet

Le système est basé sur :
- Un microcontrôleur pour piloter les moteurs (ESP32, STM32, etc.).
- Des moteurs DC avec réducteur et driver DRV8833 pour contrôler les pattes.
- Un système de levage par vis-écrou adapté aux mouvements verticaux.
- Des servomoteurs pour la synchronisation des articulations.

![Architecture du projet](images/architecture_elise.jpg)

---

## Principe de mouvement

Le mouvement recherché est de faire avancer l'araignée :
- Les paires de pattes 1/2, 3/4, 5/6 et 7/8 fonctionnent ensemble :  
  - Quand la patte 1 avance, la patte 2 recule, etc.
- Cela permet d’économiser **4 moteurs** et **de la place**.
- Le contrôle du déplacement repose sur l'**élévation** et **abaissement** des pattes :
  - Si une patte est levée pendant que son opposée est baissée, l’araignée avance.
  - Si les deux pattes d'une paire sont baissées, cela permet une **rotation**.

---

## Mécanique des Pattes

Chaque patte est contrôlée par des moteurs DC et un système d'engrenages.

> **Remarque :**  
> La deuxième version de la patte est plus épaisse au niveau du deuxième "os" pour plus de robustesse.  
> Le design intègre également un chanfrein corrigé pour permettre une rotation correcte de la patte.

![Photo Patte Elise](images/photo_patte_ELISE.jpg)

L'intérieur du corps de l'araignée montre :
- Une colonne centrale d'engrenage motorisée.
- Les engrenages des extrémités transmettent le mouvement par effet levier sur les pattes.

![Top View Corp Elise](images/corp_topview_ELISE.png)

La partie bleue est vissée aux engrenages excentrés, permettant à une patte de reculer tandis que l’autre avance.

![Joint Patte Corps Elise](images/joint_patte_corp_ELISE.png)
![Photo Engrenage Elise](images/photo_engrenage_ELISE.jpg)

---

## Electronique Embarquée

Le contrôle est réalisé via :
- **PWM** pour la vitesse des moteurs,
- **GPIO** pour la direction.

Chaque moteur est géré indépendamment, afin d'optimiser la diversité de mouvements programmables.

---

### Schéma électronique

- **Partie STM32G431** :

![Schéma STM32](images/schema_stm32.png)

- **Driver moteurs** :

![Driver moteurs](images/schema_driver_moteur.png)

- **Connecteurs et trous de montage** :

![Connecteurs PCB](images/schema_connecteurs.png)

---

### Routage PCB

- **Top layer** : Partie STM32 avec plan de masse 3.3V.
- **Bottom layer** : Partie driver avec plan d'alimentation 7.5V.

![Routage Top](images/routage_top.png)
![Routage Bottom](images/routage_bottom.png)

---

### PCB final

![PCB Vue 1](images/pcb_vue1.png)
![PCB Vue 2](images/pcb_vue2.png)

---

## Perspectives

Prochaines étapes :
- Intégration d’un **système de vision** pour que l'araignée puisse repérer dynamiquement l’émetteur et ajuster sa trajectoire en temps réel.
- ⚠️ **Note** : Cette partie n’a pas encore été implémentée dans le PCB actuel.

---

<p align="center">
  Projet réalisé par Victor Morel - Année 2025
</p>
