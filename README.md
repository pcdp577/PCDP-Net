# PCDP-Net

**Processing-Condition Prior-Guided Restoration of Dynamically Degraded Gear-Surface Visual Signals**

PCDP combines direction-factorized image restoration with noisy processing-condition information to recover gear-surface visual signals degraded during high-speed rotation. This repository provides the project overview and access to the basic restoration dataset.

## Dataset Download

**[Gear-Surface Restoration Dataset: ZIP on Google Drive](https://drive.google.com/file/d/1XxiHBFhh3eHAjfOHhgfzMiSgvbUI5NpP/view)**

Archive: `GearSurface_Restoration_Dataset.zip`.

The dataset contains degraded-sharp image pairs acquired with a self-built non-contact imaging system and sample-matched processing-condition priors. Degraded images were captured during high-speed rotation, and sharp reference images were captured under static conditions.

| Split | Paired samples | Sample IDs |
| --- | ---: | --- |
| Train | 1,067 | `000001`-`001067` |
| Test | 266 | `001068`-`001333` |
| Total | 1,333 | |

Each sample includes one degraded image, one sharp reference image, and one prior TXT file. Images are 8-bit grayscale BMP files, 320 pixels wide and 540 pixels high.

### Directory Structure

```text
dataset/
  README.md
  blur/
    train/
    test/
  sharp/
    train/
    test/
  0Parameter/
    train/
    test/
```

### Sample Matching

Match files by their six-digit sample ID within the same split:

```text
blur/train/000001.bmp
sharp/train/000001.bmp
0Parameter/train/000001.txt
```

Use `blur` as the restoration input, `sharp` as the reference target, and `0Parameter` as the corresponding scalar prior.

### Processing-Condition Prior

Each TXT file contains one field, for example:

```text
motion_blur_extent: 18
```

`motion_blur_extent` is the equivalent image-plane displacement *s*, estimated from the acquisition parameters and imaging calibration. Values are provided before model-specific normalization. Compute any normalization statistics from the training split only.

## Method Overview

- **ILDFA** is the direction-factorized backbone for complementary directional feature extraction and horizontal output-intensity correction.
- **PCPIM** stabilizes noisy equivalent image-plane displacement and combines image-conditioned correction with stage-wise prior injection.
- **HBF-PSNRLoss** supplements spatial reconstruction supervision with horizontal-biased frequency supervision during training.

The study evaluates restoration quality and inference efficiency, adaptation to the public R-RMBD benchmark, and the contribution of restored training images to downstream defect detection.

## Code and Trained Models

Training and inference code, configurations, and trained weights are being prepared and are not yet released. This page will be updated when these resources are ready.

## Citation

Bibliographic details will be added after publication.

## Contact

For questions about the dataset or method, please [open an issue](https://github.com/pcdp577/PCDP-Net/issues).
