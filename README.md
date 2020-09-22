# Dev-notes
Here is my developer notes of solutions that was hard to find for me and just useful information.

## Web

##### GIT
Remove loacl branch
```
git branch -d branch_name
```


##### Serverless puppeteer with lambda functions
[Git repository](https://github.com/serverless/examples/tree/master/aws-node-puppeteer) | 
[Lambda layers arn versions](https://github.com/shelfio/chrome-aws-lambda-layer)


##### Puppeter don't load chromium without setting env
```
npm config set puppeteer_skip_chromium_download true -g
``` 

##### Puppeteer asar packaging problem ( [Issue](https://github.com/puppeteer/puppeteer/issues/2134) ) 

main.js
```

function getChromiumExecPath() {
    return puppeteer.executablePath().replace('app.asar', 'app.asar.unpacked');
}

export function createBrowser(options = {}) {
    return puppeteer.launch({
        ...options,
        executablePath: getChromiumExecPath()
    });
}

```

package.json
```
"build": {
    "asar": true,
    "asarUnpack": "node_modules/puppeteer/.local-chromium/**/*"
}
```

## Desktop

### ngrok

[website](https://ngrok.com/)

ngrok provides a real-time web UI where you can introspect all HTTP traffic running over your tunnels. Replay any request against your tunnel with one click.

comand for seting up tunnel with localhost:3000 as a source
```
ngrok http 3000 -host-header="localhost:3000"
```

### Node.js
If you have such an error, the problem is in pareser from newer versions of node js  Try install v 10 or erlier versions :
```
Error: Parse Error: Invalid header value char
    at TLSSocket.socketOnData (_http_client.js:476:22)
    at TLSSocket.emit (events.js:311:20)
    at TLSSocket.EventEmitter.emit (domain.js:482:12)
    at addChunk (_stream_readable.js:294:12)
    at readableAddChunk (_stream_readable.js:275:11)
    at TLSSocket.Readable.push (_stream_readable.js:209:10)
    at TLSWrap.onStreamRead (internal/stream_base_commons.js:186:23)
```
This command might also help
```
--http-parser=legacy
```

nvm for windows, would help a lot with having multiple versions of node

### Electron

##### Best electron auto updater example
[Git repository](https://github.com/iffy/electron-updater-example)


## Mob

## IDE

### Vscode

Best way to do changes in multiple lines is to search for exact RegEx and replace these lines with modefied content. [Example](https://stackoverflow.com/a/44793837)
