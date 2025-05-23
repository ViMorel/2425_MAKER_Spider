# Projet Elise : Araignée Robotique

---

## Introduction

Bienvenue sur la présentation de mon projet **Elise** !  
L'objectif est de construire une araignée robotique capable de suivre un émetteur, en s'inspirant du personnage **"Elise"** (forme araignée) du jeu **League of Legends**.

---

## Architecture du Projet

'''
cd something 
'''

Le système est basé sur :
- Un microcontrôleur pour piloter les moteurs (ESP32, STM32, etc.).
- Des moteurs DC avec réducteur et driver DRV8833 pour contrôler les pattes.
- Un système de levage par vis-écrou adapté aux mouvements verticaux.
- Des servomoteurs pour la synchronisation des articulations.

![patte numérotation](https://github.com/user-attachments/assets/8f8c0ff6-cf90-49e2-8686-b84d244657de)


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

![photo_patte_ELISE](https://github.com/user-attachments/assets/0a2d7b01-e418-49be-8b43-c5079cd56dd3)
![modele_patte_ELISE](https://github.com/user-attachments/assets/8be8aed2-c5b8-4565-86b9-8490ab632d3f)


L'intérieur du corps de l'araignée montre :
- Une colonne centrale d'engrenage motorisée.
- Les engrenages des extrémités transmettent le mouvement par effet levier sur les pattes.
![corp__topview_ELISE](https://github.com/user-attachments/assets/b24d40f7-9911-4887-8833-2a1f1961622a)



La partie bleue est vissée aux engrenages excentrés, permettant à une patte de reculer tandis que l’autre avance.
![fixation_patte_ELISE](https://github.com/user-attachments/assets/ac6329e4-fa3f-455d-ad92-fa3aee28b8eb)
![photo_engrenage_ELISE](https://github.com/user-attachments/assets/74fefcbe-bb91-4981-84bd-7800ae79f679)



---

## Electronique Embarquée

Le contrôle est réalisé via :
- **PWM** pour la vitesse des moteurs,
- **GPIO** pour la direction.

Chaque moteur est géré indépendamment, afin d'optimiser la diversité de mouvements programmables.

---

### Schéma électronique

- **Partie STM32G431** :

![image](https://github.com/user-attachments/assets/7cee185d-01cd-4c83-9915-2a7232a30f27)


- **Driver moteurs** :

![image](https://github.com/user-attachments/assets/6d4ff623-47fb-44ad-8482-fb5006ec64dd)


- **Connecteurs et trous de montage** :

![image](https://github.com/user-attachments/assets/79dd16a0-7c6e-4142-9e9e-34cb45a0a3fa)


---

### Routage PCB

- **Top layer** : Partie STM32 avec plan de masse 3.3V.
![image](https://github.com/user-attachments/assets/b8691817-0cc5-4517-8409-10e7a6af6c81)

- **Bottom layer** : Partie driver avec plan d'alimentation 7.5V.
![image](https://github.com/user-attachments/assets/26b888ae-7ad8-4f40-b9a9-ae0ca1ab16fe)


---

### PCB final

![image](https://github.com/user-attachments/assets/0c76d15b-6af6-4052-8b53-9aff4320a54a)
![image](https://github.com/user-attachments/assets/759c7405-7a90-4887-be61-a7fd35ff9ed7)


---

## Perspectives

Prochaines étapes :
- Intégration d’un **système de vision** pour que l'araignée puisse repérer dynamiquement l’émetteur et ajuster sa trajectoire en temps réel.
- ⚠️ **Note** : Cette partie n’a pas encore été implémentée dans le PCB actuel.

---

<p align="center">
  Projet réalisé par Victor Morel - Année 2025
</p>
