# PostShot vs LichtFeld Studio: Case Studies

Currently, two of the most popular pieces of software used to create 3DGS are Postshot by Jawset (paid) and the open source LichtFeld Studio (free). The goal of this project is to compare these two pieces of software to see which one is better and if it’s worth it to spend that extra money on Postshot.

---

## Project Overview

To compare the Postshot and LichtFeld studio, 3D Gaussian Splats were created using both softwares for objects with qualities that are difficult for traditional photogrammetry to capture. These qualities were fine detail, transparancy and reflections. The rendered images were compared to the ground truth using PSNR, MSE and SSIM and a perceptual evaluation was conducted by viewing the splats in 3D to note inconsistencies or aspects of the result not captured by the aforementioned metrics.


---

### Visual Comparisons and analysis of results

**Date:** 21 May 2026

Comparison images were rendered for PSNR, MSE, and SSIM calculations. All images had a slight offset, which was manually corrected in Affinity Photo. Background areas were cropped to focus evaluation on object reconstruction quality.

> **Note:** LichtFeld Studio lacks a native image export function. Rendered images were captured as 3840 × 2160 screenshots. Some inconsistencies between images resulted from virtual camera distortion.

#### Figure 1: Fake Plant Comparison
*Left: Real | Middle: PostShot | Right: LichtFeld Studio*

<img width="902" height="301" alt="Skärmbild 2026-05-21 235537" src="https://github.com/user-attachments/assets/08193d9a-eb0a-4106-ab40-a4a41726d528" />

#### Figure 2: Drinking Glass Comparison
*Left: Real | Middle: PostShot | Right: LichtFeld Studio*

<img width="894" height="451" alt="Skärmbild 2026-05-21 235723" src="https://github.com/user-attachments/assets/cf53b678-77d4-407d-9fcc-1b4299c93592" />

#### Figure 3: Metal Pot Comparison
*Left: Real | Middle: PostShot | Right: LichtFeld Studio*

<img width="953" height="161" alt="image" src="https://github.com/user-attachments/assets/97b92c26-9d04-4461-af11-33c4dfaa2132" />

### Quantitative Analysis

#### Fake Plant

| Metric | PostShot | LichtFeld Studio |
|--------|----------|------------------|
| PSNR | 20.361 | 16.369 |
| MSE | 598.338 | 1500.227 |
| SSIM | 0.630 | 0.306 |

#### Drinking Glass

| Metric | PostShot | LichtFeld Studio |
|--------|----------|------------------|
| PSNR | 21.994 | 18.357 |
| MSE | 410.857 | 949.199 |
| SSIM | 0.611 | 0.481 |

#### Metal Pot

| Metric | PostShot | LichtFeld Studio |
|--------|----------|------------------|
| PSNR | 19.087 | 15.294 |
| MSE | 802.466 | 1921.801 |
| SSIM | 0.596 | 0.311 |

---

### LichtFeld Studio Results

**Date:** 20 May 2026

**Workflow:** Tracking performed in RealityScan, training in LichtFeld Studio.

| Object | Tracking Time | Training Time | Splat Count | .ply File Size |
|--------|---------------|---------------|-------------|----------------|
| Fake Plant | ~4 min | 1h 20m 10s | 3.00 M | 726 564 kB |
| Drinking Glass | ~4 min | 1h 11m 38s | 3.00 M | 726 564 kB |
| Metal Pot | ~4 min | 1h 10m 49s | 3.00 M | 726 564 kB |

#### Observations

**Fake Plant:**
- Significantly fewer disconnected Gaussians compared to PostShot
- Cleaner overall reconstruction

**Metal Pot:**
- Improved but still slightly blurry and inconsistent

**Drinking Glass:**
- Better separation of object from background

---

### PostShot Results

**Date:** 19 May 2026

| Object | Training Time | Splat Count | .ply File Size |
|--------|----------------|-------------|-----------|
| Fake Plant | 42–43 min | 3.00 M | 691 408 kB |
| Drinking Glass | 46–47 min | 3.00 M | 691 408 kB |
| Metal Pot | 45–46 min | 3.00 M | 691 408 kB |

#### Observations

**Fake Plant:**
- Strong reconstruction in still frame and from similar angles to that of the camera
- Disconnected Gaussians present around the plant
- Struggled to render the pot, possibly due to lack of angle of it.

<img width="634" height="705" alt="Skärmbild 2026-05-19 222443" src="https://github.com/user-attachments/assets/c187326d-49c1-4457-aa2c-4c9b4f9f4967" />


