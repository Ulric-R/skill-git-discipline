# Git Discipline

> Skill OpenCode pour un travail Git propre et vérifiable — commits conventionnels, diffs vérifiés, historique lisible.

**ID** : `git-discipline` · **Portée** : globale (`~/.config/opencode/skills/`) · **Langue** : FR

## Ce que fait le skill

- **Avant chaque commit** : relire le diff en entier, vérifier `git status`, tester — un commit cassé ne part jamais sur une branche partagée
- **Conventional Commits** : `<type>(<portée>) : <description en impératif>` — le message décrit l'intention, pas un résumé tautologique du diff
- **Organisation** : un commit = une intention, branches courtes, pas de `git add .` aveugle
- **Nettoyage** : amend/rebase permis en local, pas de force-push sans accord, secrets = rotation nécessaire (pas seulement retrait du dernier commit)

## Interdits

Secrets commités, `node_modules/`/`dist/`, réécriture d'historique poussé sans demander, « j'ai commité » sans avoir relu le diff.

## Structure

```text
git-discipline/
└── SKILL.md              # Workflow, message, organisation, interdits, checklist
```

## Déclenchement

- **Automatique** : tout commit, branche, merge, rebase, relecture de diff
- **Manuel** : `@git-discipline`

## Vérification

- [ ] Diff relu en entier
- [ ] Tests exécutés (ou *« non testé »* mentionné)
- [ ] Message conforme et intensionnel
- [ ] Aucun secret ni fichier hors sujet stagué

## Skills liés

- `pre-ship-review` (checklist go/no-go finale), `anti-dream` (le diff = preuve)
