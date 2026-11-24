# AGENTS.md

Instructions pour les agents de code (Claude Code, Codex, Cursor, Copilot…) qui travaillent sur ce dépôt.
Ce fichier est la source de vérité unique ; les fichiers spécifiques à un outil (`CLAUDE.md`, etc.) doivent simplement y renvoyer.

## Projet

- **Nom** : ocean-team
- **Organisation** : [ocean-tech-community](https://github.com/ocean-tech-community)
- **Objectif** : _à compléter — décrire en 2-3 phrases ce que fait le projet et pour qui._
- **Type** : API backend NestJS.

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

## NestJS : points d'attention

- **Version récente** : Nest 12 est probablement plus récent que ce que connaît l'agent. Vérifier dans la doc à jour : https://docs.nestjs.com/llms.txt (une page markdown par chapitre).
- **ESM uniquement** : le projet est en `"type": "module"`.
  - Les imports relatifs se terminent par `.js` (`import { AppService } from './app.service.js'`).
  - `__dirname` n'existe pas : utiliser `import.meta.dirname`.
- **Tests Vitest** : mocks avec `vi.fn()` / `vi.spyOn()`, jamais `jest.fn()`. Modules de test avec `Test.createTestingModule` de `@nestjs/testing`.
- **Organisation** : une fonctionnalité = un module (`*.module.ts`), avec son contrôleur et son service, importé dans `AppModule`. Utiliser la CLI pour générer : `npx nest g resource <nom>` (ou `module`, `controller`, `service`).
- **Paquets officiels d'abord** : avant d'ajouter une librairie tierce ou d'écrire la sienne, vérifier s'il existe un paquet `@nestjs/*` (config, base de données, swagger, auth, throttler, schedule, queues…).
- **Validation** : schémas Zod (ou autre lib Standard Schema) avec `StandardSchemaValidationPipe` et `@Body({ schema })`. `class-validator` reste possible via `ValidationPipe`.
- **Configuration** : variables d'environnement dans `.env` (ignoré par Git). Documenter toute nouvelle variable dans un `.env.example`.
- **Télémétrie** : `@nestjs/observe` est branché par défaut dans `app.module.ts` et n'envoie rien tant que `OBSERVE_APP_KEY` n'est pas défini. Ne pas le configurer ni ajouter de clés sans accord de l'équipe.

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
