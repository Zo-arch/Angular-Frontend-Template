# example-project

Frontend Angular template genérico para aplicações SAAS, construído com Angular, TypeScript e SCSS.

Sem biblioteca de UI fixa — escolha (Taiga UI, Angular Material, PrimeNG, etc.) quando for criar o projeto real.

## Template Instructions

Este repositório é um template de projeto. Para usar em um novo projeto:

1. Clone este repositório
2. Busque por `example-project` (Ctrl+F / Cmd+F) em todos os arquivos
3. Substitua todas as ocorrências pelo nome do seu projeto
4. Atualize as variáveis de ambiente a partir do arquivo `env.example`
5. Personalize branding e, se quiser, adicione a lib de UI escolhida

## Quick Start

### Pré-requisitos

- Node.js (v18 ou superior; v20 LTS recomendado)
- npm

### Instalação

```bash
# Instalar dependências
npm install

# Copiar arquivo de ambiente
cp env.example .env

# Editar .env com suas configurações
```

### Executar em Desenvolvimento

```bash
npm start
# equivalente a: ng serve
```

O servidor de desenvolvimento estará rodando em http://localhost:4200

### Build para Produção

```bash
npm run build

# Preview do build (após o build)
npx http-server dist/example-project/browser
```

## Estrutura do Projeto

Arquitetura baseada em features (Feature-based Architecture):

```text
example-project/
├── public/                     # Arquivos estáticos públicos
├── src/
│   ├── app/                    # Configuração da aplicação
│   │   ├── app.component.ts    # Componente raiz (router-outlet)
│   │   ├── app.config.ts       # Providers (Router, etc.)
│   │   ├── app.routes.ts       # Rotas
│   │   └── providers/          # Providers adicionais (futuro)
│   │
│   ├── features/               # Funcionalidades isoladas
│   │   ├── home/
│   │   │   ├── components/
│   │   │   ├── services/
│   │   │   ├── models/
│   │   │   └── index.ts        # Exports públicos
│   │   └── auth/
│   │       ├── components/
│   │       ├── services/
│   │       ├── models/
│   │       └── index.ts
│   │
│   ├── shared/                 # Código compartilhado
│   │   ├── ui/                 # Slot para componentes da lib de UI
│   │   ├── components/         # Componentes reutilizáveis
│   │   ├── services/           # Serviços compartilhados
│   │   ├── lib/                # Utilitários
│   │   ├── models/             # Models compartilhados
│   │   └── constants/          # Constantes (rotas, configs)
│   │
│   ├── assets/
│   │   ├── images/
│   │   └── icons/
│   │
│   ├── styles/
│   │   └── styles.scss         # Estilos globais
│   │
│   ├── index.html
│   └── main.ts                 # Entry point
│
├── env.example
├── package.json
├── tsconfig.json
└── angular.json
```

## Arquitetura

### Feature-based

Cada feature é auto-contida:

```text
features/[feature-name]/
├── components/     # Componentes específicos
├── services/       # Lógica / API
├── models/         # Models específicos
├── [Feature]Page.ts  # Página principal (quando implementar)
└── index.ts        # Barrel exports
```

### Shared

Código compartilhado entre features:

- `shared/ui/` — componentes da lib de UI (quando adicionar)
- `shared/components/` — Header, Footer, layouts, etc.
- `shared/services/` — HTTP helpers, auth session, etc.
- `shared/lib/` — utilitários
- `shared/models/` — models compartilhados
- `shared/constants/` — rotas e configurações

## Stack Tecnológica

- **Angular 19** — framework
- **TypeScript** — tipagem estática
- **SCSS** — estilos
- **Angular Router** — roteamento
- **UI** — a escolher (não incluída neste template)

## Padronização de Nomes

- Components: PascalCase (ex: `HeaderComponent`, `LoginPage`)
- Services: `*.service.ts` (ex: `auth.service.ts`)
- Models: `*.model.ts` (ex: `user.model.ts`)
- Constants: `*.ts` (ex: `routes.ts`)

## Path Aliases

```text
@/            → src/
@/shared/     → src/shared/
@/features/   → src/features/
```

Exemplo:

```ts
import { something } from '@/shared/lib/something';
import { HomePage } from '@/features/home';
```

## Scripts Disponíveis

- `npm start` — servidor de desenvolvimento (`ng serve`)
- `npm run build` — build de produção
- `npm run watch` — build em modo watch
- `npm test` — testes unitários

## Customização

### Adicionar biblioteca de UI

Instale a lib escolhida (ex: Taiga UI, Angular Material) e coloque wrappers/adapters em `src/shared/ui/`.

### Adicionar nova feature

1. Crie a pasta em `src/features/[feature-name]/`
2. Siga a estrutura (`components`, `services`, `models`, `index.ts`)
3. Exporte no `index.ts`
4. Registre a rota em `src/app/app.routes.ts`

### Alterar nome do projeto

1. Busque `example-project` em todos os arquivos
2. Substitua pelo nome do seu projeto
3. Atualize `package.json` e `angular.json`
4. Atualize valores em `.env` / `env.example`

## Licença

MIT
