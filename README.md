# Important commands 

start web server 
````./webui.sh --skip-torch-cuda-test --precision full --no-half``


# Important links 
https://github.com/ndanny/stable-diffusion-codespaces
https://docs.github.com/en/codespaces/developing-in-a-codespace/working-collaboratively-in-a-codespace
https://civitai.com/
https://huggingface.co/runwayml/stable-diffusion-v1-5


# How to run Stable Diffusion in GitHub Codespaces 🎨

Setup your own Stable Diffusion instance in the cloud to generate AI images in minutes using [GitHub Codespaces](https://github.com/features/codespaces). **You don’t need a powerful GPU or a fast internet connection.**

<img src="assets/banner.png" />

## Overview

- **⏱️ Estimated Setup Time**: 7 minutes
- ♟️ A GitHub account is required.
- 🤗 This guide is beginner friendly, but it might help to have some experience using a terminal.

## Getting Started

### Step 1: Create a Codespace

We'll be using an open source UI with over 25k stars and 280 contributers for our setup.

1. Navigate to the [AUTOMATIC1111/stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui) repo. Click on the **Code** dropdown button, navigate to the **Codespaces** tab, and click **New with options...**
2. Leave everything as is, but change the machine type to **8-core • 16GB RAM • 64GB storage**. *This is the minimum machine type required to run Stable Diffusion. If you don't have this option, please read the FAQ below.*
3. Create codespace. This should launch a VS Code editor in a new tab.

### Step 2: Install dependencies

Install the libgl1 dependency in your new Codespace by executing the following command in your Codespace terminal.

- If you don't know how to open the terminal, click the burger icon in the top left corner, hover over **Terminal**, and click **New Terminal**. Paste the following command and press enter. This will download the required libgl1 package.

    ```
    sudo apt-get update && sudo apt-get install libgl1
    ```

### Step 3: Download a Stable Diffusion model

Next, we're going to download a Stable Diffusion model (a checkpoint file) from [HuggingFace](https://huggingface.co) and put it in the `models/Stable-diffusion` folder. These models are often big (2-10GB), so here's a trick to download a model and store it in your Codespace environment in seconds without using your own internet bandwidth.

1. Find a model you want to use in HuggingFace. It could be the general purpose Stable Diffusion model [stabilityai/stable-diffusion-2-1](https://huggingface.co/stabilityai/stable-diffusion-2-1) or a fine-tuned model such as [prompthero/openjourney-v2](https://huggingface.co/prompthero/openjourney-v2).
2. Once you find a model you want to work with, click on the **Files and versions tab** and look for a file that ends with `.ckpt`. Click that model's link and you'll be directed to that checkpoint file's page.
3. Right click the **download** link and copy the URL.

    <img src="assets/hf_download_link.png" width="500" />
4. Back in your Codespace terminal, navigate to the `models/Stable-diffusion` folder and download the model in this folder using the following command (replace the link below with the URL you copied if you want).

    ```
    cd models/Stable-diffusion && wget https://huggingface.co/prompthero/openjourney-v2/resolve/main/openjourney-v2.ckpt && cd ../..
    ```

### Step 4: Launch the UI

Your setup is almost done! Use the command below in your Codespace terminal to launch the UI. It'll take a few minutes to install dependencies and launch the app.

```
./webui.sh --skip-torch-cuda-test --precision full --no-half
```

You'll get a link to the UI application in your terminal once everything is installed. If you're on Windows, you can "ctrl + click" the link. If you're on Mac, you can "cmd + click" to open the link.

<details>
    <summary>Click to see example</summary>
    
<img src="assets/output.png" width="500" />
</details>

**✅ If everything went smoothly, you should have access to the UI where you can start generating images!**

<img src="assets/ui.png" width="700" />

### Step 5 (Optional): Stop Codespaces

To save on resources, make sure to stop or shutdown your Codespace instance once you're done using it. You can do this in the repo UI or using the [GitHub CLI tool](https://cli.github.com).

## FAQ

**Q. Is this free?**\
A. If you have a GitHub Pro account, you'll have access to the 8-core Codespaces machine type required for this. Otherwise, you'll have to setup billing for Codespaces. If you're a student, most universities will hook you up with a student developer account, which is essentially Pro.

**Q. Who is this guide for?**\
A. This guide is meant for people who want to use their own instance of Stable Diffusion (text-to-img, img-to-img, inpainting, etc) and who doesn't have a powerful computer or fast internet to follow the other existing local setup guides available.

**Q. Is my usage private?**\
A. Yes. Your Codespace instance is private to you.

**Q. Can't I just use Google Colab?**\
A. Sure, you can do that if you prefer. Although, there are performance differences and some people may find Colab difficult to use.

**Q. How long does it typically take to generate an image?**\
A. Since this guide uses CPU for inference, I found that it usually takes 2-3 minutes for text-to-image generation (whereas GPU inference will take a few seconds).

**Q. Can I use a GPU in Codespaces?**\
A. Apparently it's possible to configure your Codespaces environment with a GPU (which should speed up performance considerably), but I've only done surface level research on how to do this. When I have more time I'll look into how you can use GPUs in Codespaces and apply that to this guide.

**Q. What if I want to use my own fine-tuned model that I have on my local machine, not one from HuggingFace?**\
A. You can drag and drop your custom model from your local computer to your VSCode editor. This may take awhile, depending on your internet speed. You can also host your model online and download it remotely to your Codespace environment.

**Q. Where can I find other fine-tuned ML models based on Stable Diffusion?**\
A. Explore HuggingFace https://huggingface.co/models?pipeline_tag=text-to-image&sort=likes or other similar services.

**Q. I have questions, who can I ask?**\
A. Either file an issue or create a new discussion in this repo with your question or comment.

## Disclaimer

*The information provided in this guide is intended for educational purposes only. This guide is not meant to be an endorsement or advertisement for GitHub Codespaces or AUTOMATIC1111's UI. It is simply intended to educate the community on how to run Stable Diffusion models in the cloud based on the limited research conducted. Please note that this may not be the optimal way to use Stable Diffusion, but it does provide an option for those with limited access to compute resources. Additionally, this tutorial is intended to follow the [terms of service of GitHub Codespaces](https://docs.github.com/en/site-policy/github-terms/github-terms-for-additional-products-and-features#codespaces).*




# Stable Diffusion web UI
A web interface for Stable Diffusion, implemented using Gradio library.

![](screenshot.png)

## Features
[Detailed feature showcase with images](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Features):
- Original txt2img and img2img modes
- One click install and run script (but you still must install python and git)
- Outpainting
- Inpainting
- Color Sketch
- Prompt Matrix
- Stable Diffusion Upscale
- Attention, specify parts of text that the model should pay more attention to
    - a man in a `((tuxedo))` - will pay more attention to tuxedo
    - a man in a `(tuxedo:1.21)` - alternative syntax
    - select text and press `Ctrl+Up` or `Ctrl+Down` (or `Command+Up` or `Command+Down` if you're on a MacOS) to automatically adjust attention to selected text (code contributed by anonymous user)
- Loopback, run img2img processing multiple times
- X/Y/Z plot, a way to draw a 3 dimensional plot of images with different parameters
- Textual Inversion
    - have as many embeddings as you want and use any names you like for them
    - use multiple embeddings with different numbers of vectors per token
    - works with half precision floating point numbers
    - train embeddings on 8GB (also reports of 6GB working)
- Extras tab with:
    - GFPGAN, neural network that fixes faces
    - CodeFormer, face restoration tool as an alternative to GFPGAN
    - RealESRGAN, neural network upscaler
    - ESRGAN, neural network upscaler with a lot of third party models
    - SwinIR and Swin2SR ([see here](https://github.com/AUTOMATIC1111/stable-diffusion-webui/pull/2092)), neural network upscalers
    - LDSR, Latent diffusion super resolution upscaling
- Resizing aspect ratio options
- Sampling method selection
    - Adjust sampler eta values (noise multiplier)
    - More advanced noise setting options
- Interrupt processing at any time
- 4GB video card support (also reports of 2GB working)
- Correct seeds for batches
- Live prompt token length validation
- Generation parameters
     - parameters you used to generate images are saved with that image
     - in PNG chunks for PNG, in EXIF for JPEG
     - can drag the image to PNG info tab to restore generation parameters and automatically copy them into UI
     - can be disabled in settings
     - drag and drop an image/text-parameters to promptbox
- Read Generation Parameters Button, loads parameters in promptbox to UI
- Settings page
- Running arbitrary python code from UI (must run with `--allow-code` to enable)
- Mouseover hints for most UI elements
- Possible to change defaults/mix/max/step values for UI elements via text config
- Tiling support, a checkbox to create images that can be tiled like textures
- Progress bar and live image generation preview
    - Can use a separate neural network to produce previews with almost none VRAM or compute requirement
- Negative prompt, an extra text field that allows you to list what you don't want to see in generated image
- Styles, a way to save part of prompt and easily apply them via dropdown later
- Variations, a way to generate same image but with tiny differences
- Seed resizing, a way to generate same image but at slightly different resolution
- CLIP interrogator, a button that tries to guess prompt from an image
- Prompt Editing, a way to change prompt mid-generation, say to start making a watermelon and switch to anime girl midway
- Batch Processing, process a group of files using img2img
- Img2img Alternative, reverse Euler method of cross attention control
- Highres Fix, a convenience option to produce high resolution pictures in one click without usual distortions
- Reloading checkpoints on the fly
- Checkpoint Merger, a tab that allows you to merge up to 3 checkpoints into one
- [Custom scripts](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Custom-Scripts) with many extensions from community
- [Composable-Diffusion](https://energy-based-model.github.io/Compositional-Visual-Generation-with-Composable-Diffusion-Models/), a way to use multiple prompts at once
     - separate prompts using uppercase `AND`
     - also supports weights for prompts: `a cat :1.2 AND a dog AND a penguin :2.2`
- No token limit for prompts (original stable diffusion lets you use up to 75 tokens)
- DeepDanbooru integration, creates danbooru style tags for anime prompts
- [xformers](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Xformers), major speed increase for select cards: (add `--xformers` to commandline args)
- via extension: [History tab](https://github.com/yfszzx/stable-diffusion-webui-images-browser): view, direct and delete images conveniently within the UI
- Generate forever option
- Training tab
     - hypernetworks and embeddings options
     - Preprocessing images: cropping, mirroring, autotagging using BLIP or deepdanbooru (for anime)
- Clip skip
- Hypernetworks
- Loras (same as Hypernetworks but more pretty)
- A separate UI where you can choose, with preview, which embeddings, hypernetworks or Loras to add to your prompt 
- Can select to load a different VAE from settings screen
- Estimated completion time in progress bar
- API
- Support for dedicated [inpainting model](https://github.com/runwayml/stable-diffusion#inpainting-with-stable-diffusion) by RunwayML
- via extension: [Aesthetic Gradients](https://github.com/AUTOMATIC1111/stable-diffusion-webui-aesthetic-gradients), a way to generate images with a specific aesthetic by using clip images embeds (implementation of [https://github.com/vicgalle/stable-diffusion-aesthetic-gradients](https://github.com/vicgalle/stable-diffusion-aesthetic-gradients))
- [Stable Diffusion 2.0](https://github.com/Stability-AI/stablediffusion) support - see [wiki](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Features#stable-diffusion-20) for instructions
- [Alt-Diffusion](https://arxiv.org/abs/2211.06679) support - see [wiki](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Features#alt-diffusion) for instructions
- Now without any bad letters!
- Load checkpoints in safetensors format
- Eased resolution restriction: generated image's dimensions must be a multiple of 8 rather than 64
- Now with a license!
- Reorder elements in the UI from settings screen
- [Segmind Stable Diffusion](https://huggingface.co/segmind/SSD-1B) support

## Installation and Running
Make sure the required [dependencies](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Dependencies) are met and follow the instructions available for:
- [NVidia](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-NVidia-GPUs) (recommended)
- [AMD](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-AMD-GPUs) GPUs.
- [Intel CPUs, Intel GPUs (both integrated and discrete)](https://github.com/openvinotoolkit/stable-diffusion-webui/wiki/Installation-on-Intel-Silicon) (external wiki page)
- [Ascend NPUs](https://github.com/wangshuai09/stable-diffusion-webui/wiki/Install-and-run-on-Ascend-NPUs) (external wiki page)

Alternatively, use online services (like Google Colab):

- [List of Online Services](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Online-Services)

### Installation on Windows 10/11 with NVidia-GPUs using release package
1. Download `sd.webui.zip` from [v1.0.0-pre](https://github.com/AUTOMATIC1111/stable-diffusion-webui/releases/tag/v1.0.0-pre) and extract its contents.
2. Run `update.bat`.
3. Run `run.bat`.
> For more details see [Install-and-Run-on-NVidia-GPUs](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-NVidia-GPUs)

### Automatic Installation on Windows
1. Install [Python 3.10.6](https://www.python.org/downloads/release/python-3106/) (Newer version of Python does not support torch), checking "Add Python to PATH".
2. Install [git](https://git-scm.com/download/win).
3. Download the stable-diffusion-webui repository, for example by running `git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git`.
4. Run `webui-user.bat` from Windows Explorer as normal, non-administrator, user.

### Automatic Installation on Linux
1. Install the dependencies:
```bash
# Debian-based:
sudo apt install wget git python3 python3-venv libgl1 libglib2.0-0
# Red Hat-based:
sudo dnf install wget git python3 gperftools-libs libglvnd-glx 
# openSUSE-based:
sudo zypper install wget git python3 libtcmalloc4 libglvnd
# Arch-based:
sudo pacman -S wget git python3
```
2. Navigate to the directory you would like the webui to be installed and execute the following command:
```bash
wget -q https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh
```
3. Run `webui.sh`.
4. Check `webui-user.sh` for options.
### Installation on Apple Silicon

Find the instructions [here](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Installation-on-Apple-Silicon).

## Contributing
Here's how to add code to this repo: [Contributing](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Contributing)

## Documentation

The documentation was moved from this README over to the project's [wiki](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki).

For the purposes of getting Google and other search engines to crawl the wiki, here's a link to the (not for humans) [crawlable wiki](https://github-wiki-see.page/m/AUTOMATIC1111/stable-diffusion-webui/wiki).

## Credits
Licenses for borrowed code can be found in `Settings -> Licenses` screen, and also in `html/licenses.html` file.

- Stable Diffusion - https://github.com/Stability-AI/stablediffusion, https://github.com/CompVis/taming-transformers
- k-diffusion - https://github.com/crowsonkb/k-diffusion.git
- Spandrel - https://github.com/chaiNNer-org/spandrel implementing
  - GFPGAN - https://github.com/TencentARC/GFPGAN.git
  - CodeFormer - https://github.com/sczhou/CodeFormer
  - ESRGAN - https://github.com/xinntao/ESRGAN
  - SwinIR - https://github.com/JingyunLiang/SwinIR
  - Swin2SR - https://github.com/mv-lab/swin2sr
- LDSR - https://github.com/Hafiidz/latent-diffusion
- MiDaS - https://github.com/isl-org/MiDaS
- Ideas for optimizations - https://github.com/basujindal/stable-diffusion
- Cross Attention layer optimization - Doggettx - https://github.com/Doggettx/stable-diffusion, original idea for prompt editing.
- Cross Attention layer optimization - InvokeAI, lstein - https://github.com/invoke-ai/InvokeAI (originally http://github.com/lstein/stable-diffusion)
- Sub-quadratic Cross Attention layer optimization - Alex Birch (https://github.com/Birch-san/diffusers/pull/1), Amin Rezaei (https://github.com/AminRezaei0x443/memory-efficient-attention)
- Textual Inversion - Rinon Gal - https://github.com/rinongal/textual_inversion (we're not using his code, but we are using his ideas).
- Idea for SD upscale - https://github.com/jquesnelle/txt2imghd
- Noise generation for outpainting mk2 - https://github.com/parlance-zz/g-diffuser-bot
- CLIP interrogator idea and borrowing some code - https://github.com/pharmapsychotic/clip-interrogator
- Idea for Composable Diffusion - https://github.com/energy-based-model/Compositional-Visual-Generation-with-Composable-Diffusion-Models-PyTorch
- xformers - https://github.com/facebookresearch/xformers
- DeepDanbooru - interrogator for anime diffusers https://github.com/KichangKim/DeepDanbooru
- Sampling in float32 precision from a float16 UNet - marunine for the idea, Birch-san for the example Diffusers implementation (https://github.com/Birch-san/diffusers-play/tree/92feee6)
- Instruct pix2pix - Tim Brooks (star), Aleksander Holynski (star), Alexei A. Efros (no star) - https://github.com/timothybrooks/instruct-pix2pix
- Security advice - RyotaK
- UniPC sampler - Wenliang Zhao - https://github.com/wl-zhao/UniPC
- TAESD - Ollin Boer Bohan - https://github.com/madebyollin/taesd
- LyCORIS - KohakuBlueleaf
- Restart sampling - lambertae - https://github.com/Newbeeer/diffusion_restart_sampling
- Hypertile - tfernd - https://github.com/tfernd/HyperTile
- Initial Gradio script - posted on 4chan by an Anonymous user. Thank you Anonymous user.
- (You)
