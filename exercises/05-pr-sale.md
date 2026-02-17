# PR "sale" a reparer

## Objectif
Analyser une PR problematique et etablir une checklist de review.

## Consignes

### La PR problematique

Voici ce qui ne va pas dans cette PR :

1. **1 seul commit** avec le message "wip"
2. **Fichier modifie partout** : cdc-technique.md, 2 diagrammes UML, le README, les conventions
3. **Message de PR vague** : "update stuff"
4. **Pas d'issue liee**
5. **Fichiers non lies** : un `.DS_Store` traine

### Phase 1 : Identifier les problemes

En classe entiere, listez tout ce qui ne va pas.

### Phase 2 : Ecrire la checklist

Par equipe, redigez `docs/review-checklist.md`.

### Phase 3 : Simuler la review

- Demander des changements sur la PR
- L'auteur corrige (squash/rewrite si besoin)
- Re-review et merge

## Template review-checklist.md

```markdown
# Checklist de Review

## Avant de reviewer
- [ ] L'issue liee est claire
- [ ] La PR a une description

## Contenu
- [ ] Petit perimetre (1 sujet = 1 PR)
- [ ] Pas de fichier inutile (.DS_Store, .env, etc.)
- [ ] Nommage coherent (fichiers, variables)

## Qualite
- [ ] Docs a jour si necessaire
- [ ] Diagrammes coherents avec les use cases
- [ ] Aucun commit "WIP" ou "fix" sans contexte

## Commits
- [ ] Messages lisibles (Conventional Commits)
- [ ] 1 commit = 1 intention
- [ ] Pas de commit de merge inutile

## Approbation
- [ ] Au moins 1 review
- [ ] Tous les changements demandes sont resolus
```

## Livrable
- `docs/review-checklist.md` complete

## Aide

### Exemples de commentaires de review

**Mauvais** :
- "C'est pas bien"
- "Change ca"

**Bon** :
- "Ce commit melange 2 sujets (section CDC + diagramme). Peux-tu separer en 2 commits ?"
- "Le message 'wip' n'est pas assez descriptif. Suggestion : 'docs: add architecture section to CDC'"
- "Ce fichier .DS_Store ne devrait pas etre versionne. Ajoute-le au .gitignore"
