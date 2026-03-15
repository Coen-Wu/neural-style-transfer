# Neural Style Transfer: Van Gogh vs. Ghibli

This project implements Neural Style Transfer (NST) using VGG19 network to synthesize the content of a real-world image with the artistic styles of Van Gogh and Studio Ghibli.

## Key Implementation

Instead of a simple implementation, this project is designed as a controlled experiment to explore the following dimensions:

Artistic Style Comparison: Comparing the synthesis performance of VGG19 on highly textured styles (Van Gogh's oil painting) versus clean, contour-based styles (Studio Ghibli's animation).

Hyperparameter Optimization: Conducted experiments with various $\alpha$ and $\beta$ settings to achieve a perfect visual balance between the original content and the target artistic style.

Hyperparameter Exploration ($\gamma$ - TV Loss): A core focus of this project is the investigation of Total Variation (TV) Loss. By adjusting the $\gamma$ parameter, I analyzed its effectiveness in noise reduction across different artistic domains.

## Results & Insights

### 1. Domain Sensitivity Analysis

The experiment reveals that the quality of results depends on the target style's visual characteristics:

* High Texture (Van Gogh): The Gram Matrix used in Style Loss effectively captures and reproduces the thick brushstrokes and vivid color textures of oil paintings.

* Structural Line Art (Studio Ghibli): The model struggled to transfer this style. Findings suggest that animation styles rely on clean lines and character proportions, which are often distorted by texture-oriented loss functions.

### 2. Hyperparameter Exploration: Tuning for Balance and Clarity

* Balancing Content & Style (α and β)

  * Goal: I tested various ratios of α (content weight) and β (style weight) to find the "sweet spot".
  * Result: This ensures the generated image preserves its original structural integrity while successfully adopting the                 target artistic colors and textures.

* The "Gamma (γ)" Innovation for Noise Control

  * Goal: To prevent the model from generating excessive "noise" or "red dots" when attempting to imitate complex,
          high-contrast styles.
  * Result: This hyperparameter failed to enahance the quality of generated pictures with Ghibli style. This is because                  Ghibli’s style is made of smooth blocks of color, not rough textures. Therefore, "denoising" hyperparameters                 like $\gamma$ don't have much work to do on an already smooth style.

### 3. Comprehensive Analysis

For a deep dive into the analysis, please refer to the **[Project Slides (PDF)](./project_slides.pdf)**.

## Techniques Used

* VGG19 Model: Used as a feature extractor to pick out important shapes and patterns from the images. 

* Gram Matrix: Used to calculate and "record" the artistic style and textures. 

* Gradient Descent: Updated the pixels of the new image step-by-step to match both content and style. 

* Hyperparameter Experiments: Ran experiments on $\alpha$, $\beta$, and $\gamma$ to find the best balance and reduce noise.

## Libraries
tensorflow, numPy, matplotlib, PIL, scipy 

## Project Structure

```text
├── data/                  # Content and Style images (Van Gogh, Ghibli, NCKU campus scenery)
├── output/                  # Genarated images with various hyperparameters
├── Style_Transfer.ipynb   # Core implementation
├── project_slides.pdf   # Detailed experimental report and analysis
└── README.md              # Project overview and insights
