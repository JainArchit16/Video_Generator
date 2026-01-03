# 🎬 AI Video Generator: The Zero-Cost AI Filmmaker

**Generate professional, 9:16 vertical short films with coherent storytelling, dual-camera angles, and original music, running 100% free on Google Colab (T4 GPU).**

## 🚀 Features

* **Dual-Shot "Director's Cut" Engine:** Unlike standard AI video loops, this engine generates two unique camera angles (Shot A + Shot B) for every scene and stitches them with cinematic crossfades. No more repetitive looping!
* **Zero API Costs:** Uses local models (`AnimateDiff`, `DreamShaper`, `MusicGen`/Math-Synth) instead of paid APIs like OpenAI or Runway.
* **Dynamic FPS Smoothing:** Includes an FFmpeg pipeline to upscale raw 8fps AI output to smooth 24fps or 30fps using motion interpolation (`minterpolate`).
* **Native Vertical Generation:** optimized 512x896 resolution for YouTube Shorts, TikTok, and Reels.
* **Math-Based Audio Synthesis:** Generates royalty-free background music procedurally using Python (NumPy) to avoid copyright strikes and dependency errors.

## 🛠️ How It Works

The pipeline is split into 5 distinct phases for stability on free cloud GPUs:

1.  **Setup:** Installs `diffusers`, `accelerate`, and `moviepy`.
2.  **Config:** User defines the script, style (`pixar`, `anime`, `realistic`), and aspect ratio.
3.  **Filming:** `AnimateDiff` generates 2 raw clips per scene based on the script.
4.  **Audio:** `gTTS` generates voiceovers; `NumPy` synthesizes background scores.
5.  **Assembly:** `MoviePy` stitches shots using the "Director's Logic" (A/B Cutting) and mixes the final audio.

## 💻 Usage

1. Open the [Google Colab Notebook](https://colab.research.google.com/drive/1lT3OpTIbTrOYibxha1zTKxj3nfPjEBUr?usp=sharing).
2. Connect to a **T4 GPU** Runtime.
3. Run the **Installation** cell.
4. Edit the `USER_CONFIG` dictionary in Phase 2 to change the video style or script.
5. Run all subsequent cells.
6. Download your `DirectorCut_Final.mp4`!

## 🧠 Configuration Example

```python
USER_CONFIG = {
    "ratio": "9:16",         # Perfect for Shorts
    "fps": 24,               # Cinematic framerate
    "style": "pixar_3d",     # Options: pixar_3d, anime, realistic
}
