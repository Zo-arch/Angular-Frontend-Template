# example-project

Template Angular mínimo (Bun). Substitua `example-project` pelo nome do seu projeto.

## Uso

```bash
bun install
bun run dev
```

Build: `bun run build`

## Estrutura (feature-based)

Cada feature é isolada; código compartilhado fica em `shared/`. Pastas vazias usam `.gitkeep` só para documentar o layout.

```text
src/
├── app/                    # Bootstrap, rotas, providers
│   └── providers/
├── features/
│   ├── home/
│   │   ├── components/
│   │   ├── services/
│   │   ├── models/
│   │   └── index.ts        # API pública da feature
│   └── auth/
│       └── …
├── shared/
│   ├── ui/                 # Wrappers da lib de UI (quando houver)
│   ├── components/
│   ├── services/
│   ├── lib/
│   ├── models/
│   └── constants/
├── assets/
│   ├── images/
│   └── icons/
├── styles/
├── index.html
└── main.ts
public/                     # Estáticos na raiz do build (favicon, etc.)
```

### Feature

```text
features/[nome]/
├── components/
├── services/
├── models/
└── index.ts
```

Exporte só o que outras partes do app podem importar pelo `index.ts`. Registre rotas em `src/app/app.routes.ts`.

### Shared

- `shared/ui` — adapters da biblioteca de UI escolhida
- `shared/components` — layout, header, etc.
- `shared/services` — HTTP, sessão, etc.
- `shared/lib` — utilitários
- `shared/models` — tipos compartilhados
- `shared/constants` — rotas, configs

## Path aliases

| Alias | Caminho |
|-------|---------|
| `@/*` | `src/*` |
| `@/shared/*` | `src/shared/*` |
| `@/features/*` | `src/features/*` |

```ts
import { routes } from '@/shared/constants/routes';
import { HomePage } from '@/features/home';
```
