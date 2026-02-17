# Collaboration Git : simulation

## Objectif
Pratiquer le workflow Git en equipe avec 3 issues concretes liees au CDC.

## Consignes

### Issues a traiter

Votre equipe doit traiter ces 3 issues :

**Issue 1** : "CDC : section architecture technique"
- Ajouter la section 4 (Architecture) dans `docs/cdc-technique.md`
- Decrire les composants principaux et leurs interactions

**Issue 2** : "UML : diagramme de sequence UC principal"
- Creer le diagramme de sequence de votre UC le plus critique dans `uml/`

**Issue 3** : "Docs : ajouter conventions equipe"
- Creer `docs/conventions.md` avec les regles Git et code de l'equipe

### Workflow pour chaque issue

1. **Creer l'issue** sur GitHub (titre + description)
2. **Creer la branche** : `feature/<id>-<slug>`
   ```bash
   git checkout -b feature/1-cdc-architecture
   ```
3. **Commits propres** (Conventional Commits)
   ```bash
   git commit -m "docs: add architecture section to CDC"
   ```
4. **Push + PR**
   ```bash
   git push -u origin feature/1-cdc-architecture
   ```
5. **Review croisee** : un autre membre review la PR
6. **Merge** apres approbation

### Regles imposees

- `main` protegee : interdit de push direct
- Branches : `feature/<id>-<slug>`
- PR obligatoire + 1 review minimum
- Commits lisibles (Conventional Commits)

## Conventions Commits

```
feat: ...    -> nouvelle fonctionnalite
fix: ...     -> correction de bug
docs: ...    -> documentation
refactor: ... -> restructuration sans changement fonctionnel
```

1 commit = 1 intention
Message : verbe + objet ("docs: add review checklist")

## Livrable
- 3 PR mergees
- `docs/conventions.md` avec les regles de votre equipe

## Aide

### Template pour docs/conventions.md

```markdown
# Conventions Git - Equipe [nom]

## Branches
- `main` : branche stable, protegee
- `feature/<id>-<slug>` : branches de travail

## Commits
- Format : `type: description courte`
- Types : feat, fix, docs, refactor
- 1 commit = 1 intention

## Pull Requests
- Toujours liee a une issue
- 1 review minimum avant merge
- Petit perimetre (pas de PR "tout le projet")

## Review
- Verifier la coherence avec l'issue
- Verifier le nommage
- Commenter de maniere constructive
```

### Commandes utiles

```bash
# Creer une branche
git checkout -b feature/1-mon-sujet

# Voir les branches
git branch -a

# Pousser une branche
git push -u origin feature/1-mon-sujet

# Revenir sur main
git checkout main
git pull origin main
```
