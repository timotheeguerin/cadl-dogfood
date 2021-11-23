# Cadl Dogfood repo

This is a repo containing a basic REST API project to get started with CADL.

## Prerequisites

### [Required] Cadl cli/compiler

Option 1: Via Node

1. Install node 14.x or node 16.x. **CADL is NOT compatible with version of node below 14.x**
1. Install package globally

```
npm install -g @cadl-lang/compiler
```

Option 2: Via docker

See [docs](https://github.com/microsoft/cadl/blob/main/docs/docker.md) for full docker documentations.

1. Install docker
1. For all the following steps replace the `cadl` ecutable from the command with the following line

```bash
docker run -v "${pwd}:/wd" --workdir="/wd"  -t azsdkengsys.azurecr.io/cadl
```

### [Recommended] VSCode and extensions

Install the following extensions:

- `prettier`: Provide auto formatting for cadl language
- `cadl`: cadl extension, will provide error reporting and syntax highlighting for cadl files. To install that extension run

```bash
cadl code install
```

## Getting started

1. Install cadl libraries for this project

```bash
cadl install
```

2. Compile

```bash
cadl compile .
```

3. Produced `openapi.json` in `./cadl-output` folder

4. Dev with `--watch` to rebuild on changes

```bash
cadl compile . --watch
```

## Commnad summary

| Action                   | Command                    |
| ------------------------ | -------------------------- |
| Help                     | `cadl --help`              |
| Compile once             | `cadl compile .`           |
| Compile in watch mode    | `cadl compile . --watch`   |
| Format cadl code         | `cadl format **/*.cadl`    |
| Install dependencies     | `cadl install`             |
| Install dependencies     | `cadl install`             |
| Install VSCode extension | `cadl code install`        |
| Init a new project       | `cadl init [tempalateUrl]` |
