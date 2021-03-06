# Markdown Links

> Biblioteca que oferece uma CLI (Command Line Interface - Interface de Linha de Comando) que retorna uma lista dos links contidos em um arquivo Markdown(.md) e pode verificar a validade dos mesmos.

## Como instalar

    $ npm install -g aline-camargo/SAP003-md-links

    
Se for mostrado um erro de permissão, tente usar `sudo` (talvez você precise de permissões
de administrador, dependendo da sua instalação do node).

```console
# usando `sudo` (somente se o passo anterior falhar)
$ sudo npm install -g aline-camargo/SAP003-md-links
```

## Como usar

### No seu projeto JavaScript

Para utilizar a biblioteca em um projeto JavaScript, faça o `require` no arquivo desejado. Dessa forma:

```js
const mdLinks = require(".caminho-da-pasta-de-instalação/lib/index.js");

mdLinks("./exemplo.md", { validate: true })
  .then(links => {
    if(validate) {
      // => [{ href, text, status }]
    } else {
      // => [{ href, text }]
    }
  })
  .catch(console.error);
```

### CLI (Command Line Interface - Interface de Linha de Comando)
#### Para fazer uma simples listagem:

    $ md-links caminho/do/arquivo.md

Retorno esperado


```console
$ md-links ./algum/exemplo.md
http://algo.com/2/3/ Link de algo
https://outra-coisa-.net/algum-doc.html algum doc
http://google.com/ Google
```

#### Para verificar a validade dos links:

    $ md-links caminho/do/arquivo.md -v

ou

    $ md-links caminho/do/arquivo.md  --validate

Retorno esperado


```console
$ md-links ./algum/exemplo.md --validate
http://algo.com/2/3/ 200 Link de algo
https://outra-coisa-.net/algum-doc.html 404 algum doc
https://site-inexistente.com ENOTFOUND Nome do site
http://google.com/ 301 Google
```

## Considerações gerais

### Tecnologias e bibliotecas utilizadas

* [Node.js](https://nodejs.org/)
* [yargs](https://www.npmjs.com/package/yargs)
* [chalk](https://www.npmjs.com/package/chalk)
* [fs](https://nodejs.org/api/fs.html)
* [node-fetch](https://www.npmjs.com/package/node-fetch)
* [eslint](https://eslint.org/)
* [jest](https://jestjs.io/)

### Arquivos do Projeto


* `README.md`
* `package.json` possuindo o nome, versão, descrição, autor, licença,
  dependências e scripts (eslint e test).
* `package-lock.json` arquivo gerado pelo npm, para controle dos pacotes instalados
* `.eslintrc` com a configuração para o linter.
* `.gitignore` para ignorar o `node_modules` e outras pastas que não devem ser incluídas no controle de versão (`git`).
* `cli.js` arquivo que chama a função `mdLinks` que será executada pela linha de comando.
* `lib/index.js` criação e exportação da função `mdLinks`.
* `lib/__tests__/index.spec.js` contém testes unitários para a função `mdLinks`.
