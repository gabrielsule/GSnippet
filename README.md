## GSnippet
### Cómo generar un snippet para VSCode paso a paso

- correr desde la consola de comandos `npm i -g yo generator-code`
- crear una carpeta por ejemplo: **dev**
- una vez dentro de la carpeta ejecutamos el siguiente comando `yo code`, seleccionar **snippet** y suministrar los datos solicitados
- modificamos el archivo package.json, deberá tener un formato similar al siguiente:

```json
{
    "name": "gsinippet",
    "displayName": "GSinippet",
    "description": "Dummy de un snippet de NodeJS",
    "version": "1.0.0",
    "publisher": "Gabriel",
    "repository": {
        "type": "git",
        "url": "https://github.com/gabrielsule/gsnippet"
    },
    "icon": "batman.ico",
    "engines": {
        "vscode": "^1.33.0"
    },
    "categories": [
        "Snippets"
    ],
    "contributes": {
        "snippets": [
            {
                "language": "javascript",
                "path": "./snippets/snippets.json"
            }
        ]
    }
}
```
- modificamos el archivo CHANGELOG.md, simplemente agregándole el número de versión `## [1.0.0]`

#### Ahora viene la parte divertida !!!
- ingresamos en la carpeta **snippets** y editamos el archivo **snippets.json** (que es el core de nuestro snippet), y agregamos el siguiente código:

```json
{
    "NodeJS starter template": {
        "prefix": "!gs",
        "body": [
            "const express = require('express');",
            "const app = express();",
            "app.get('/', (req, res) => {",
            "    res.send('hello dev');",
            "});",
            "app.get('/api/courses', (req, res) => {",
            "    res.send([1,2,3,4]);",
            "});",
            "app.get('/api/courses/:id', (req, res) => {",
            "    res.send(req.params);",
            "});",
            "const port = process.env.PORT || 3000;",
            "app.listen(port, () => {console.log(`server en port ${port}`)});"
        ],
        "description":"Creates a NodeJS starter"
    }
}
```
- para realizar una prueba de test o simplemente para dejarlo en nuestro "store personal", copiamos el folder del código a la carpeta `%USERPROFILE%\.vscode\extensions` para win o en `~/.vscode/extensions` para macOS 

#### Testeo
- reiniciamos VSCode para que tome los cambios
- generamos un archivo denominado **server.js**  y ejecutamos `!gs`, veremos cómo se genera automáticamente el template de NodeJS para generar un servidor para ser ejecutado en el puerto 3000



[@gabrielsule](https://twitter.com/gabrielsule "@gabrielsule")
