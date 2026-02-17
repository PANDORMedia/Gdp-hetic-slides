# Workflow propre : Issues -> PR -> Done

## Objectif
Relier gestion de projet et Git avec des issues completes.

## Consignes

### Phase 1 : Creer 2 issues

Chaque equipe choisit 2 nouvelles issues parmi :
- Ajouter une section manquante au CDC (stack technique, risques, roadmap...)
- Completer un diagramme UML
- Ameliorer une section existante du CDC
- Ajouter un diagramme d'etat ou de sequence

Pour chaque issue, ajouter des **criteres d'acceptation** (DoD) :

```markdown
## Description
[Ce qu'il faut faire]

## Criteres d'acceptation
- [ ] La section est ajoutee dans docs/cdc-technique.md
- [ ] Le format respecte la structure du CDC
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
Ajout de la section "Stack technique" au CDC.

## Issue liee
Fixes #12

## Changements
- Nouvelle section 6 dans `docs/cdc-technique.md`
- Justification des choix technologiques

## Comment relire
1. Verifier la coherence avec l'architecture (section 4)
2. Verifier que chaque choix est justifie
3. Verifier que les alternatives ont ete mentionnees

## Checklist
- [x] Issue liee
- [x] Petit perimetre
- [x] Commits propres
- [x] CDC a jour
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
