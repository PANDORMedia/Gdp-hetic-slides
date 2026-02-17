# Use Cases — CDC section 3

## Objectif
Ecrire 6 use cases et en detailler 2 critiques.
Cela correspond a la **section 3 (Use cases)** de votre CDC technique.

## Consignes

### Phase 1 : Lister 6 use cases

Format court pour chaque :

```
UC-XX : <Nom>
Acteur : <qui>
But : <1 phrase>
```

### Phase 2 : Detailler 2 use cases critiques

Choisir 2 use cases et les detailler avec le template complet :

```
ID : UC-XX
Nom : ...
Acteurs : ...
But : ...
Preconditions : ...
Declencheur : ...

Scenario nominal :
1. ...
2. ...
3. ...

Extensions / erreurs :
- 2a. Si ... alors ...
- 3a. Si ... alors ...

Postconditions : ...

Notes / regles metier : ...
```

## Fichier a modifier

`docs/cdc-technique.md` — section 3

## Livrable
- PR #2 "CDC section 3 : Use cases v1"
- Avec review

---

## Exemples par projet

### Projet Flipper

**6 use cases :**
- UC-01 : Lancer une partie — Joueur — Demarrer une nouvelle partie de flipper
- UC-02 : Connecter un controleur physique — Joueur — Associer un ESP32 comme controleur
- UC-03 : Consulter les scores — Joueur — Voir le classement des meilleurs scores
- UC-04 : Configurer la table — Admin — Modifier les parametres de la table (vitesse bille, force bumpers)
- UC-05 : Synchroniser les ecrans — Systeme — Maintenir la coherence entre playfield, backglass et DMD
- UC-06 : Sauvegarder une partie — Joueur — Enregistrer son score en fin de partie

**Exemple detaille : UC-01 Lancer une partie**

```markdown
# UC-01 : Lancer une partie

## Acteurs
- Joueur (via interface web ou controleur ESP32)

## But
Demarrer une nouvelle partie de flipper avec la bille en position de lancement.

## Preconditions
- Le serveur WebSocket est demarre
- Au moins l'ecran playfield est connecte

## Declencheur
Le joueur appuie sur "Nouvelle partie" (web) ou sur le bouton Start (ESP32)

## Scenario nominal
1. Le systeme reinitialise le score a 0
2. Le systeme place la bille dans le lanceur
3. Le DMD affiche "Ready"
4. Le joueur actionne le lanceur (ressort)
5. La bille entre dans le playfield
6. Le systeme active la physique (Cannon.js)

## Extensions / erreurs
- 1a. Partie en cours : le systeme demande confirmation avant de reinitialiser
- 3a. DMD non connecte : la partie demarre quand meme (mode degrade)
- 5a. Capteur ESP32 non detecte : bascule en mode clavier automatiquement

## Postconditions
- Une partie est en cours
- Le score est affiche sur le backglass et le DMD
- Les flippers repondent aux commandes du joueur

## Notes
- La physique est calculee cote serveur (Cannon.js) et synchronisee via WebSocket
- Le lanceur a une force variable selon la duree d'appui
```

---

### Projet Robotique

**6 use cases :**
- UC-01 : Naviguer vers un point — Robot — Se deplacer de maniere autonome vers une destination
- UC-02 : Saisir un objet — Robot — Detecter, approcher et saisir un objet avec le bras
- UC-03 : Piloter manuellement — Operateur — Controler le robot a distance via le dashboard
- UC-04 : Cartographier l'environnement — Robot — Scanner et construire la carte SLAM
- UC-05 : Surveiller l'etat du robot — Operateur — Consulter les capteurs en temps reel sur le dashboard
- UC-06 : Eviter un obstacle dynamique — Robot — Detecter et contourner un obstacle en mouvement

**Exemple detaille : UC-02 Saisir un objet**

```markdown
# UC-02 : Saisir un objet

## Acteurs
- Robot (autonome) ou Operateur (via dashboard)

## But
Detecter un objet cible, s'en approcher et le saisir avec le bras robotique.

## Preconditions
- La camera RealSense est calibree
- Le bras robotique est en position initiale
- L'objet est dans le champ de vision

## Declencheur
L'operateur designe l'objet sur le dashboard OU le robot detecte l'objet cible automatiquement

## Scenario nominal
1. La camera detecte l'objet et calcule sa position 3D
2. Le robot planifie le trajet d'approche (ROS 2 Navigation)
3. Le robot se deplace jusqu'a portee du bras
4. Le bras se positionne au-dessus de l'objet
5. La pince se ferme et saisit l'objet
6. Le dashboard confirme "Objet saisi"

## Extensions / erreurs
- 1a. Objet non detecte : le robot tourne sur lui-meme pour scanner (360°)
- 3a. Obstacle sur le trajet : le robot recalcule le chemin (UC-06)
- 5a. Saisie echouee (objet glisse) : le robot relache, recalibre et reessaie (max 2 fois)

## Postconditions
- L'objet est tenu par le bras robotique
- La position de l'objet est enregistree dans les logs
- Le dashboard affiche le statut "objet en main"

## Notes
- La detection utilise la camera Intel RealSense (depth + RGB)
- Le bras a 4 DOF, la pince supporte max 500g
```

---

## Aide

### Erreurs courantes a eviter
- Use case trop technique ("Le serveur envoie une requete POST via WebSocket")
- Use case trop vague ("Gerer le robot")
- Melanger plusieurs actions dans un seul use case

### Structure dans le CDC

```markdown
## 3. Use cases

### Liste des use cases
| ID | Nom | Acteur | But |
|----|-----|--------|-----|
| UC-01 | ... | ... | ... |
| UC-02 | ... | ... | ... |
...

### UC-XX : [Nom] (detaille)
[Template complet ci-dessus]

### UC-YY : [Nom] (detaille)
[Template complet ci-dessus]
```
