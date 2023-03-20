# TypeScript project for Node.js command-line

How to initialize a Typescript application.

## TypeScript

```bash
node init
npm install --save-dev typescript
npm install @types/node --save-dev
npx tsc --init
```

Edit options in `tsconfig.json`:

```json
"rootDir": "./src/"
"outDir": "./dist/",
"lib": ["ESNext"],
"noImplicitAny": true,
```

## Source code

Create some source code:

- `src/index.ts`:

  ```ts
  import { greeting } from "./greeting";

  console.log(greeting());
  ```

- `src/greeting.ts`:

  ```ts
  export function greeting(): string {
    return "Hello world";
  }
  ```

## Scripts

Add to the `scripts` in `package.json`:

```json
"start": "node dist/index.js",
"build": "tsc",
"dev": "tsc -W",
"clean": "rimraf ./dist",
"lint": "eslint ./src"
```

Test the scripts:

```bash
npm run build
npm start
```

## ESLint

```bash
npm --save-dev install eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
npx eslint --init
```

Options:

```
√ How would you like to use ESLint? · problems
√ What type of modules does your project use? · esm
√ Which framework does your project use? · none
√ Does your project use TypeScript? · No / Yes
√ Where does your code run? · node
√ What format do you want your config file to be in? · JSON
√ Would you like to install them now? · No / Yes
√ Which package manager do you want to use? · npm
```

If you're using Prettier:

```bash
npm install --save-dev eslint-config-prettier
```

... and then add `"prettier"` to the end of the `extends` array in the `.eslintrc.json` configuration file.

## VS Code extensions

- Prettier Formatter for Visual Studio Code -- prettier.io
- VS Code ESLint extension -- microsoft.com

## Debugging

```bash
npm install --save-dev ts-node
```

Create a `.vscode\launch.json` file:

```json
{
  // Use IntelliSense to learn about possible attributes.
  // Hover to view descriptions of existing attributes.
  // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "cwd": "${workspaceRoot}",
      "runtimeArgs": ["-r", "ts-node/register"],
      "args": ["${workspaceRoot}/src/index.ts"]
    }
  ]
}
```
