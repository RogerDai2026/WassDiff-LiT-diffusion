WissDiff is a generative model focused on enhancing the resolution of regional precipitation data using advanced diffusion-based image synthesis techniques. Developed in collaboration with Yuhao Liu and under the guidance of Professor Ashok Veeraraghavan, WissDiff transforms low-resolution weather data into detailed, high-resolution precipitation images.

In wassdiff model, to addresses the VRAM limitations inherent in large-scale diffusion models (such as UNet), we employed a tiled diffusion strategy inspired by \citet{jimenez2023mixture}. This method partitions large-scale precipitation maps into smaller, manageable patches, processes them individually, and seamlessly merges them at each diffusion step.

Direct Pixel Merging and Tiled Diffusion
To achieve artifact-free and consistent boundary blending across adjacent patches, WissDiff implements direct pixel merging at every diffusion step:
* Gaussian Masking: Each patch receives a Gaussian weighting mask emphasizing its center while smoothly tapering toward its boundaries, ensuring seamless transitions.
* Controlled Merging: Instead of relying on traditional noise prediction methods, patches are merged directly during each diffusion step. This maintains high-fidelity boundaries without introducing noise-related artifacts.
* Hyperparameters: Patch size (256 pixels), stride (192 pixels for sufficient overlap), and batch size are optimized to balance computational efficiency and VRAM constraints.
Currently, generating a full continental-scale high-resolution precipitation map (e.g., the contiguous United States) takes approximately 14 hours. Despite this computational cost, the tiled diffusion approach successfully enables continental-scale applications previously constrained by hardware limitations.
Key Features
* Resolution Enhancement: Converts low-resolution precipitation data into high-resolution, detailed maps.
* Seamless Boundary Integration: Utilizes direct pixel merging and Gaussian masking at each diffusion step for smooth transitions between patches.
* StableSR-Inspired Techniques: Incorporates methodologies inspired by StableSR to refine and maintain accurate boundary consistency across patches.
Results
The following visualizations demonstrate WissDiff's effectiveness in generating artifact-free, high-resolution precipitation maps using direct patch merging and tiled diffusion strategies.
Continental-scale Tiled Diffusion Results
[tiled_diffusion.pdf](https://github.com/user-attachments/files/19579103/tiled_diffusion.pdf)
(Patch Size: 256×256, Stride: 192×192)
Figure: Tiled diffusion on the contiguous United States (CONUS): (a) A cold front, 2015-12-02 UTC; (b) A hailstorm, 2015-06-11 UTC; and (c) Storm Bill, 2015-06-08 UTC.
High-Resolution Patch-Merging Results
<table> <tr> <td><strong>WissDiff Merge Result</strong></td> <td><strong>Ground Truth</strong></td> </tr> <tr> <td><img src="https://github.com/user-attachments/assets/7def1d16-724e-4353-ba20-9bfa7864ba8b" width="400" alt="WissDiff Merge"></td> <td><img src="https://github.com/user-attachments/assets/eb47a03f-2004-4b49-a6b4-3309f16debcf" width="400" alt="Ground Truth"></td> </tr> </table>
(Image Size: 1024×1024, Patch Size: 256×256, Stride: 192×192)
Acknowledgments
This work was developed collaboratively with Professor Ashok Veeraraghavan. The integration of direct pixel-merging techniques, inspired by \citet{jimenez2023mixture}, and StableSR-based methodologies significantly enhanced the resolution and boundary consistency of generated precipitation maps.


