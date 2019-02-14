# import json file

## 新增 options 在 tsconfig.json

~~~typescript
{
  "compileOnSave": false,
  "compilerOptions": {
    "baseUrl": "./",
    "outDir": "./dist/out-tsc",
    "sourceMap": true,
    "declaration": false,
    "module": "es2015",
    "moduleResolution": "node",
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "target": "es5",
    "typeRoots": [
      "node_modules/@types"
    ],
    "lib": [
      "es2018",
      "dom"
    ],
    "resolveJsonModule": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true
  }
}
~~~

- 這三項

    ~~~typescript
        "resolveJsonModule": true,
        "esModuleInterop": true,
        "allowSyntheticDefaultImports": true
    ~~~

## link 

 > https://stackblitz.com/edit/json-import-example?file=src%2Fapp%2Fapp.component.ts