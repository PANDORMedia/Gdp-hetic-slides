# Vision & Personas NerdTickets

## Objectif
Definir la vision produit, les objectifs, non-objectifs et personas.

## Consignes

### 1. Vision (1 phrase)
Ecrivez UNE phrase qui resume ce que NerdTickets fait et pour qui.

Exemple : "NerdTickets permet a une petite equipe de gerer ses tickets de developpement sans quitter son terminal."

### 2. Objectifs (3)
Qu'est-ce que le produit DOIT faire ?

Exemples :
- Creer et assigner des tickets
- Suivre le statut d'un ticket (open / in-progress / done)
- Commenter un ticket

### 3. Non-objectifs (3)
Qu'est-ce que le produit ne fait PAS (pour cette version) ?

Exemples :
- Pas de notifications en temps reel
- Pas d'integration Slack/Discord
- Pas de gestion de sprints

### 4. Personas (2)
Format court :

```
Persona : <Prenom>
Role : <role dans l'equipe>
Besoin principal : <1 phrase>
Frustration : <1 phrase>
```

## Fichier a creer

`docs/vision.md`

## Livrable
- PR #1 "Vision + Personas"
- Review obligatoire par une autre equipe (si possible)
- Au moins 1 approbation avant merge

## Aide

Structure suggeree pour `docs/vision.md` :

```markdown
# Vision NerdTickets

## Vision
[1 phrase]

## Objectifs
1. ...
2. ...
3. ...

## Non-objectifs
1. ...
2. ...
3. ...

## Personas

### Persona 1 : Alice
- Role : Dev frontend
- Besoin : voir rapidement les tickets qui lui sont assignes
- Frustration : trop d'outils differents

### Persona 2 : Bob
- Role : Tech Lead
- Besoin : avoir une vue d'ensemble de l'avancement
- Frustration : pas de visibilite sur qui fait quoi
```
