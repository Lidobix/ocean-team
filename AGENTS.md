# AGENTS.md

Instructions pour les agents de code (Claude Code, Codex, Cursor, Copilot…) qui travaillent sur ce dépôt.
Ce fichier est la source de vérité unique ; les fichiers spécifiques à un outil (`CLAUDE.md`, etc.) doivent simplement y renvoyer.

## Projet

- **Nom** : ocean-team
- **Organisation** : [ocean-tech-community](https://github.com/ocean-tech-community)
- **Objectif** : _à compléter — décrire en 2-3 phrases ce que fait le projet et pour qui._

## Stack et structure

_À compléter dès que le code arrive._

- Langage(s) / framework(s) :
- Gestionnaire de paquets :
- Arborescence principale :

## Commandes

_À compléter. Les agents doivent exécuter ces commandes avant de proposer une PR._

```bash
# Installer les dépendances
# Lancer en local
# Lancer les tests
# Lint / format
```

## Conventions

- **Langue** : documentation, issues et PR en français ; noms de code (variables, fonctions, fichiers) en anglais.
- **Branches** : `feat/…`, `fix/…`, `docs/…`, `chore/…` à partir de `main`.
- **Commits** : [Conventional Commits](https://www.conventionalcommits.org/fr/) (`feat: …`, `fix: …`, `docs: …`, `chore: …`).
- **PR** : petites et ciblées, avec une description du *pourquoi* et de la façon de tester.
- Ne jamais pousser directement sur `main`.

## Règles pour les agents

- Lire ce fichier et le `README` avant toute modification.
- Préférer des changements minimaux et cohérents avec le style existant.
- Ajouter ou mettre à jour les tests quand le comportement change.
- Ne jamais committer de secrets (`.env`, clés API, identifiants).
- En cas de doute sur une décision structurante, demander plutôt que deviner.
- Mettre à jour ce fichier quand une convention, une commande ou la structure change.
