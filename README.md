# WissDiff: High-Resolution Precipitation Enhancement through Tiled Diffusion

WissDiff is a generative model designed to significantly enhance the resolution of regional precipitation data using advanced diffusion-based image synthesis techniques. Developed collaboratively by Yuhao Liu and guided by Professor Ashok Veeraraghavan, this research effectively transforms low-resolution meteorological data into precise, high-resolution precipitation maps.

To overcome VRAM limitations associated with large-scale diffusion models (such as UNet), WissDiff adopts a tiled diffusion strategy inspired by Jimenez et al. (2023). This method partitions extensive precipitation maps into smaller patches, individually processes these patches, and subsequently merges them seamlessly at each diffusion step.

## Direct Pixel Merging and Tiled Diffusion

WissDiff employs direct pixel merging at each diffusion step to ensure artifact-free results with seamless transitions and consistent boundary blending across adjacent patches. The primary mechanisms include:

- **Gaussian Masking**: Each patch is weighted with a Gaussian mask, emphasizing its center and smoothly tapering toward edges to facilitate seamless integration.
- **Controlled Merging**: Unlike traditional noise-prediction merging methods, WissDiff directly merges pixels at each diffusion step, maintaining boundary integrity and preventing noise-induced artifacts.
- **Optimized Hyperparameters**: Hyperparameters including patch size (256×256 pixels), stride (192×192 pixels), and batch size are carefully optimized to balance computational efficiency with VRAM constraints.

Currently, generating a high-resolution continental-scale precipitation map (such as for the contiguous United States) requires approximately 14 hours. Despite this computational demand, the tiled diffusion strategy enables high-resolution large-scale applications previously constrained by hardware limitations.

## Key Features

- **Enhanced Resolution**: Transforms low-resolution precipitation data into highly detailed, high-resolution maps.
- **Seamless Boundary Integration**: Utilizes direct pixel merging combined with Gaussian masking at each diffusion step for smooth transitions between adjacent patches.
- **StableSR-Inspired Techniques**: Incorporates methodologies from StableSR to ensure precise boundary consistency and enhance the accuracy across patch interfaces.

## Results and Visualizations

The visualizations below demonstrate WissDiff’s ability to generate artifact-free, high-resolution precipitation maps:

### Continental-Scale Tiled Diffusion Results

![Tiled diffusion on CONUS]([https://github.com/user-attachments/files/19579214/tiled_diffusion.1.pdf](https://github.com/user-attachments/assets/464aaffc-53bd-40b7-9c6d-91ab68034345))

*Figure*: Tiled diffusion results over the contiguous United States (CONUS): (a) Cold front, 2015-12-02 UTC; (b) Hailstorm, 2015-06-11 UTC; (c) Storm Bill, 2015-06-08 UTC. (Patch Size: 256×256 pixels, Stride: 192×192 pixels)

### High-Resolution Patch-Merging Results

| **WissDiff Merge Result** | **Ground Truth** |
|---------------------------|------------------|
| ![WissDiff Merge](https://github.com/user-attachments/assets/7def1d16-724e-4353-ba20-9bfa7864ba8b) | ![Ground Truth](https://github.com/user-attachments/assets/eb47a03f-2004-4b49-a6b4-3309f16debcf) |

*(Image Size: 1024×1024 pixels, Patch Size: 256×256 pixels, Stride: 192×192 pixels)*

## Acknowledgments

This research was conducted collaboratively with Professor Ashok Veeraraghavan. Integration of direct pixel-merging techniques inspired by Jimenez et al. (2023), coupled with StableSR-based methodologies, has significantly enhanced both the resolution and boundary consistency of the synthesized precipitation maps.


