# Workflow propre : Issues -> PR -> Done

## Objectif
Relier gestion de projet et Git avec des issues completes.

## Consignes

### Phase 1 : Creer 2 issues

Chaque equipe choisit 2 nouvelles issues parmi :
- Ecrire un use case manquant
- Completer un diagramme UML
- Ameliorer la documentation
- Ajouter un diagramme d'etat

Pour chaque issue, ajouter des **criteres d'acceptation** (DoD) :

```markdown
## Description
[Ce qu'il faut faire]

## Criteres d'acceptation
- [ ] Le fichier est cree dans le bon dossier
- [ ] Le format respecte le template
- [ ] La PR reference cette issue
- [ ] 1 review minimum
```

### Phase 2 : Travailler les issues

Pour chaque issue :
1. Assigner a un membre
2. Creer la branche `feature/<id>-<slug>`
3. Travailler + commits propres
4. PR qui :
   - Reference l'issue (`Fixes #12`)
   - Decrit le changement
   - Propose comment tester/relire

### Phase 3 : Review et merge

- Review croisee
- Verifier les criteres d'acceptation
- Merge

## Template de PR

```markdown
## Description
Ajout du use case UC-04 "Commenter un ticket".

## Issue liee
Fixes #12

## Changements
- Nouveau fichier `docs/use-cases/UC-04.md`
- Scenario nominal + 2 extensions

## Comment relire
1. Verifier la coherence avec la vision
2. Verifier le format (template use case)
3. Verifier que les extensions sont realistes

## Checklist
- [x] Issue liee
- [x] Petit perimetre
- [x] Commits propres
- [x] Docs a jour
```

## Livrable
- 2 PR mergees par equipe
- Historique propre (pas de "merge main into feature")

## Aide

### Referencer une issue dans une PR

```
Fixes #12     -> ferme l'issue au merge
Closes #12    -> idem
Resolves #12  -> idem
Refs #12      -> reference sans fermer
```

### Historique propre

```bash
# Avant de creer la PR, rebaser sur main
git checkout main
git pull
git checkout feature/mon-sujet
git rebase main

# Si conflit, resoudre puis :
git add .
git rebase --continue
```
