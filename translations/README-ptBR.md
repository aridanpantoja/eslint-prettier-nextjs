<h1 align="center">Configuração do ESLint + Prettier para Next.js 💻</h1> 

<p align="center">
    <b>Este repositório fornece um guia abrangente para integrar o ESLint e o Prettier em um projeto Next.js com TailwindCSS.</b>
</p>

<p align="center">
  <a href="https://nextjs.org/" target="_blank">
    <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js" alt="Badge do Next.js">
  </a>
  <a href="https://reactjs.org/" target="_blank">
    <img src="https://img.shields.io/badge/React-005CFE?style=for-the-badge&logo=react" alt="Badge do React">
  </a>
  <a href="https://eslint.org/" target="_blank">
    <img src="https://img.shields.io/badge/ESLint-4B32C3?style=for-the-badge&logo=eslint" alt="Badge do ESLint">
  </a>
  <a href="https://prettier.io/" target="_blank">
    <img src="https://img.shields.io/badge/Prettier-182025?style=for-the-badge&logo=prettier" alt="Badge do Prettier">
  </a>
  <a href="https://tailwindcss.com/" target="_blank">
    <img src="https://img.shields.io/badge/TailwindCSS-ffffff?style=for-the-badge&logo=tailwindcss" alt="Badge do TailwindCSS">
  </a>
</p>

<p align="center">
  Leia isso em outros idiomas: <a href="./../README.md">Inglês</a>
</p>


<h2 id="project-overview">Visão Geral do Projeto 📋</h2>

Este repositório fornece uma configuração para integrar o ESLint e o Prettier em seu projeto Next.js com TailwindCSS.

- **ESLint**: Analisa o código JavaScript/TypeScript em busca de problemas potenciais e impõe boas práticas.
- **Prettier**: Formata o código para um estilo consistente.
- **Suporte ao TailwindCSS**: Integra o `prettier-plugin-tailwindcss` para organizar as classes do TailwindCSS.

<h2 id="getting-started">Começando</h2>

Para começar com este projeto, siga os passos abaixo:

### Pré-requisitos

Certifique-se de ter o seguinte:

- **Node.js**: Baixe em [nodejs.org](https://nodejs.org/).
- **npm** ou **yarn**: Vem com o Node.js; para yarn, visite [yarnpkg.com](https://yarnpkg.com/).
- **Projeto Next.js**: Crie um novo projeto com o comando: `npx create-next-app@latest my-next-app` ou `yarn create next-app my-next-app`
- Quando solicitado, escolha `Sim` para usar o ESLint.

> Se você não estiver usando o TailwindCSS, pode pular a instalação do `prettier-plugin-tailwindcss` e removê-lo do seu arquivo `.prettierrc.json`.

#### 1. Instale as Dependências Necessárias

Usando npm:
```bash
npm install -D eslint-config-prettier eslint-plugin-jsx-a11y eslint-plugin-prettier prettier prettier-plugin-tailwindcss
```
Usando yarn:
```bash
yarn add --dev eslint-config-prettier eslint-plugin-jsx-a11y eslint-plugin-prettier prettier prettier-plugin-tailwindcss
```

#### 2. Configure o ESLint e o Prettier

Se você estiver usando o Next.js 15 ou superior, crie ou atualize seu arquivo `eslint.config.mjs` em vez de usar `.eslintrc.json`, com a seguinte configuração:

```ts
import { FlatCompat } from '@eslint/eslintrc'

const compat = new FlatCompat({
  // import.meta.dirname is available after Node.js v20.11.0
  baseDirectory: import.meta.dirname,
})

const eslintConfig = [
  ...compat.config({
    extends: [
      'next',
      'next/core-web-vitals',
      'next/typescript',
      'plugin:prettier/recommended',
      'plugin:jsx-a11y/recommended',
    ],
    plugins: ['prettier', 'jsx-a11y'],
    rules: {
      'prettier/prettier': 'error',
      'react/react-in-jsx-scope': 'off',
      'jsx-a11y/alt-text': 'warn',
      'jsx-a11y/aria-props': 'warn',
      'jsx-a11y/aria-proptypes': 'warn',
      'jsx-a11y/aria-unsupported-elements': 'warn',
      'jsx-a11y/role-has-required-aria-props': 'warn',
      'jsx-a11y/role-supports-aria-props': 'warn',
    },
  }),
]

export default eslintConfig
```

Após instalar as dependências, crie ou atualize seu arquivo `.eslintrc.json` com a seguinte configuração:

```json
{
  "extends": [
    "next/core-web-vitals",
    "next/typescript",
    "plugin:prettier/recommended",
    "plugin:jsx-a11y/recommended"
  ],
  "plugins": ["prettier", "jsx-a11y"],
  "rules": {
    "prettier/prettier": "error",
    "react/react-in-jsx-scope": "off",
    "jsx-a11y/alt-text": "warn",
    "jsx-a11y/aria-props": "warn",
    "jsx-a11y/aria-proptypes": "warn",
    "jsx-a11y/aria-unsupported-elements": "warn",
    "jsx-a11y/role-has-required-aria-props": "warn",
    "jsx-a11y/role-supports-aria-props": "warn"
  }
}
```

Em seguida, crie um arquivo .prettierrc.json para personalizar suas configurações do Prettier, se desejado:

```json
{
    "trailingComma": "all",
    "semi": false,
    "tabWidth": 2,
    "singleQuote": true,
    "printWidth": 80,
    "endOfLine": "auto",
    "arrowParens": "always",
    "plugins": ["prettier-plugin-tailwindcss"]
}
```

Se você não estiver usando o TailwindCSS, sua configuração deve ser a seguinte:

```json
{
  "trailingComma": "all",
  "semi": false,
  "tabWidth": 2,
  "singleQuote": true,
  "printWidth": 80,
  "endOfLine": "auto",
  "arrowParens": "always"
}
```

#### 3. Configure o VSCode para autocorreção

Para configurar o ESLint no Visual Studio Code:

- Abra o VSCode e vá para Extensões `Ctrl + Shift + X` ou `Command + Shift + X`.
- Busque por "ESLint" e instale a [extensão da Microsoft](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint).
- (Opcional) Reinicie o VSCode.

Para habilitar correções automáticas de código ao salvar no Visual Studio Code, adicione a seguinte configuração ao seu settings.json:

```json
"editor.codeActionsOnSave": {
    "source.fixAll.eslint": "always",
}
```

<h2 id="contribute">Contribuir 🚀</h2>

Se você quiser contribuir, clone este repositório, crie sua branch de trabalho e coloque a mão na massa!

```bash
git clone https://github.com/aridanpantoja/eslint-prettier-nextjs.git
```
```bash
git checkout -b feature/NAME
```

Ao final, abra um Pull Request explicando o problema resolvido ou a funcionalidade criada, se existir, anexe uma captura de tela das modificações visuais e aguarde a revisão!

### Documentações que podem ajudar

[📝 Como criar um Pull Request](https://www.atlassian.com/br/git/tutorials/making-a-pull-request) |
[💾 Padrão de commit](https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716)

<h2 id="license">Licença 📃 </h2>

Este projeto está sob a licença [MIT](./LICENSE)