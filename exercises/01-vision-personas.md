# Vision & Personas — CDC sections 1-2

## Objectif
Definir la vision produit, les objectifs, non-objectifs et personas de votre projet.
Cela correspond aux **sections 1 (Vision) et 2 (Objectifs)** de votre CDC technique.

## Consignes

### 1. Vision (1 phrase)
Ecrivez UNE phrase qui resume ce que votre projet fait et pour qui.

### 2. Objectifs (3-5)
Qu'est-ce que le produit DOIT faire ?

### 3. Non-objectifs (3)
Qu'est-ce que le produit ne fait PAS (pour cette version) ?

### 4. Personas (2)
Format court :

```
Persona : <Prenom>
Role : <role / profil utilisateur>
Besoin principal : <1 phrase>
Frustration : <1 phrase>
```

## Fichier a modifier

`docs/cdc-technique.md` — sections 1 et 2

## Livrable
- PR #1 "CDC sections 1-2 : Vision + Personas"
- Review obligatoire par un autre membre
- Au moins 1 approbation avant merge

---

## Exemples par projet

### Projet Flipper

**Vision :** "Flipper est un flipper virtuel multijoueur qui combine une simulation physique realiste (Three.js) avec des controleurs physiques (ESP32) pour offrir une experience arcade moderne."

**Objectifs :**
1. Simuler une table de flipper avec physique realiste (bille, bumpers, flippers)
2. Synchroniser 3 ecrans (playfield, backglass, DMD) en temps reel via WebSocket
3. Permettre le controle via interface web ET controleurs physiques (ESP32)

**Non-objectifs :**
1. Pas de mode multijoueur en ligne (local uniquement)
2. Pas d'editeur de table personnalise
3. Pas de systeme de microtransactions

**Personas :**

- **Lea**, 22 ans, etudiante dev web — veut un projet fun qui combine front et IoT. Frustration : les projets scolaires sont rarement jouables.
- **Marc**, 24 ans, passione d'arcade — veut retrouver les sensations du flipper physique. Frustration : les simulations existantes manquent de feedback physique.

---

### Projet Robotique

**Vision :** "Robot Assistance est un robot autonome d'assistance qui navigue dans un environnement interieur, detecte et saisit des objets, et se pilote via un dashboard web accessible."

**Objectifs :**
1. Navigation autonome dans un espace interieur (SLAM + LiDAR)
2. Detection et saisie d'objets avec le bras robotique
3. Dashboard web temps reel pour monitoring et pilotage manuel

**Non-objectifs :**
1. Pas de navigation en exterieur
2. Pas de reconnaissance vocale
3. Pas d'apprentissage autonome en production (modeles pre-entraines uniquement)

**Personas :**

- **Sofia**, 23 ans, etudiante robotique — veut comprendre l'integration ROS 2 + web. Frustration : la doc ROS est dense et les tutoriels sont fragmentes.
- **Karim**, 25 ans, ingenieur accessibilite — veut un robot utile pour des personnes a mobilite reduite. Frustration : les solutions existantes sont trop cheres et pas open source.

---

## Aide

Structure suggeree pour les sections 1-2 de `docs/cdc-technique.md` :

```markdown
# Cahier des Charges Technique

## 1. Vision
[1 phrase]

## 2. Objectifs et perimetre

### Objectifs
1. ...
2. ...
3. ...

### Non-objectifs
1. ...
2. ...
3. ...

### Personas

#### Persona 1 : [Prenom]
- Role : ...
- Besoin : ...
- Frustration : ...

#### Persona 2 : [Prenom]
- Role : ...
- Besoin : ...
- Frustration : ...
```
