# Release & Versioning

## Objectif
Creer une premiere release propre avec tag, changelog et release note.

## Consignes

### Phase 1 : CHANGELOG.md

Creer `CHANGELOG.md` a la racine du repo :

```markdown
# Changelog

Toutes les modifications notables de NerdTickets.

Format base sur [Keep a Changelog](https://keepachangelog.com/).

## [0.1.0] - YYYY-MM-DD

### Added
- Vision et personas (PR #1)
- 6 use cases dont 2 detailles (PR #2)
- Diagrammes UML : use case, sequence, etat (PR #3)
- Conventions Git et collaboration (PR #4)
- Checklist de review (PR #5)
- Gestion des conflits documentee

### Fixed
- Rien (premiere version)

### Changed
- Rien (premiere version)
```

### Phase 2 : Tag v0.1.0

```bash
# S'assurer d'etre sur main a jour
git checkout main
git pull origin main

# Creer le tag
git tag -a v0.1.0 -m "v0.1.0 - MVP documentation NerdTickets"

# Pousser le tag
git push origin v0.1.0
```

### Phase 3 : Release note

Sur GitHub : Releases -> "Create a new release"

- Tag : `v0.1.0`
- Title : `v0.1.0 - MVP Documentation`
- Description :

```markdown
## Ce que contient cette version

### Documentation produit
- Vision et personas du projet NerdTickets
- 6 use cases (dont 2 detailles avec scenarios)
- 3 diagrammes UML (use case, sequence, etat)

### Process equipe
- Conventions Git (branches, commits, PR)
- Checklist de review
- Guide de resolution de conflits

### Prochaines etapes
- Implementer l'API (v0.2.0)
- Ajouter les tests (v0.3.0)
```

### Phase 4 (option) : Branche release

```bash
# Creer la branche release
git checkout -b release/0.1.0
git push -u origin release/0.1.0

# Merger vers main
git checkout main
git merge release/0.1.0
git push origin main
```

## Livrable
- `CHANGELOG.md` a jour
- Tag `v0.1.0`
- Release note sur GitHub

## Aide

### Semantic Versioning (SemVer)

```
MAJOR.MINOR.PATCH

0.1.0 = premiere version, fonctionnalites de base
0.2.0 = ajout de fonctionnalites
0.2.1 = correction de bug
1.0.0 = version stable, prete pour la prod
```

### Voir les tags

```bash
git tag -l
git show v0.1.0
```
