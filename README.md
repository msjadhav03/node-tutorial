# Node.js Application Developer
1. [Buffer and Stream](#bufferandstreams)
2. [Control Flow](#controlflow)
3. [Child Process](#childprocess)
4. [Dignostics](#diagnostics)
5. [Error Handling](#errorhandling)
6. [Node.js CLI](#nodejscli)
7. [Events](#events)
8. [File System](#filesystem)
9. [Javascript Prequesites](#jsprequesite)
10. [Module System](#modulesystem)
11. [Package.json](#packagejson)
12. [Unit Testing](#unittesting) 

# Installing Node.js using fnm
- fast node manager
- fast and simple Node.js version manager
- allows to manage multiple released versions
- Provides operation support
    1. installation
    2. uninstallation
    3. automatic node version switching
- cross platform compatibility
- installing fnm
```sh
curl -fsSL https://fnm.vercel.app/install | bash
```
- export fnm path
```sh
export PATH="/home/test1/.local/share/fnm:$PATH"
```
- install Node.js
```sh
fnm install --lts
```
this command will install latest long term support version of node.
- checking Node version
```sh
node -v
```
# .nvmrc File
- File informs Node.js and the installed package manager on your system to utilize the specific version of Node mentioned in file.
- Creating .nvmrc file
    - open CLI at root directory of Project
    - Now create file with below command
    ```ts
    touch .nvmrc
    ```
    - mention specific version of Node you want to use in your project
    eg. `.nvmrc`
    ```ts
    V18.16.0
    ```
    Save and Close the file.
- Installing Specific Version for Project
    - After creating the file with desired Node.js version. Use following command to install and set specific version for your node.js project
    ```ts
    fnm use --version-file-strategy local
    ```
    Above command will read the .nvmrc file in your ptoject directory and install the specified Node version.

# File Server
- create node project, move to project directory and run below command
```sh
npm init -y
```
- `serve` can be used to serve files from folder
- install serve
```sh
npm install serve
```
- create directory static, add all static files in that folder
```sh
mkdir static
```
- navigate to the static directory and start file server with following command
```sh
npx serve -p 5050 
```
We have used serve command with proper options to run file server.
# Creating npm shell Commands
- custom commands of NPM
- commands are defined in package.json
    ```json
    {
        "static": "serve -p 5050",
        "test":"echo \"Testing command\" && exit 1"
    }
    ```
    Above we have two commands
    1. `static` - command responsible for start file server
    2. `test` - Test command, echoes test message 
- Use indiviually like below
```ts
npm run test
npm run static
```

# Service Mocking
- Rapid Prototyping
- In above File Server data has been mocked no api call has been done to any web service
- server.mjs
```js
 const API = 'http://localhost:3000'

const populateProducts = async (category) => {
  const products = document.querySelector('#products')
  products.innerHTML = ''
  const res = await fetch(${API}/${category})
  const data = await res.json()

  for (const product of data) {
    const item = document.createElement('product-item')
    for (const key of ['name', 'rrp', 'info']) {
      const span = document.createElement('span')
      span.slot = key
      span.textContent = product[key]
      item.appendChild(span)
    }
    products.appendChild(item)
  }
}

const category = document.querySelector('#category')

category.addEventListener('input', async ({ target }) => {
  await populateProducts(target.value)
})

 

 customElements.define('product-item', class Item extends HTMLElement {
  constructor() {
    super()
    const itemTmpl = document.querySelector('#item').content
    this.attachShadow({mode: 'open'}).appendChild(itemTmpl.cloneNode(true))
  }
})
```
# package.json
- to create node project we need to create package.json file, which serves as manifest for the project's dependencies and metadata.
- To create package.json need to initalize Node Project
```sh
npm init
``` 
- enter necessary details as the project name, version, description, entry point file, author, license and more.

- package.json plays vital role in managing dependencies, scripts and other project configurations.

# 
# Buffer and Stream
- Node.js Buffer API
- Incremental Processing
- Transforming Data
- Connecting streams
# Control Flow
- Managing Asynchronous Operations
- Control flow abstraction
# Diagnostics
- Debugging Node.js
- Basic Performance Analysis
# Error Handling
- Common patterns
- Handling errors in various scenarios
# Node.js CLI
- Node executable command line flags
# Events
- The Event System
- Building Event Emitters
- Consuming Event Emitters
# File System
- Input/Output
- Watching
# Javascript prequesite
- Language fundamentals
- scoped to core language features introduced since ECMA Script 
# Module System
- CommonJS Module System Only
# Package.json
- Package Configuration
- Depedency Management
# Unit Testing
- Using Assertions
- Testing Synchronous Code
- Testing Asynchronous Code