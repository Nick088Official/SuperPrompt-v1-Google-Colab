# SuperPrompt-v1

[![Discord](https://img.shields.io/discord/1198701940511617164?color=%23738ADB&label=Discord&style=for-the-badge)](https://discord.gg/osai)

Very small AI Model that Makes your prompts better for AI

Model Used: https://huggingface.co/roborovski/superprompt-v1

Check the model blog here: https://brianfitzgerald.xyz/prompt-augmentation/

## Examples
### 1
This tool has been also used by a **Stable Diffusion 3 Beta Tester** and it shows how good it is and will be when everyone has access to SD 3: https://twitter.com/dark_sm1/status/1774054069126009032
### 2
**Your Prompt** (task prefix already setted): A storefront with 'Text to Image' written on it.

**Generated Better Prompt:** The neon sign above the storefront reads "NeurIPS" in bold, white letters. The storefront is surrounded by a bustling cityscape, with skyscrapers and neon signs lining the walls. The sign is surrounded by a variety of colorful goods, including a variety of fruits, vegetables, and fruits, all arranged in a neat and organized manner. The storefront is surrounded by a bustling crowd of people, all chatting and laughing as they go about their daily routines.

## Local Usage

### Python Code

```py
pip install transformers
```
if its your first time installing the package transformers on Windows, then you may wanna check this https://learn.microsoft.com/en-us/windows/win32/fileio/maximum-file-path-limitation?tabs=powershell#enable-long-paths-in-windows-10-version-1607-and-later.
```py
from transformers import T5Tokenizer, T5ForConditionalGeneration

tokenizer = T5Tokenizer.from_pretrained("google/flan-t5-small")
model = T5ForConditionalGeneration.from_pretrained("roborovski/superprompt-v1", device_map="auto")

input_text = "Expand the following prompt to add more detail: A storefront with 'Text to Image' written on it."
input_ids = tokenizer(input_text, return_tensors="pt").input_ids.to("cuda")

outputs = model.generate(input_ids, max_new_tokens=77)
print(tokenizer.decode(outputs[0]))

# The neon sign above the storefront reads "NeurIPS" in bold, white letters. The storefront is surrounded by a bustling cityscape, with skyscrapers and neon signs lining the walls. The sign is surrounded by a variety of colorful goods, including a variety of fruits, vegetables, and fruits, all arranged in a neat and organized manner. The storefront is surrounded by a bustling crowd of people, all chatting and laughing as they go about their daily routines.
```

### Precompiled
As its a very small model (77M parameters) it can run easily and fast even on old PCs CPU:

#### INSTALLATION
1. [Install Python](https://www.python.org/downloads/), if you haven't already.
2. Click on Code and download as a zip.
3. Extract it.
4. Open the install_and_run_no_ui.bat if you want to use it without ui, or install_and_run_gradio_ui.bat to use the Gradio UI (if its your first time installing the package transformers on Windows, then you may wanna check this https://learn.microsoft.com/en-us/windows/win32/fileio/maximum-file-path-limitation?tabs=powershell#enable-long-paths-in-windows-10-version-1607-and-later).
5. (UI VERSION ONLY): Ctrl+Click the Local URL link that will appear after installing (DO NOT CLOSE THE CMD UNTIL YOU'RE DONE).
5. (UI VERSION ONLY): Ctrl+Click the Local URL link that will appear after installing (DO NOT CLOSE THE CMD UNTIL YOU'RE DONE).
6. After it downloads everything it will ask you for the prompt you want to make better.
7. Enter the Task Prefix, which is The prompt prefix for how the AI should make yours better, recommended "Expand the following prompt to add more detail"
8. Put the Max New Tokens, controls how long is the output, recommended to the max which is 512.
9. Put the Repetition Penalty, the higher the less the ai repeats itself, it goes from 1.0 to 2.0, 1.2 is recommended.
10. Put the Temperature, Higher values produce more diverse outputs, from 0 to 1, 0.7 is suggested.
11. Put the Top P, Higher values sample more low-probability tokens, varies from 0.0 to 2.0, 1.0 is suggested to use.
12. Put the Top K, Higher k means more diverse outputs by considering a range of tokens, from 1 to 100, 50 is suggested.
13. Put the Seed, A starting point to initiate the generation process, any integers, put 0 if you want it to be random.
14. After you will get the generated better prompt and it will start all again.
15. If you want to delete it, delete the venvs folder and then put to the trash bin the .zip and folders of the SuperPrompt-v1.

## Online Usage
### Google Colab
#### NO UI
Run <a target="_blank" href="https://colab.research.google.com/github/Nick088Official/SuperPrompt-v1/blob/main/SuperPrompt_v1_NO_UI.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

#### Ipywidgets UI
Run <a target="_blank" href="https://colab.research.google.com/github/Nick088Official/SuperPrompt-v1/blob/main/SuperPrompt_v1_Ipywidgets_UI.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

#### WEB UI **(WARNING: COULD RISK YOUR GOOGLE COLAB FREE TIER ACC)**
Run <a target="_blank" href="https://colab.research.google.com/github/Nick088Official/SuperPrompt-v1/blob/main/SuperPrompt_v1_WEB_UI.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>


### Hugging Face Space
[![Hugging Face Spaces](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Spaces-blue)](https://huggingface.co/spaces/Nick088/SuperPrompt-v1)

## CREDITS
- [Nick088](https://linktr.ee/Nick088) for the ports.
- [roborovski](https://huggingface.co/roborovski) for making the AI Model
- [Poopmaster/Poiqazwsx](https://github.com/poiqazwsx) added venvs to the local version

## CHANGELOG
### Update - October 26th, 2024
Fix https://github.com/Nick088Official/SuperPrompt-v1/issues/5.
### Update - June 12th, 2024
Reduced the minimum max new tokens to 50 instead of 250, and fixed a bug where you couldn't put repetition penalty on 2 for the web ui
### Update - May 26th, 2024
Correctly use the seed via the tranformers library instead of the torch one, and added a task prefix parameter which is the prompt for how to expand the your prompt to the AI.
### Update - May 17th, 2024
Added back the model precision option for every ports and also improved a bit more the local version.
### Update - May 16th, 2024
Improved the Local Version and removed the model precision option, so i used auto instead.
### Update - April 14th, 2024
Updated the local version to make it use venvs, Credits for it to [Poopmaster/Poiqazwsx](https://github.com/poiqazwsx)
