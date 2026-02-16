# Use Cases NerdTickets

## Objectif
Ecrire 6 use cases et en detailler 2 critiques.

## Consignes

### Phase 1 : Lister 6 use cases

Format court pour chaque :

```
UC-XX : <Nom>
Acteur : <qui>
But : <1 phrase>
```

Exemples possibles :
- UC-01 : Creer un ticket
- UC-02 : Assigner un ticket
- UC-03 : Changer le statut d'un ticket
- UC-04 : Commenter un ticket
- UC-05 : Exporter un recap
- UC-06 : Filtrer les tickets par statut

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

## Fichiers a creer

```
docs/use-cases/UC-01.md
docs/use-cases/UC-02.md
... (un fichier par use case)
```

## Livrable
- PR #2 "Use-cases v1"
- Avec review

## Aide

### Exemple detaille : UC-01 Creer un ticket

```markdown
# UC-01 : Creer un ticket

## Acteurs
- Utilisateur (tout membre de l'equipe)

## But
Creer un nouveau ticket avec titre, description et priorite.

## Preconditions
- L'utilisateur est authentifie
- L'utilisateur a acces au projet

## Declencheur
L'utilisateur clique sur "Nouveau ticket"

## Scenario nominal
1. Le systeme affiche le formulaire de creation
2. L'utilisateur saisit le titre (obligatoire)
3. L'utilisateur saisit la description (optionnel)
4. L'utilisateur choisit la priorite (low/medium/high)
5. L'utilisateur valide
6. Le systeme cree le ticket avec statut "open"
7. Le systeme affiche le ticket cree

## Extensions / erreurs
- 2a. Titre vide : le systeme affiche "Titre obligatoire"
- 5a. Erreur serveur : le systeme affiche "Erreur, reessayez"

## Postconditions
- Un nouveau ticket existe avec statut "open"
- Le ticket est visible dans la liste

## Notes
- Le createur est automatiquement l'auteur du ticket
- Pas d'assignation a la creation (use case separe)
```

### Erreurs courantes a eviter
- Use case trop technique ("Le serveur envoie une requete POST")
- Use case trop vague ("Gerer les tickets")
- Melanger plusieurs actions dans un seul use case
