# CI legere & qualite

## Objectif
Mettre en place un garde-fou automatique ou process.

## Consignes

### Option A : Script lint docs (recommande)

Creer un script `scripts/lint-docs.sh` qui verifie :

```bash
#!/usr/bin/env bash
set -euo pipefail

errors=0

# Verifier que chaque use case a les sections obligatoires
for file in docs/use-cases/UC-*.md; do
  if [ ! -f "$file" ]; then continue; fi

  for section in "Acteurs" "But" "Scenario nominal"; do
    if ! grep -q "## $section" "$file" 2>/dev/null; then
      echo "ERREUR: $file manque la section '$section'"
      errors=$((errors + 1))
    fi
  done
done

# Verifier que vision.md existe et n'est pas vide
if [ ! -s "docs/vision.md" ]; then
  echo "ERREUR: docs/vision.md est vide ou absent"
  errors=$((errors + 1))
fi

# Verifier qu'il n'y a pas de fichiers .DS_Store
if find . -name ".DS_Store" | grep -q .; then
  echo "ERREUR: fichiers .DS_Store trouves"
  errors=$((errors + 1))
fi

if [ $errors -eq 0 ]; then
  echo "OK: toutes les verifications passent"
else
  echo "ECHEC: $errors erreur(s) trouvee(s)"
  exit 1
fi
```

### Option B : GitHub Action (si le temps le permet)

Creer `.github/workflows/lint.yml` :

```yaml
name: Lint docs
on: [pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: bash scripts/lint-docs.sh
```

### Option C : PR template solide

Ameliorer `.github/pull_request_template.md` avec une checklist stricte.

## Livrable
- 1 check automatique (script ou GitHub Action)
- OU un PR template solide

## Aide

### Tester le script localement

```bash
chmod +x scripts/lint-docs.sh
./scripts/lint-docs.sh
```

### Ajouter au .gitignore

```
.DS_Store
*.swp
*.swo
.env
node_modules/
```
