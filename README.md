# Cadl Dogfood repo

This is a repo containing a basic REST API project to get started with CADL.

[**See notes for known issues and things to watch for**](#notes)

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

### Visual studio

**NOTE: For Visual Studio, you must open the folder from the command-line (`devenv .` from the Cadl project folder) to inherit the proper environment.**

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

4. Dev with `--watch` to rebuild on changes (Not working when using docker.)

```bash
cadl compile . --watch
```

5. Edit `main.cadl`. Hello world sample is laying there

6. Optional (Needs docker): Run swagger ui on output openapi => `./swager-ui.sh`(Linux/MacOS) or `./swagger-ui.ps1` (Windows)

## Command summary

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

## Notes

1. When defining operations under a namespace the `@route` decorator is required on the namespace or it won't be discovered and emitted.
1. You cannot define operations at the root of the file
1. Issue with generic interface `interface Adoptable<TPet, TError> {}` that cannot be defined in the main file. Workaround is to define the generic interface in another file and import it. `import "./foo.cadl"`
1. Do not remove the `import "@cadl-lang/openapi3"` import as this is what register the openapi emitter (Specially if copying one of the samples). Without it nothing gets emitted.
