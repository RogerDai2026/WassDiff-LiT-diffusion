Here's an updated README to reflect your direct patch-merging approach in WissDiff:

---

# WissDiff

**WissDiff** is a research-driven project focused on improving the resolution of regional precipitation data using advanced image synthesis techniques. The project leverages diffusion models to transform low-resolution weather data into high-resolution precipitation images, enhancing data clarity and detail.

## Project Overview

Collaborating with Yuhao Liu, This projects employs novel methods for pixel merging and patch integration to maintain seamless transitions across high-resolution precipitation maps:

- **Diffusion Model**: A diffusion model is applied to train on low-resolution weather data, generating detailed, high-resolution precipitation images. The model is implemented using PyTorch.
- **StableSR-Inspired Pixel Merging**: Rather than relying on traditional noise prediction methods, WissDiff directly merges each patch at each diffusion step, allowing for consistent, artifact-free boundary blending between patches.
- **Enhanced Boundary Consistency**: The merging process refines boundaries across adjacent patches without the need for noise prediction, providing a smoother and more accurate visualization of precipitation patterns.

## Key Features

1. **Resolution Enhancement**  
   Converts low-resolution data into high-resolution precipitation maps, improving insights and visibility of weather data.

2. **Direct Pixel Merging at Each Diffusion Step**  
   By merging patches directly at each step, WissDiff maintains boundary consistency, creating a unified map from small, high-resolution patches without introducing noise artifacts.

3. **Integration of StableSR Techniques**  
   StableSR's methods assist in refining boundaries, ensuring high fidelity and smooth transitions between patches across the entire image.

This approach allows for controlled merging at each diffusion step, yielding consistent boundaries and maintaining high-resolution details across patches.


## Results 
1. **image size 1024 *1024, patch 256*256, stride 192*192**
   wassdiff merge
<img width="982" alt="Screenshot 2024-11-13 at 12 53 58 AM" src="https://github.com/user-attachments/assets/7def1d16-724e-4353-ba20-9bfa7864ba8b">
   groud truth
<img width="1063" alt="Screenshot 2024-11-13 at 12 58 12 AM" src="https://github.com/user-attachments/assets/eb47a03f-2004-4b49-a6b4-3309f16debcf">


## Installation and Usage

1. **Clone the Repository**
   ```bash
   git clone https://github.com/yourusername/wissdiff.git<img width="982" alt="Screenshot 2024-11-13 at 12 53 58 AM" src="https://github.com/user-attachments/assets/3c686213-adf2-400f-9ae0-510bd18a74b7">

   ```

2. **Requirements**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run Model**
   ```bash

   python run_diffusion.py --input data/low_res_weather_data --output results/high_res_precipitation
   ```

## Acknowledgments

This project was developed in collaboration with Professor Ashok Veeraraghavan. The innovative patch-merging process, bypassing noise prediction, and StableSR techniques significantly improved the accuracy and resolution of precipitation data maps.

---
