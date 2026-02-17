# Mise en place du monorepo

## Objectif
Creer le repo de votre equipe et faire un premier commit avec la structure monorepo.

## Consignes

1. **Un membre** cree le repo sur GitHub (public ou prive)
   - Nom suggere : `flipper` ou `robot-assistance` (selon votre projet)
2. Les autres **clone** le repo (pas de fork, vous travaillez dans le meme repo)
3. Mettre en place la structure monorepo (voir ci-dessous)
4. Chaque membre fait un commit `init: add team member <prenom>`

## Structure du monorepo

```
mon-projet/
  docs/
    cdc-technique.md      (fichier principal du CDC — vide pour l'instant)
  apps/                    (code source — plus tard)
  research/                (benchmarks & POC — plus tard)
  .github/
    pull_request_template.md
  README.md
```

> **Note :** les dossiers `apps/` et `research/` seront utilises quand vous commencerez a coder. Pour l'instant, ajoutez juste un fichier `.gitkeep` dans chacun pour que Git les suive.

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
- Repo pret avec la structure monorepo ci-dessus
- README.md avec le nom du projet et les membres de l'equipe

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

### Creer les dossiers vides

```bash
mkdir -p docs apps research .github
touch docs/cdc-technique.md
touch apps/.gitkeep research/.gitkeep
```
