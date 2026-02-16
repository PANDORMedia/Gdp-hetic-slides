# Mise en place du repo NerdTickets

## Objectif
Creer le repo de votre equipe et faire un premier commit.

## Consignes

1. **Un membre** cree le repo sur GitHub (public ou prive)
2. Les autres **fork** ou **clone** le repo
3. Verifier la structure initiale :

```
/docs/vision.md
/docs/use-cases/
/uml/
.github/pull_request_template.md
```

4. Chaque membre fait un commit `init: add team member <prenom>`

## Structure du repo

```
nerd-tickets/
  docs/
    vision.md          (vide pour l'instant)
    use-cases/         (dossier vide)
  uml/                 (dossier vide)
  .github/
    pull_request_template.md
  README.md
```

## Template PR (minimal)

```markdown
## Description
<!-- Qu'est-ce que cette PR fait ? -->

## Issue liee
<!-- Fixes #XX -->

## Checklist
- [ ] Le but est clair
- [ ] Petit perimetre
- [ ] Pas de fichier inutile
```

## Livrable
- 1 commit initial par membre
- Repo pret avec la structure ci-dessus

## Aide

Si vous n'avez pas Git installe :
```bash
# macOS
brew install git

# Ubuntu
sudo apt install git

# Windows
# Telecharger depuis https://git-scm.com
```

Commandes de base :
```bash
git clone <url>
git add .
git commit -m "init: add team member Alice"
git push origin main
```
