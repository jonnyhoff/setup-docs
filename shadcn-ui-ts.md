# Shadcn UI TS

https://ui.shadcn.com/docs

## Create Project

```bash
npm create vite@latest frontend -- --template react-ts
```


## Install Dependencies

```bash
npm install -D tailwindcss postcss autoprefixer
npm install
```

## Init Tailwind

```bash
npx tailwindcss init -p
```

Add this import header in your main css file, `src/index.css` in our case:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Configure the tailwind template paths in tailwind.config.js:

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./index.html", "./src/**/*.{ts,tsx,js,jsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

## Edit `tsconfig.json` file:

The current version of Vite splits TypeScript configuration into three files, two of which need to be edited. Add the `baseUrl` and `paths` properties to the `compilerOptions` section of the `tsconfig.json` and `tsconfig.app.json` files:

```
{
  "files": [],
  "references": [
    {
      "path": "./tsconfig.app.json"
    },
    {
      "path": "./tsconfig.node.json"
    }
  ],
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}
```

## Edit `tsconfig.app.json` file

Add the following code to the `tsconfig.app.json` file to resolve paths, for your IDE:

```json
{
  "compilerOptions": {
    // ...
    "baseUrl": ".",
    "paths": {
      "@/*": [
        "./src/*"
      ]
    }
    // ...
  }
}
```

## Update `vite.config.ts`

Add the following code to the `vite.config.ts` so your app can resolve paths without error:

```bash
npm install -D @types/node
```

```ts
import path from "path"
import react from "@vitejs/plugin-react"
import { defineConfig } from "vite"

export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
})
```

## Install Shadcn UI

```bash
npx shadcn@latest init
```


## Configure `components.json`

You will be asked a few questions to configure `components.json`:

```
Which style would you like to use? › New York
Which color would you like to use as base color? › Zinc
Do you want to use CSS variables for colors? › no / yes
```

## Start adding components to your project.

```bash
npx shadcn@latest add button \
    alert \
    alert-dialog \
    badge \
    card \
    checkbox \
    command \
    toast \
    toggle \
    tooltip \
    dialog \
    dropdown-menu \
    form \
    input \
    menubar \
    navigation-menu \
    select \
    separator \
    sheet \
    sidebar \
    slider \
    switch \
    table \
    tabs \
    textarea
```

The command above will add the components to your project. You can then import it like this:

```tsx
import { Button } from "@/components/ui/button"

export default function Home() {
  return (
    <div>
      <Button>Click me</Button>
    </div>
  )
}
```