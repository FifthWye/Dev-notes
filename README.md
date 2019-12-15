# Dev-notes
Here is my developer notes of solutions that was hard to find for me and just useful information.

## Web

## Desktop

### Electron

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

## Mob
