---
name: Git Discipline
description: Travail Git propre et vérifiable — Conventional Commits, branchement, diffs vérifiés avant commit, séparation des changements. À utiliser pour tout commit, création de branche, merge, rebase, relecture de diff ou historique à nettoyer.
---

# Git Discipline

Objectif : un historique lisible, des commits unitaires, aucun change
non vérifié. Chaque commit raconte une chose et seulement une chose.

## Avant chaque commit

1. **Relire le diff en entier** (`git diff`, puis `git diff --staged`) :
   - rien d'inattendu (fichiers générés, secrets, chemins perso, `console.log` de debug)
   - rien d'oublié (fichier modifié non ajouté)
   - rien d'inventé : le diff correspond exactement à l'intention
2. **Vérifier l'état** : `git status` — pas de fichiers hors sujet stagués.
3. **Tester** si le projet a des tests/build : un commit vert, jamais un
   commit cassé sur une branche partagée.

## Message de commit (Conventional Commits)

```text
<type>(<portée>) : <description en impératif, minuscule, sans point>

<body optionnel : pourquoi, pas quoi (le diff montre quoi)
```

Types courants : `feat`, `fix`, `docs`, `refactor`, `test`, `chore`,
`perf`, `style`, `ci`.

Exemples :
```text
fix(auth) : corriger le rafraîchissement du token expiré
feat(api) : ajouter la pagination des listes
docs(readme) : documenter la variable DISABLE_CACHE
```

- Pas de `WIP`, `update`, `correction truc` sur une branche partagée.
- Un message décrit l'**intention**, jamais un résumé tautologique du
  diff (« modifie fichier »).

## Organisation

- **Un commit = une intention** : ne pas mélanger formatage + fonctionnalité.
  Refaire le formatage dans un commit séparé.
- **Branche courte** : travailler sur une branche, merger vite, ne pas
  laisser vivre une branche 3 semaines.
- **Avant merge/rebase** : re-relire le diff final, vérifier que la
  branche est à jour avec la cible.
- **Pas de `git add .` aveugle** sur un dépôt avec des fichiers hors
  sujet : ajouter fichier par fichier ou par motifs précis.

## Nettoyage

- Historique local non partagé : `commit --amend`, `rebase -i` permis.
- Historique **poussé** : ne pas force-push sans accord explicite
  (réécriture d'historique = risque pour les autres).
- Secrets accidentellement commis : les retirer du diff **et** prévenir
  l'utilisateur qu'une rotation est nécessaire (le retirer du dernier
  commit ne suffit pas si c'est poussé).

## Interdits

- Commiter des secrets (clés, tokens, `.env` réel)
- Commiter `node_modules/`, `dist/`, fichiers générés, `.DS_Store`
- Squash/rebase d'historique poussé sans demander
- Réponse du type « j'ai commité » sans avoir relu le diff

## Vérification finale

- [ ] `git diff` relu en entier
- [ ] Tests/build passent (ou mention *« non testé »*)
- [ ] Message conforme Conventional Commits et décrit l'intention
- [ ] Rien hors sujet stagué, pas de secret
- [ ] Un commit = une intention
