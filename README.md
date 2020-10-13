# GAS project Template with TypeScript

This repository is a template to develop a GoogleAppsScript project with TypeScript.

## Usage

Clone from Github.

```zsh
git clone https://github.com/genki-sano/gas-ts-template <your-project-name>
cd <your-project-name>
yarn install
```

login with Google.

```zsh
yarn run clasp login
```

Create new GoogleAppsScript project. (Check [the referrence](https://github.com/google/clasp#create).)

```zsh
yarn run clasp create --type standalone --title "Your GAS Project Name" --parentId "1D_Gxyv*****************************NXO7o" --rootDir ./dist
```

Inject Your functions to `global` variable in `index.ts` like this:

```ts
declare const global: {
  [x: string]: any
}

global.doGet = (
  e: GoogleAppsScript.Events.DoGet,
): GoogleAppsScript.HTML.HtmlOutput => {
  console.log('GAS got a get request!')

  const params = JSON.stringify(e)
  return HtmlService.createHtmlOutput(params)
}

global.doPost = (
  e: GoogleAppsScript.Events.DoPost,
): GoogleAppsScript.HTML.HtmlOutput => {
  console.log('GAS got a post request!')

  const params = JSON.stringify(e)
  return HtmlService.createHtmlOutput(params)
}
```

Once your development is done, push your codes to GAS project.

```zsh
yarn run deploy
```

Visit https://script.google.com/d/{your-script-id}/edit, and try to run your code.

Have a nice hack !

## License

This software is released under the MIT License, see [LICENSE](LICENSE)
