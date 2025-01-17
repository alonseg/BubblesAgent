# Bubbles Agent

<img src="images/logo.png" width="150px" height="150px" alt="Project logo"/>

Apply your GPT/Gemini prompt to a mass of code files in one shot.

## Installation
Clone the repository

Inside the project run
```bash
npm i
```

## AI configuration
If you use ChatGpt insert your API key in the _config file_ under **openAiConfig**

If you are using Vertex AI, choose your model in the _config file_ under **vertexAiConfig**
And insert the creds in the _vertex-ai-creds.json file_ as well as project and location in _vertexAi_ file
```bash
## Configuration
Add your own configuration under RefactorsActions in the config file.json

```bash
      {
            "description": "description of the refactoring task for readability",
            "prompt": "string|file path - Prompt string to give insturctions for refactoring OR file path to a .txt file with long prompt.",
            "targetDir": "the full path of the directory where the refactoring should be done recursively",
            "targetFilesExtensionRegex": "regex - which files to work on, like '.*.test.js'",
            "contentConditionRegex": "regex - which content should be in the file in order to refactor, like '.*'. Another example: 'extends\\s+(React\\.)?(Pure)?Component\\s*{'",
            "advanceOptions": {
                "outputFileExtension": "optional - when given, the result of the refactoring will be saved to the same file name and given file extention, like test.js",
                "examples": {
                    "useFilePath": "true/false - if true, will search for {\"file_path\":\"/Path/of/file.js\"}",
                    "diffFile": "oprional - will be used as 'diff' code example"
                },
                "codeValidators": [
                    "babelCompile - optional - validate the refactor is compiled by JS babel",
                    "JestRunner - optional - validate the refactor is tested by Jest and the unit test is green"
                ]
            }
        }
```
## Usage

For an example if you use the Accessify prompt to make the file accessible
```bash
 "Accessify": {
            "description": "Make it to accessiable",
            "prompt": "Make the following code to be fully accessible.\n Make sure to add the proper aria attributes and roles.\n Follow the WAI-ARIA best practices and WCAG 2 A and AA Checklist.",
            "targetDir": "/business/components/Accordion",
            "targetFilesExtensionRegex": ".*.react.js",
            "contentConditionRegex": "extends\\s+(React\\.)?(Pure)?Component\\s*{",
            "advanceOptions": {
                "codeValidators": [
                    "babelCompile"
                ]
            }
        },
```

you will run it with the next command
```bash
npm run start Accessify
```


## Contributing


You are welcome to contribute :)

TODO list:
- Add more AI models (Claude)
- Add more code validators (Css validator, etc)
- Use Husky(https://typicode.github.io/husky/get-started.html) to prevent the commit of secrets
- Add UT for the code (can be added with bubbles agent itself)