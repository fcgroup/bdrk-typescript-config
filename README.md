# TypeScript Config

This repository contains the baseline TypeScript compiler configuration for all Bedrock projects
that use TypeScript 5 or newer.

## Referencing this Configuration

You can reference this config by installing the NPM package in your project:

```bash
npm install --save-dev @bdrk/typescript-config
```

Then replace the contents of your `tsconfig.json` file with:

```json
{
  "extends": "@bdrk/typescript-config"
}
```

You can overwrite settings defined in this configuration by specifying them in your project's `tsconfig.json`.
