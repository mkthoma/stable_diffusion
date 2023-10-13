# Stable Diffusion using Textual Inversion

This is repo contains code that uses the Stable Diffusion model to generate images based on a textual prompt. It includes an option to apply vibrance loss to the generated images. The script uses the CLIP model for text and image embeddings and the Stable Diffusion model for image generation.

You'll need to have a CUDA-enabled GPU for faster image generation. If you don't have a GPU, you can still run the script on CPU, but it will be significantly slower.

## Usage
- Import the necessary libraries and load the models.
- Set the torch_device variable to "cuda" if you have a GPU, or "cpu" if you don't.
- Define the style files you want to use for image generation.
- Configure other parameters like the number of inference steps, guidance scale, and random seed values.
- Define custom loss functions (optional).
- Implement the generate_with_embs and generate_images functions to generate images based on the textual prompts and styles.
- Define the image_generator function to generate images with or without a custom loss.

## Styles using learned embeddings
The different styles in which the same prompt has been generated was downloaded from the [HuggingFace SD Concepts Library](https://huggingface.co/sd-concepts-library). The different styles used are:
1. [Arcane Style](https://huggingface.co/sd-concepts-library/arcane-style-jv)
2.  [Midjourney Style](https://huggingface.co/sd-concepts-library/midjourney-style)
3. [Oil Style](https://huggingface.co/sd-concepts-library/oil-style)
4. [Dr Stange Style](https://huggingface.co/sd-concepts-library/dr-strange)
5. [Birb Style](https://huggingface.co/sd-concepts-library/birb-style)   

## Functionality
The script generates images based on textual prompts and specified styles.
You can choose to apply vibrance loss to the generated images by selecting "Yes" when using the Gradio interface. The generated images are displayed in rows, showing the results with and without loss if applicable.

## Vibrancy Loss
Vibrance loss is a concept used in image generation to enhance the vibrancy and colorfulness of generated images. It is a custom loss function applied during the image generation process to encourage the model to produce more visually appealing and colorful results. This loss function is particularly useful when the generated images appear dull or lack color variation.

The core idea behind vibrance loss is to measure the diversity and intensity of colors within an image. It does so by evaluating the standard deviation of color channels (e.g., Red, Green, Blue) in the generated image. The greater the standard deviation, the more varied and vibrant the colors in the image.

Vibrance loss encourages the model to generate images with higher color diversity and intensity. It penalizes images that are visually uninteresting, monochromatic, or lack color richness.

## Customization
You can customize the script by modifying the following:

- style_files: Add or remove style files for different image styles.
- seed_values: Change the random seed values for image generation.
- height and width: Adjust the image dimensions.
- num_inference_steps: Change the number of denoising steps.
- guidance_scale: Adjust the scale for classifier-free guidance.
- loss_function: Implement custom loss functions for image conditioning.

The live implementation on HuggingFace can be found [here](https://huggingface.co/spaces/mkthoma/StableDiffusion_with_VibranceLoss).

## Examples Generated

#### Prompt - `dog sitting on a bench`

![image](https://github.com/mkthoma/stable_diffusion/assets/135134412/27024b20-98dd-4d04-8012-226d70402fe4)

#### Prompt - `cat on a bike`

![download](https://github.com/mkthoma/stable_diffusion/assets/135134412/ca405001-0fce-4b4b-9ae8-7dd120967054)
