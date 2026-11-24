# AGENTS.md

## Projet

ocean-team est l'application NestJS qui sert à gérer la communauté Ocean Tech.

## Stack et structure

- **Framework** : [NestJS](https://docs.nestjs.com) v12, TypeScript en mode `strict`.
- **Runtime** : Node.js 20 minimum (22 LTS recommandé).
- **Gestionnaire de paquets** : npm **11 ou plus** (`npm install` plante avec npm 10 ; sinon `npx npm@11 install`).
- **Tests** : [Vitest](https://vitest.dev) ; e2e avec Supertest.
- **Lint / format** : [oxlint](https://oxc.rs) (type-aware) et Prettier.

```
src/
  main.ts                  # bootstrap : crée l'app, écoute sur PORT (3000 par défaut)
  app.module.ts            # module racine, importe les autres modules
  app.controller.ts        # exemple de contrôleur
  app.service.ts           # exemple de service
  app.controller.spec.ts   # test unitaire, à côté du code
test/
  app.e2e-spec.ts          # tests end-to-end
```

## Commandes

Les agents doivent faire passer `build`, `test`, `test:e2e` et `lint` avant de proposer une PR.

```bash
npm install            # installer les dépendances (npm >= 11)
npm run start:dev      # lancer en local avec rechargement
npm run build          # compiler dans dist/
npm test               # tests unitaires (Vitest)
npm run test:e2e       # tests end-to-end
npm run lint           # oxlint
npm run format         # Prettier sur src/ et test/
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
