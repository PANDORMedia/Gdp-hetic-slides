# Conflits Git

## Objectif
Creer, comprendre et resoudre un conflit Git proprement.

## Consignes

### Mise en place

En binome :
1. Choisir un fichier commun (ex: `docs/cdc-technique.md`, section Architecture)
2. Chacun cree une branche depuis `main`

```bash
# Personne A
git checkout -b feature/conflict-a

# Personne B
git checkout -b feature/conflict-b
```

### Creer le conflit

Les deux personnes modifient la **meme section** du fichier :

**Personne A** : modifie la description de l'architecture (composants principaux)
**Personne B** : modifie aussi la description de l'architecture (differemment)

Chacun commit et push sa branche.

### Provoquer le conflit

1. Personne A cree une PR et merge en premier
2. Personne B cree sa PR -> conflit !

### Resoudre le conflit

```bash
# Personne B met a jour main
git checkout main
git pull origin main

# Rebase sa branche sur main
git checkout feature/conflict-b
git rebase main

# Resoudre le conflit dans l'editeur
# Chercher les marqueurs :
# <<<<<<< HEAD
# ... (version main)
# =======
# ... (votre version)
# >>>>>>> feature/conflict-b

# Apres resolution :
git add .
git rebase --continue
git push --force-with-lease origin feature/conflict-b
```

### Documenter

Ajouter dans `docs/conventions.md` une section "Gestion des conflits".

## Livrable
- 1 conflit resolu par equipe
- Section ajoutee dans `docs/conventions.md`

## Aide

### Strategie de resolution

1. **Lire les deux versions** : comprendre ce que chacun a voulu faire
2. **Discuter** : se mettre d'accord sur la version finale
3. **Fusionner intelligemment** : parfois c'est un mix des deux
4. **Tester** : verifier que le resultat est coherent
5. **Committer** : message clair ("resolve conflict on CDC architecture section")

### Commandes utiles

```bash
# Voir l'etat du rebase
git status

# Abandonner un rebase
git rebase --abort

# Voir les differences
git diff

# Force push securise (ne supprime pas le travail des autres)
git push --force-with-lease
```

### Template pour docs/conventions.md

```markdown
## Gestion des conflits

### Quand ca arrive
- Deux branches modifient le meme fichier, la meme zone

### Notre strategie
1. Toujours rebase sur main avant de push
2. Resoudre en binome (pas en solo silencieux)
3. Commit de resolution explicite
4. Re-review apres resolution

### Commandes
- `git rebase main` depuis sa branche
- Resoudre les marqueurs `<<<<<<<`
- `git add .` + `git rebase --continue`
- `git push --force-with-lease`
```
