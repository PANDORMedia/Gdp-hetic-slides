# Sprint CDC technique

## Objectif
Compiler votre Cahier des Charges technique complet, le faire relire par une autre equipe, et preparer la presentation finale (10 min).

## Consignes

### Phase 1 : Compiler le CDC (30 min)

Votre `docs/cdc-technique.md` doit contenir **au minimum** ces sections :

1. **Vision**
2. **Objectifs et perimetre**
3. **Use cases**
4. **Architecture technique**
5. **Diagrammes UML**
6. **Stack technique**
7. **Risques et contraintes**
8. **Conventions equipe**
9. **Roadmap et questions ouvertes**

> Cette liste n'est pas exhaustive. Si votre projet necessite d'autres sections (securite, accessibilite, protocoles de communication, modele de donnees...), ajoutez-les.

Verifiez que tout y est, completez ce qui manque. Voici ce qu'on attend pour chaque section :

---

#### 1. Vision

Une phrase. Qui, quoi, pourquoi.

```markdown
Flipper est un flipper virtuel multijoueur qui combine une simulation
physique realiste (Three.js/Cannon.js) avec des controleurs physiques
(ESP32) pour offrir une experience arcade moderne jouable sur 3 ecrans.
```

#### 2. Objectifs et perimetre

3-5 objectifs, 3 non-objectifs, 2 personas.

```markdown
### Objectifs
1. Simuler une table de flipper avec physique realiste
2. Synchroniser 3 ecrans en temps reel via WebSocket
3. Permettre le controle via web ET controleurs physiques (ESP32)

### Non-objectifs
1. Pas de mode multijoueur en ligne
2. Pas d'editeur de table personnalise

### Personas
**Lea**, 22 ans, etudiante dev web — veut un projet fun combinant front et IoT.
```

#### 3. Use cases

Tableau recapitulatif + 2 use cases detailles (scenario nominal, extensions, postconditions).

```markdown
| ID | Nom | Acteur | But |
|----|-----|--------|-----|
| UC-01 | Lancer une partie | Joueur | Demarrer une nouvelle partie |
| UC-02 | Connecter controleur | Joueur | Associer un ESP32 |
| ...  | ... | ... | ... |

### UC-01 : Lancer une partie (detaille)
Acteurs : Joueur (via web ou ESP32)
Preconditions : Serveur WS demarre, au moins 1 ecran connecte
Scenario nominal :
1. Le systeme reinitialise le score a 0
2. La bille est placee dans le lanceur
3. ...
Extensions :
- 1a. Partie en cours → confirmation avant reinitialisation
```

#### 4. Architecture technique

Schema des composants et leurs interactions. Texte ou ASCII, peu importe, tant que c'est clair.

```markdown
┌──────────┐  WebSocket  ┌──────────┐
│ UI Web   │◄───────────►│ Serveur  │
│ (Three.js)│            │ (Node.js)│
└──────────┘             └────┬─────┘
                              │ Serial
                         ┌────▼─────┐
                         │  ESP32   │
                         └──────────┘
```

#### 5. Diagrammes UML

Liens ou contenu des diagrammes (use case, sequence, etat). Au minimum 3.

```markdown
(voir uml/use-case-diagram.puml)
(voir uml/sequence-lancer-partie.puml)
(voir uml/state-partie.puml)
```

#### 6. Stack technique

Tableau avec justification des choix ET alternatives ecartees.

```markdown
| Composant | Techno | Justification |
|-----------|--------|---------------|
| Playfield | Three.js + Cannon.js | Rendu 3D web + physique realiste |
| Serveur | Node.js + ws | Event-driven, bon pour le temps reel |

Alternatives ecartees :
- Socket.io → trop lourd pour notre besoin
- Unity → pas web-native
```

#### 7. Risques et contraintes

Tableau de risques avec probabilite, impact et mitigation. Plus les contraintes du projet.

```markdown
| Risque | Probabilite | Impact | Mitigation |
|--------|-------------|--------|------------|
| Latence WebSocket trop haute | Moyenne | Fort | POC reseau S2, fallback local |
| Physique pas assez realiste | Haute | Moyen | Tests des S2, ajuster params |

### Contraintes
- Delai : 10 semaines
- Equipe : 4 personnes
- Materiel : 3 ecrans, 1 ESP32, composants (~50€)
```

#### 8. Conventions equipe

Regles Git, nommage, review.

```markdown
- Branches : feature/<id>-<slug>
- Commits : Conventional Commits (feat:, fix:, docs:)
- PR obligatoire + 1 review minimum
- Conflits : rebase sur main, resolution en binome
```

#### 9. Roadmap et questions ouvertes

Planning macro + liste de ce qu'on ne sait pas encore.

```markdown
| Phase | Semaines | Objectif |
|-------|----------|----------|
| CDC + Setup | S1 | CDC valide, monorepo pret |
| POC | S2-S3 | Valider les choix techniques |
| MVP | S4-S8 | Fonctionnalites coeur |
| Polish | S9-S10 | Integration, demo |

### Questions ouvertes
- [ ] Cannon.js ou Ammo.js pour la physique ?
- [ ] BLE ou Serial pour l'ESP32 ?
- [ ] Faut-il un systeme de replay ?
```

> Les questions ouvertes sont **normales et attendues**. C'est la preuve que vous avez identifie ce que vous ne savez pas encore.

---

### Phase 2 : Relecture croisee (15 min)

1. Echangez votre CDC avec une **autre equipe**
2. Chaque equipe lit et commente (directement sur la PR ou sur papier)
3. Criteres de relecture :
   - [ ] Les 9 sections sont presentes
   - [ ] La vision est claire en 1 phrase
   - [ ] Les use cases sont du point de vue utilisateur (pas technique)
   - [ ] L'architecture est coherente avec les use cases
   - [ ] Les risques sont realistes
   - [ ] La roadmap est realiste vu le temps disponible

### Phase 3 : PR finale (10 min)

1. Integrer les retours de la relecture
2. Creer la PR finale : `CDC technique v1 complet`
3. Review par un membre de l'equipe
4. Merge sur `main`

### Phase 4 : Presentation (10 min par equipe)

1. **Votre projet en 1 phrase** (vision)
2. **2 use cases cles** (les plus importants)
3. **1 diagramme UML** (le plus parlant)
4. **Architecture** (composants principaux)
5. **Risques identifies** (top 3)
6. **Questions ouvertes** (ce que vous devez encore valider)

> Montrez directement votre repo et votre CDC sur GitHub. Pas besoin de slides supplementaires.

## Livrable
- PR finale "CDC technique v1 complet" mergee sur `main`
- Presentation prete (10 min)
- Tag `v0.0.1`
