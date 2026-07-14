# TypeScript Config

This repository contains the baseline TypeScript compiler configuration for all Bedrock projects
that use TypeScript 5 or newer. It is verified against TypeScript 5.x, 6.x, and 7.x.

## Referencing this Configuration

You can reference this config by installing the NPM package in your project:

```bash
npm install --save-dev @bdrk/typescript-config
```

Then replace the contents of your `tsconfig.json` file with:

```json
{
  "extends": "@bdrk/typescript-config",
  "include": ["./src/**/*"]
}
```

You can overwrite settings defined in this configuration by specifying them in your project's `tsconfig.json`.

## Defaults

This configuration targets Node.js projects with the conventional layout of sources in `src/`
compiled to `dist/`:

- `target: ES2022` / `lib: ["ES2022"]` — safe for all maintained Node.js releases
- `module: nodenext` / `moduleResolution: nodenext` — modern Node.js module semantics
  (emits CommonJS unless your `package.json` declares `"type": "module"`)
- `rootDir: src` / `outDir: dist` — resolved relative to your project root;
  TypeScript 6+ requires an explicit `rootDir`, so override it if your sources live elsewhere
- `resolveJsonModule`, `esModuleInterop`, and `skipLibCheck` are enabled
- `strictNullChecks` is enabled (full `strict` mode is not)

## Common Overrides

Browser-facing projects should add the DOM libraries:

```json
{
  "extends": "@bdrk/typescript-config",
  "compilerOptions": {
    "lib": ["DOM", "ES2022"]
  }
}
```

Projects using legacy (pre-TC39) decorators, such as NestJS or TypeORM services, should set:

```json
{
  "extends": "@bdrk/typescript-config",
  "compilerOptions": {
    "experimentalDecorators": true,
    "emitDecoratorMetadata": true
  }
}
```
