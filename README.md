<h1 align="center">ESLint + Prettier Setup for Next.js 💻</h1> 

<p align="center">
    <b>This repository provides a comprehensive guide for integrating ESLint and Prettier into a Next.js project with TailwindCSS.</b>
</p>

<p align="center">
  <a href="https://nextjs.org/" target="_blank">
    <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js" alt="Next.js Badge">
  </a>
  <a href="https://reactjs.org/" target="_blank">
    <img src="https://img.shields.io/badge/React-005CFE?style=for-the-badge&logo=react" alt="React Badge">
  </a>
  <a href="https://eslint.org/" target="_blank">
    <img src="https://img.shields.io/badge/ESLint-4B32C3?style=for-the-badge&logo=eslint" alt="ESLint Badge">
  </a>
  <a href="https://prettier.io/" target="_blank">
    <img src="https://img.shields.io/badge/Prettier-182025?style=for-the-badge&logo=prettier" alt="Prettier Badge">
  </a>
  <a href="https://tailwindcss.com/" target="_blank">
    <img src="https://img.shields.io/badge/TailwindCSS-ffffff?style=for-the-badge&logo=tailwindcss" alt="TailwindCSS Badge">
  </a>
</p>

<p align="center">
  <i>Read this in other languages: <a href="./translations/README-ptBR.md">Português</a></i>
</p>

<h2 id="project-overview">Project Overview 📋</h2>

This repository provides a setup for integrating ESLint and Prettier into your Next.js project with TailwindCSS.

- **ESLint**: Analyzes JavaScript/TypeScript code for potential issues and enforces best practices.
- **Prettier**: Formats code for consistent styling.
- **TailwindCSS Support**: Integrates `prettier-plugin-tailwindcss` to organize TailwindCSS classes.

<h2 id="getting-started">Getting Started</h2>

To get started with this project, follow the steps below:

### Prerequisites

Ensure you have the following:

- **Node.js**: Download from [nodejs.org](https://nodejs.org/).
- **npm** or **yarn**: Comes with Node.js; for yarn, visit [yarnpkg.com](https://yarnpkg.com/).
- **Next.js Project**: Create a new project with the command: `npx create-next-app@latest my-next-app` or `yarn create next-app my-next-app`
- When prompted, choose `Yes` for using ESLint.

> If you're not using TailwindCSS, you can skip installing `prettier-plugin-tailwindcss` and remove it from your `.prettierrc.json` file.

#### 1. Install Required Dependencies

Using npm:
```bash
npm install -D eslint-config-prettier eslint-plugin-jsx-a11y eslint-plugin-prettier prettier prettier-plugin-tailwindcss
```
Using yarn:
```bash
yarn add --dev eslint-config-prettier eslint-plugin-jsx-a11y eslint-plugin-prettier prettier prettier-plugin-tailwindcss
```

#### 2. Configure ESLint and Prettier

If you're using Next.js 15+, create or update your `eslint.config.mjs` file instead of `.eslintrc.json` with the following configuration:

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

After installing the dependencies, create or update your `.eslintrc.json` file with the following configuration:

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

Next, create a `.prettierrc.json` file to customize your Prettier settings, if desired:

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

If you're not using TailwindCSS, your configuration should be as follows:

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

#### 3. Configure VSCode for AutoFix

To set up ESLint in Visual Studio Code:

- Open VSCode and go to Extensions `Ctrl + Shift + X` or `Command + Shift + X`.
- Search "ESLint" and install the [extension by Microsoft](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint).
- (Optional) Restart VSCode.

To enable automatic code fixes on save in Visual Studio Code, add the following setting to your `settings.json`:

```json
"editor.codeActionsOnSave": {
    "source.fixAll.eslint": "always",
}
```

<h2 id="contribute">Contribute 🚀</h2>

If you want to contribute, clone this repo, create your work branch and get your hands dirty!

```bash
git clone https://github.com/aridanpantoja/eslint-prettier-nextjs.git
```

```bash
git checkout -b feature/NAME
```

At the end, open a Pull Request explaining the problem solved or feature made, if exists, append screenshot of visual modifications and wait for the review!

### Documentations that might help

[📝 How to create a Pull Request](https://www.atlassian.com/br/git/tutorials/making-a-pull-request) |
[💾 Commit pattern](https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716)

<h2 id="license">License 📃 </h2>

This project is under [MIT](./LICENSE) license