# treeify-cli 

<p>
    <a href="https://www.npmjs.com/package/treeify-cli">
        <img src="https://img.shields.io/npm/v/treeify-cli" alt="NPM Version"></a>
    <a href="https://www.npmjs.org/package/treeify-cli">
        <img src="http://img.shields.io/npm/dm/treeify-cli.svg" alt="Downloads"></a>
    <a href="https://www.npmjs.com/package/treeify-cli">
        <img src="https://img.shields.io/npm/l/treeify-cli.svg?sanitize=true" alt="License"></a>
</p>

You can use treeify-cli list directory structure as tree-like in terminal.
## Example

Run this command in treeify-cli root directory
```sh
tree-cli -d ./treeify-cli --ignore node_modules,.git,.DS_Store
```

This will print the following results:
```
·
└── t/treeify-cli
    ├── .gitignore
    ├── .npmignore
    ├── LICENSE
    ├── README.md
    ├── README_zh.md
    ├── bin
    │   └── tree-cli.js
    ├── package-lock.json
    ├── package.json
    ├── read-dir-to-tree.js
    └── tree.js
```

The option `--ignore` or `-i` will ignore directory that you don't want list in terminal


Use `--out` or `-o` to output content to a specified file

```
tree-cli -d ./treeify-cli -o output-demo.md
```

Use `--level` or `-l` option to list custom depth

```
tree-cli -d ./treeify-cli -l 1
```


### Install Globally
In order to use `tree-cli` in terminal you should install `treeify-cli` globally
```
npm install -g treeify-cli
```

### Options

```
Usage: tree-cli [options]

Options:
  -V, --version               output the version number
  -d, --dir <directoryPath>   the directory path you want to render by tree
  -o, --out <filename>        write the tree to a new file
  -i, --ignore <ignoreFiles>  ignore the specified directory or file, they will not be listed
  -l, --level <level>         the depth of the directory tree
  -c, --color [color]         tree’s color which output to the terminal (default: "white")
  -h, --help                  display help for command
```
### Example with API

```js
var cli = require('treeify-cli')
cli.asTree([
        {
            name: "done",
            children: [
                { name: "hiking" }, 
                { name: "camping"}
            ]
        }, 
        {
            name: "todos",
            children: [
                { name: "scuba diving" },
                { name: "surfing" }
            ]
        }
    ])
```
This will get the following results:
```
·
├── done
│   ├── hiking
│   └── camping
└── todos
    ├── scuba diving
    └── surfing
```
You can change the default node name by passing in the second parameter, the default value is {label: "name", children: "children"}
```js
tree.asTree([
    {
        title: "done",
        items: [
            { title: "hiking" }, 
            { title: "camping"}
        ]
    }
], { label: "title", children: "items" })
```

### Cloning this repository

```sh
git clone --depth=1 https://github.com/egsee/treeify-cli.git
```
### License

[MIT](./LICENSE)
