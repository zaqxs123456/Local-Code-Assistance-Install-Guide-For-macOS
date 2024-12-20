# Local Code Assistance Install Guide For macOS

## Aimed Device

- Base model of the new Mac Mini (M4)
    - Apple M4 chip
        - 10-core CPU
        - 10-core GPU
        - 16-core Neural Engine
    - 16GB unified memory
    - 256GB SSD storage

## Packages to Install

- Ollama
- Visual Studio Code
- Continue (Visual Studio Code extension)

## Steps

### 1. Install Ollama

1. Download the Ollama installer from the github repository:
    - [macOS package](https://ollama.com/download/Ollama-darwin.zip)
    - Reference: [Ollama GitHub Repository](https://github.com/ollama/ollama)

2. Installation steps:

    - Click on the Download for macOS button.

    - Once the download is complete, locate the .zip file in your ~/Downloads folder.

    - Double-click the .zip file to extract its contents. This should create Ollama.app.

    - Drag Ollama.app to your Applications folder.

    - Open the Applications folder and double-click on Ollama.app.

    - If you see a warning, click Open to proceed.

### 2. Run a model (optional, use as general chatbot for testing):

- Open terminal.

- Run the following command:
    ```shell
    ollama run [model_name]
    ```
    The model will be downloaded if it is not already downloaded.
    - For example: `ollama run llama3.2`

- [Ollama Model Library](https://ollama.com/library)

- For recommended models, see: [Model Recommendations](#model-recommendations)

### 3. Install Visual Studio Code

- should be installed. If not, download from the [official website](https://code.visualstudio.com/).

### 4. Install Continue (Visual Studio Code extension)

1. Open Visual Studio Code.

2. Click on the Extensions icon on the left sidebar.

3. Search for "Continue" in the search bar.

4. Click on the Install button.

5. Once installed, there will be a Continue icon on the left sidebar.

### 5. Configurations for Continue

1. Click on the Continue icon on the left sidebar.

2. There will be a gear icon on the top right corner. Click on it.

3. config.json file will open.

    - In the models key, you can add the models you want to use for the chatbot, for example:

        ```json
        {
            "models": [
                {
                "title": "model_nickname",
                "model": "actual_model_name_from_ollama_library",
                "provider": "ollama"
                }
            ]
        }
        ```
    - To change the autocomplete model, you can change the "tabAutocompleteModel" key to the model you want to use, for example:

        ```json
        {
            "tabAutocompleteModel": {
                "title": "model_nickname",
                "model": "actual_model_name_from_ollama_library",
                "provider": "ollama",
                "apiBase": "https://127.0.0.1:11434/v1"
            },
        }
        ```
    - "apiBase" is optional, sometimes you may need to add "/v1" to the end of the URL

    - Again, for recommended models, see: [Model Recommendations](#model-recommendations)

    **WARNING:** Do not use any models that require apiKey, it will connect to external servers and violate security policies.


4. Save the file.

5. Before using the chatbot, make sure the Ollama app is running, you can ensure it by running the following command in the terminal:

    ```shell
    ollama serve
    ```

6. Before using the chatbot, make sure you downloaded the model you want to use for the ollama.

    ```shell
    ollama pull [model_name]
    ```

7. Select the model you want to use from the dropdown menu on the bottom of the chatbot text box.

8. Enjoy using the chatbot and code assistance!

## Addional Notes

1. Using external models will cause the chatbot to connect to external servers and violate security policies.

2. Please disable GitHub Copilot when using Continue. As the shortcut conflicted with each other.

## Model Recommendations

Recommended models to use with the base model of the new Mac Mini (M4):

### Chatbot Models

#### [qwen2.5-coder](https://ollama.com/library/qwen2.5-coder)

``` shell
ollama pull qwen2.5-coder:14b # larger option
ollama pull qwen2.5-coder:7b # if 14b is too heavy for mac mini
```

#### [opencoder](https://ollama.com/library/opencoder) 

``` shell
ollama pull opencoder:8b # also a very new model
```

#### [codeqwen](https://ollama.com/library/codeqwen) 

``` shell
ollama pull codeqwen:7b-code # similar to opencoder performance
ollama pull codeqwen:7b-code-v1.5-q4_1 # a bit bigger with different quantization
```

### Code Autocomplete Models

#### [qwen2.5-coder](https://ollama.com/library/qwen2.5-coder)

``` shell
ollama pull qwen2.5-coder:3b # small but relatively powerful
```

#### [deepseek-coder](https://ollama.com/library/deepseek-coder) 

``` shell
ollama pull deepseek-coder:1.3b-instruct-fp16 # somehow have a relatively high score on EvalPlus, too small so I chose the fp16 version
```

#### [phi3.5](https://ollama.com/library/phi3.5)

``` shell
ollama pull phi3.5 # another very small model but high score on EvalPlus
```
