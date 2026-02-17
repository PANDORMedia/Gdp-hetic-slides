# CI legere & qualite

## Objectif
Mettre en place un garde-fou automatique ou process pour verifier la qualite du CDC.

## Consignes

### Option A : Script lint CDC (recommande)

Creer un script `scripts/lint-docs.sh` qui verifie :

```bash
#!/usr/bin/env bash
set -euo pipefail

errors=0

CDC="docs/cdc-technique.md"

# Verifier que le CDC existe et n'est pas vide
if [ ! -s "$CDC" ]; then
  echo "ERREUR: $CDC est vide ou absent"
  errors=$((errors + 1))
else
  # Verifier les sections obligatoires du CDC
  for section in "## 1. Vision" "## 2. Objectifs" "## 3. Use cases" "## 4. Architecture" "## 5. Diagrammes UML"; do
    if ! grep -q "$section" "$CDC" 2>/dev/null; then
      echo "ERREUR: $CDC manque la section '$section'"
      errors=$((errors + 1))
    fi
  done
fi

# Verifier que le README existe et n'est pas vide
if [ ! -s "README.md" ]; then
  echo "ERREUR: README.md est vide ou absent"
  errors=$((errors + 1))
fi

# Verifier qu'il n'y a pas de fichiers .DS_Store
if find . -name ".DS_Store" | grep -q .; then
  echo "ERREUR: fichiers .DS_Store trouves"
  errors=$((errors + 1))
fi

# Verifier qu'il y a au moins 1 diagramme UML
if [ ! -d "uml" ] || [ -z "$(ls -A uml/ 2>/dev/null)" ]; then
  echo "ATTENTION: dossier uml/ vide — pensez a ajouter vos diagrammes"
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
