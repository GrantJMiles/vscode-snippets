# Useful code snippets
An extension to collect and collate a handful of useful code snippets for visual studio code.

[![Deploy Extension to the Marketplace](https://github.com/GrantJMiles/vscode-snippets/actions/workflows/package-extension.yml/badge.svg)](https://github.com/GrantJMiles/vscode-snippets/actions/workflows/package-extension.yml)

# Getting Started
The project uses a remote development container made up of the boilerplate Node.js & typescript with a couple of commands added to the [Dockerfile](.devcontainer/Dockerfile) to install some of the cli tools for creating VS code extensions.

## Running the project
If using the .devcontainer open the project inside or opent he project in an environment with the correct dependencies already installed. The dependencies can be seen inside the [base Dockerfile](https://github.com/microsoft/vscode-dev-containers/tree/v0.194.0/containers/typescript-node/.devcontainer/base.Dockerfile) that the container is formed from.

Once opened in your preferred environment you can hit F5 to debug the extension which will open a new VS code window with the capabilities of the extension available. 

## How to contribute
If you want to modify any of the exisitng snippets or add a new one for ease of use, [raise an issue](https://github.com/GrantJMiles/vscode-snippets/issues/new) or [start a discussion](https://github.com/GrantJMiles/vscode-snippets/discussions/new) to connect with other interested parties. Once a snippet has been discussed and agreed the suggested workflow is:
1. Fork the repo and complete any work in your version of the repo
1. Update the version with:
    * Major if you completly rewritten an exisiting snippet
	* Minor if you have introduced new snippets
	* Patch if you have made a fix to an exisiting but not changed the way it is used or consumed
1. Squash Commit your changes before making a PR into the [main](https://github.com/GrantJMiles/vscode-snippets/tree/main) branch.

## How to add a snippet to the project
To add a new snippet that will write "Hello World!" to the console we need to first follow the steps in the [VS code docs](https://code.visualstudio.com/docs/editor/userdefinedsnippets#_snippet-syntax) to create the snippet. For this example the snippet we are going to use is this:
```json
"hello-world": {
	"prefix": ["hello-world", "hw-test"],
	"scope": "csharp",
	"description": "Example snippet to demonstrate how to contribute",
	"body": "Console.WriteLine(\"Hello World!\");"
}
```
Above the prefix are the suggestions that will show when you type in a C# file or "CTRL + ." and the body is the snippet that will be added.

Take the above snippet and put it into a json file inside the .snippets folder (wrapped in {}).

Once the snippet exists in a file we need to add the file to the contributes section inside the `package.json` file.
```json
"contributes": {
    "snippets": [
        // ...Removed for brevity
        {
            "language": "chsarp",
            "path": "./.snippets/hello-world.json"
        }
    ]
},
```
As this is a new snippet we will increase the minor version in the same file as the above `"version": "0.0.1"`

## Add a section to the extension README
Add a section to the readme that shows off the prefixes and eventual code block
```md
# Testing Snippet
By using the following prefixes `"prefixes":["hello-world", "hw-test"]` you will get the eventual code line:

Console.Writeline("Hello World!");
```

## Publishing the extension
Once the PR has been completed into main a GitHub action will trigger and deploy the extension. It can then take up to 5 minutes for the extension to be verified by the marketplace before being visible inside VS code Extensions