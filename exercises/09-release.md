# Release & Versioning

## Objectif
Creer une premiere release propre avec tag, changelog et release note.

## Consignes

### Phase 1 : CHANGELOG.md

Creer `CHANGELOG.md` a la racine du repo :

```markdown
# Changelog

Toutes les modifications notables de ce projet.

Format base sur [Keep a Changelog](https://keepachangelog.com/).

## [0.0.1] - YYYY-MM-DD

### Added
- Vision, objectifs et personas (PR #1)
- 6 use cases dont 2 detailles (PR #2)
- Diagrammes UML : use case, sequence, etat (PR #3)
- Architecture technique (PR #4)
- Conventions Git et collaboration
- Checklist de review
- Gestion des conflits documentee

### Fixed
- Rien (premiere version)

### Changed
- Rien (premiere version)
```

### Phase 2 : Tag v0.0.1

```bash
# S'assurer d'etre sur main a jour
git checkout main
git pull origin main

# Creer le tag
git tag -a v0.0.1 -m "v0.0.1 - CDC technique v1"

# Pousser le tag
git push origin v0.0.1
```

### Phase 3 : Release note

Sur GitHub : Releases -> "Create a new release"

- Tag : `v0.0.1`
- Title : `v0.0.1 - CDC technique v1`
- Description :

```markdown
## Ce que contient cette version

### Cahier des Charges technique
- Vision et personas du projet
- 6 use cases (dont 2 detailles avec scenarios)
- Architecture technique avec composants
- 3 diagrammes UML (use case, sequence, etat)
- Stack technique justifiee

### Process equipe
- Conventions Git (branches, commits, PR)
- Checklist de review
- Guide de resolution de conflits

### Prochaines etapes
- Valider le CDC avec les encadrants
- Commencer les POC dans `research/`
- Demarrer l'implementation (v0.1.0)
```

### Phase 4 (option) : Branche release

```bash
# Creer la branche release
git checkout -b release/0.0.1
git push -u origin release/0.0.1

# Merger vers main
git checkout main
git merge release/0.0.1
git push origin main
```

## Livrable
- `CHANGELOG.md` a jour
- Tag `v0.0.1`
- Release note sur GitHub

## Aide

### Semantic Versioning (SemVer)

```
MAJOR.MINOR.PATCH

0.0.1 = premier draft (CDC technique)
0.1.0 = premiere version fonctionnelle
0.2.0 = ajout de fonctionnalites
1.0.0 = version stable, prete pour la prod
```

> **Pourquoi v0.0.1 et pas v0.1.0 ?** On est encore au stade du CDC, pas d'un produit fonctionnel. Le PATCH sert a marquer les iterations de documentation.

### Voir les tags

```bash
git tag -l
git show v0.0.1
```
