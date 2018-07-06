# cnys [![Build Status](https://travis-ci.org/FabienGreard/cnys.svg?branch=master)](https://travis-ci.org/FabienGreard/cnys)[![dependencies Status](https://david-dm.org/FabienGreard/cnys/status.svg)](https://david-dm.org/FabienGreard/cnys)[![devDependencies Status](https://david-dm.org/FabienGreard/cnys/dev-status.svg)](https://david-dm.org/FabienGreard/cnys?type=dev)

cnys main feature allow developers to synchronize files between remote server on change !, **what it does**:

- sftp ! :globe_with_meridians:
- Server hoping (netcat) :lock:
- Copy/delete file/folder ! :eyeglasses:
- Ready to use :fire:

If something doesn’t work, please [file an issue](https://github.com/FabienGreard/cnys/issues/new) :bug:.

## Quick Start

### Install

```sh
$ npm install or yarn install
```

### Commands

Start cnys on a local folder to a local destination :

```sh
$ cyns local [source=<sourcePath>] [destination=<destinationpath>]
```

| Options   | Description                                           | aliases | type                                                  | default |
| --------- | ----------------------------------------------------- | ------- | ----------------------------------------------------- | ------- |
| --verbose | Output action logs                                    | --v     | boolean                                               | true    |
| --debug   | Output debug logs                                     | --d     | boolean                                               | false   |
| --remove  | Enable delete file from destination                   | --rm    | boolean                                               | true    |
| --ignored | A glob, regex, function, or array of any combination. | --i     | [filePattern](https://github.com/micromatch/anymatch) | null    |

:warning: **The remote feature is still under huge development !**

```sh
$ cyns remote [source=<sourcePath>] [url=<urlString>] [destination=<destinationpath>]
```

| Options      | Description                                           | aliases | type        | default |
| ------------ | ----------------------------------------------------- | ------- | ----------- | ------- |
| --verbose    | Output action logs                                    | --v     | boolean     | false   |
| --debug      | Output debug logs                                     | --d     | boolean     | true    |
| --copy       | Enable to copy source to destination at start         | --cp    | boolean     | true    |
| --remove     | Enable delete file from destination                   | --rm    | boolean     | null    |
| --glob       | A single string glob pattern or an array of them      | --g     | filePattern | null    |
| --ignored    | A glob, regex, function, or array of any combination. | --i     | filePattern | null    |
| --ncUrl      | A netcat url for ssh.                                 | --nc    | string      | 5       |
| --retry      | Number of retry when an error occur durring copy.     | --r     | number      | null    |
| --username   | A username to connect for ssh.                        | --u     | string      | null    |
| --password   | A password to connect for ssh.                        | --pwd   | string      | null    |
| --privateKey | Will look for your pka file under ~/.ssh.             | --ppk   | boolean     | false   |

## Example of use :

```sh
$ cnys local 'sync' 'sync2' --v true --ignored '.*' '*.yml'
```

The example above will start watching file on a folder name sync and copying file into folder sync2

```sh
$ cnys remote 'sync' '192.168.30.2' '/home/user/test'  --ncUrl '192.168.30.3' --username 'fgreard' --privateKey true --retry 100
```

The example above will start watching file on a folder name sync and copying file to '192.168.30.2' at '/home/user/test'

## Test

Use `npm test` to start testing your file. By default it read test file named `*.test.js` under `/test`.

You can easily add your own config by editing `package.json`

It also has a built-in coverage with `npm run coverage`

## Credits

[chokidar](https://github.com/paulmillr/chokidar), a powerfull watcher
[Jest](https://facebook.github.io/jest/), a testing framework
