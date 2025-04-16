# TP ESLINT

## 1. Initialisation du projet et installation d'ESLint

## 2. Test d’ESLint sur un fichier JavaScript
Après création d'un fichier js avec erreur : 
```
C:\Users\sarah\source\repos\Ecole\Outils_pratique_code_BIAM\tp-eslint-git\app.js
  0:0  warning  File ignored because of a matching ignore pattern. Use "--no-ignore" to disable file ignore settings or use "--no-warn-ignored" to suppress this warning

✖ 1 problem (0 errors, 1 warning)
```



## 3. Intégration avec Git Hooks (Husky)
Après test du hook : 
```
>git add .
warning: in the working copy of 'node_modules/.package-lock.json', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'package-lock.json', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'package.json', LF will be replaced by CRLF the next time Git touches it

>git commit -m "Test du hook ESLint"
.husky/pre-commit: line 1: npx eslint .: command not found
husky - pre-commit script failed (code 127)
husky - command not found in PATH=node_modules/.bin:/mingw64/libexec/git-core:/mingw64/bin:/usr/bin:/c/Users/sarah/bin:/c/Program Files/Common Files/Oracle/Java/javapath:/c/Program Files (x86)/Common Files/Oracle/Java/java8path:/c/Program Files (x86)/Common Files/Oracle/Java/javapath:/c/Windows/system32:/c/Windows:/c/Windows/System32/Wbem:/c/Windows/System32/WindowsPowerShell/v1.0:/c/Windows/System32/OpenSSH:/c/Program Files (x86)/NVIDIA Corporation/PhysX/Common:/c/Program Files/WireGuard:/c/Program Files/Microsoft SQL Server/150/Tools/Binn:/c/Program Files/Microsoft SQL Server/Client SDK/ODBC/170/Tools/Binn:/c/Program Files/dotnet:/c/Users/sarah/.config/herd/bin/nvm:/c/Program Files/nodejs:/cmd:/c/Program Files/Docker/Docker/resources/bin:/c/Program Files (x86)/Windows Kits/10/Windows Performance Toolkit:/c/Program Files/CMake/bin:/c/Program Files/Java/jdk-23/bin:/c/WINDOWS/system32:/c/WINDOWS:/c/WINDOWS/System32/Wbem:/c/WINDOWS/System32/WindowsPowerShell/v1.0:/c/WINDOWS/System32/OpenSSH:/c/Program Files/NVIDIA Corporation/NVIDIA app/NvDLISR:/c/Program Files/nodejs:/c/Users/sarah/.config/herd/bin:/c/Users/sarah/AppData/Local/Programs/Python/Python312:/c/Users/sarah/AppData/Local/Microsoft/WindowsApps:/c/Users/sarah/AppData/Local/Programs/Microsoft VS Code/bin:/c/Program Files/JetBrains/PhpStorm 2024.2.1/bin:/c/Users/sarah/.dotnet/tools:/c/Program Files/JetBrains/CLion 2024.2.2/bin:/c/Users/sarah/AppData/Local/Programs/Python/Python312/Scripts:/c/Users/sarah/AppData/Local/poppler-24.08.0/Library/bin:/c/Program Files/JetBrains/IntelliJ IDEA 2024.2.3/bin:/c/Users/sarah/anaconda3/condabin:/c/Users/sarah/AppData/Local/JetBrains/Toolbox/scripts:/c/Users/sarah/AppData/Local/Microsoft/WindowsApps:/c/Users/sarah/AppData/Roaming/npm
```

## 4. Confi guration avancée d’ESLint

Modification du fichier 'eslint.config.mjs':
```
import json from '@eslint/json';
import { defineConfig } from 'eslint/config';

export default defineConfig([
  {
    ignores: ['node_modules/**', 'dist/**'], 
  },
  {
    files: ['**/*.js'],
    languageOptions: {
      ecmaVersion: 2021,
      sourceType: 'module',
      globals: {
        browser: true,
        node: true
      }
    },
    rules: {
      'no-console': 'warn',
      'indent': ['error', 2],
      'quotes': ['error', 'single']
    }
  }
]);
```
ajout du script 'lint' et lancement de la commande ```npm run lint```:

```
C:\Users\sarah\source\repos\Ecole\Outils_pratique_code_BIAM\tp-eslint-git\app.js
    2:1  warning  Unexpected console statement  no-console
  4:3  warning  Unexpected console statement  no-console

✖ 2 problems (0 errors, 2 warnings)


```


## 5. Mise en place de GitHub Actions


Après ajout du Workflow : présence d'un workflow run avec comme nom le dernier commit et réception d'un email avec le succès ou l'échec de la Run du workflow


## 6. Simulation d’un travail d’équipe

Après ajout du code non conforme : 
```
C:\Users\sarah\source\repos\Ecole\Outils_pratique_code_BIAM\tp-eslint-git\app.js
  2:1  warning  Unexpected console statement  no-console
  4:3  warning  Unexpected console statement  no-console

C:\Users\sarah\source\repos\Ecole\Outils_pratique_code_BIAM\tp-eslint-git\utils.js
   2:1   error    Expected indentation of 2 spaces but found 0  indent
   3:1   warning  Unexpected console statement                  no-console
   3:1   error    Expected indentation of 2 spaces but found 0  indent
   4:1   error    Expected indentation of 2 spaces but found 0  indent
  11:5   warning  Unexpected console statement                  no-console
  11:17  error    Strings must use singlequote                  quotes
  17:1   warning  Unexpected console statement                  no-console
  22:3   warning  Unexpected console statement                  no-console
  22:15  error    Strings must use singlequote                  quotes
  26:1   error    Expected indentation of 2 spaces but found 0  indent
  28:1   error    Expected indentation of 2 spaces but found 0  indent
  33:3   warning  Unexpected console statement                  no-console
  37:3   warning  Unexpected console statement                  no-console
  48:3   warning  Unexpected console statement                  no-console
  49:3   warning  Unexpected console statement                  no-console
  53:3   warning  Unexpected console statement                  no-console

✖ 18 problems (7 errors, 11 warnings)
  7 errors and 0 warnings potentially fixable with the `--fix` option.

husky - pre-commit script failed (code 1)
```