<img width="1054" height="654" alt="Skärmbild 2026-05-19 222510" src="https://github.com/user-attachments/assets/b7d79503-cf75-420e-a759-e765dd1b3e29" />

**Glass:**
- Decent, though blurry, reconstruction of the glass from angles similar to original camera angles
- Inconsistent Gaussians when rotating around the object
- Disconnected Gaussians near the top of the glass
- Significant background elements incorrectly merged with the object
- Noticeable "fuzz" artifact visible inside the glass

<img width="503" height="507" alt="Skärmbild 2026-05-19 234117" src="https://github.com/user-attachments/assets/d1c2e282-8eb2-452a-8b23-be5c60950e29" />

<img width="674" height="298" alt="Skärmbild 2026-05-19 234202" src="https://github.com/user-attachments/assets/05429a76-5eb7-4831-a7bd-d2e98b5f8add" />![Uploading Skärmbild 2026-05-21 235537.png…]()


<img width="646" height="565" alt="Skärmbild 2026-05-19 234339" src="https://github.com/user-attachments/assets/680a3402-9e9f-4832-88cb-4c4f88103608" />

<img width="583" height="368" alt="Skärmbild 2026-05-19 234222" src="https://github.com/user-attachments/assets/25d95186-3ea3-4b89-9395-d8df6fcc435d" />


**Metal Pot:**
- Decent, though slightly blurry, reconstruction of the pot from angles similar to original camera angles, especially inside of the pot
- Inconsistent Gaussians when rotating around the object creating a popping effect on the outside of the pot
- Disconnected Gaussians above the pot
- Exterior surface lacked smoothness
- Light fuzz present inside the pot

<img width="678" height="492" alt="Skärmbild 2026-05-20 003758" src="https://github.com/user-attachments/assets/adb66fe7-a4a0-4e61-a58a-1bbb8f742480" />

<img width="913" height="545" alt="Skärmbild 2026-05-20 003648" src="https://github.com/user-attachments/assets/82950363-4ad9-4a26-a758-7bb1d02214bb" />

<img width="537" height="243" alt="Skärmbild 2026-05-20 004240" src="https://github.com/user-attachments/assets/f0172839-d601-4ac5-ab5c-752c61be5f81" />


---
## Gathering image data

**Date:** 19 May 2026

### Capture Conditions

Images were taken during daytime outside on a cloudy day in order to get even lighting. Even lighting ensures more consistency between different angles as the person taking photos does not occasionally block and reveal light.

### Choosing test objects

#### Object 1: Fake Plant
The fake plant offers a high level of detail with thin stems and leaves. 

#### Object 2: Drinking Glass
This drinking glass offers another complicated aspect of 3D-capture: transparency. With a transparent object, it can be difficult to determine what is part of the object itself and what is part of the background. Another added layer of complexity is that the glass has smudges and fingerprints on it, which was intentional, as this can make it even harder to determine what is part of the foreground or background.

#### Object 3: Metal Pot
Similarly to transparency, reflections can be very difficult to capture in 3D from videos, as it can be difficult to determine what is part of the object itself and what is simply being reflected on its surface. The pot was also dirty and smudged for the same reason as the glass.

<img width="916" height="284" alt="Skärmbild 2026-05-21 235403" src="https://github.com/user-attachments/assets/df3e5695-ac17-4f8d-a8cc-0a8aa8994cc9" />


### Camera Settings

| Setting | Value |
|---------|-------|
| Device | iPhone 13 Pro |
| Shutter Speed | 1/2000s |
| ISO | 48 |
| Resolution | 3840 × 2160 px |
| Format | Video (converted to image sequences) |

**Rationale:**
- **1/2000s shutter speed** ensured crisp footage with minimal motion blur
- **ISO 48** limited image noise
- **4K resolution** provided sufficient detail for reconstruction

Each video was between **1:03 and 1:30 minutes** long, capturing as many angles of each object as possible.

<img width="2532" height="1170" alt="camera_settings" src="https://github.com/user-attachments/assets/6455e45e-9478-407f-b8bc-0688fea1f3f9" />

### Frame Extraction Workflow

1. **Initial Approach:** Videos imported into DaVinci Resolve, frames exported as `.tif` files
2. **Compatibility Issue:** Discovered PostShot requires a Studio license for `.tif` import
3. **Solution:** Re-exported videos as `.png` sequences using Adobe Media Encoder
4. **Frame Selection:** Every 6–8 frames retained (dependent on original video length), targeting **under 300 images per object**

### Image Count per Object

| Object | Number of Images |
|--------|------------------|
| Fake Plant | 277 |
| Drinking Glass | 265 |
| Metal Pot | 283 |

---
