<div align="center">

# 🎨 Free Image & Video AI Agent Skill

**7 Free Local AI Tools + 300+ Cloud AI Models — One Skill for All AI Agents**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Python 3.10-3.12](https://img.shields.io/badge/Python-3.10--3.12-blue.svg)](https://python.org)
[![uv](https://img.shields.io/badge/uv-package%20manager-blueviolet)](https://docs.astral.sh/uv/)

[English](./README.md) · [中文](./README_zh.md) · [日本語](./README_ja.md) · [한국어](./README_ko.md)

</div>

<br>

### ✨ Why This Skill?

- 🆓 **Completely Free** — 7 local AI tools run offline, no API keys, no usage limits, zero cost
- ⚡ **Zero Setup** — Just `uv run` and go. Dependencies auto-install on first run
- 🔒 **Privacy First** — All local processing stays on your machine. No data uploaded
- 🌐 **300+ Cloud Models** — Access Flux, Seedream, Nano Banana, Kling, Wan via one API — **up to 88% cheaper** than fal.ai & official APIs
- 🤖 **Agent-Ready** — Works out of the box with Claude Code, Cursor, Codex, Copilot, and 15+ AI agents
- 🔗 **Production Workflows** — Chain tools together: generate → upscale → remove bg → create video

> 🏆 **Gold Sponsor**: [Atlas Cloud](https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-and-video-generation-skill) — Unified API for 300+ AI models. SOC I & II Certified · HIPAA Compliant. Up to 88% cheaper than alternatives.

---

## 📦 Installation

### Prerequisites

- 🐍 Python 3.10 - 3.12 — [python.org](https://python.org) (3.13 not yet supported by some dependencies; `uv` will auto-manage the correct version)
- 📦 uv — `curl -LsSf https://astral.sh/uv/install.sh | sh`
- 🎬 FFmpeg — `brew install ffmpeg` / `apt install ffmpeg` / `winget install ffmpeg`

### Install the Skill

```bash
# ✅ Option 1: Install as an AI agent skill (Claude Code, Cursor, Codex, etc.)
npx skills add ristponex/free-image-and-video-generation-skill

# 📂 Option 2: Clone directly
git clone https://github.com/ristponex/free-image-and-video-generation-skill.git
cd free-image-and-video-generation-skill
```

### ☁️ Cloud AI Setup (Optional — for AI image/video generation)

```bash
# Get your free API key at: https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-and-video-generation-skill
# (free credits included, no credit card required)

# Mac / Linux — add to ~/.bashrc or ~/.zshrc:
export ATLAS_CLOUD_API_KEY=your_key_here

# Windows (PowerShell):
$env:ATLAS_CLOUD_API_KEY="your_key_here"
# Windows (permanent — run as Administrator):
setx ATLAS_CLOUD_API_KEY "your_key_here"

# Or create a .env file in the project directory:
echo 'ATLAS_CLOUD_API_KEY=your_key_here' >> .env
```

---

## 🛠️ What's Included

### 🆓 Free Local Tools — No API Key, 100% Offline

All local tools run entirely on your machine. **No data leaves your computer.**

| # | Tool | Script | Powered By | What It Does |
|---|------|--------|-----------|--------------|
| 1 | 🔍 **Image Upscale** | `scripts/upscale.py` | Real-ESRGAN | 2x/4x AI super resolution |
| 2 | 👤 **Face Enhance** | `scripts/face-enhance.py` | Real-ESRGAN | Restore blurry/old photos, enhance details |
| 3 | ✂️ **Background Remove** | `scripts/bg-remove.py` | rembg (U2-Net) | Remove backgrounds → transparent PNG |
| 4 | 🧹 **Object Erase** | `scripts/erase.py` | LaMa Inpainting | Erase unwanted objects seamlessly |
| 5 | 🎭 **Face Swap** | `scripts/face-swap.py` | InsightFace | Swap faces between images |
| 6 | 🧩 **Smart Segment** | `scripts/segment.py` | FastSAM | Segment any object by text/point/box |
| 7 | 🎬 **Media Process** | `scripts/media-process.py` | FFmpeg | Convert, compress, trim, merge, GIF |

### ☁️ Cloud AI Generation — 300+ Models via Atlas Cloud API

| # | Tool | Script | What It Does |
|---|------|--------|--------------|
| 8 | 🎨 **AI Generate** | `scripts/ai-generate.py` | Generate images & videos with any of 300+ cloud AI models |

**Popular models**: Flux Schnell · Seedream v5.0 · Nano Banana 2 · Imagen4 Ultra · Wan 2.6 · Kling v3.0 · Seedance · Vidu · Hailuo · and many more

```bash
# 📋 Browse all available models and pricing
uv run scripts/ai-generate.py models
```

---

## 📖 Usage

All scripts use `uv run` — dependencies are **automatically installed** on first run. Zero setup needed.

<details>
<summary>🔍 <b>Image Upscale</b> — 2x/4x AI super resolution (FREE)</summary>

```bash
uv run scripts/upscale.py input.jpg                   # 4x upscale (default)
uv run scripts/upscale.py input.jpg --scale 2          # 2x upscale
uv run scripts/upscale.py input.jpg --face-enhance     # With face enhancement
uv run scripts/upscale.py ./photos/ --scale 4          # Batch process folder
```
</details>

<details>
<summary>👤 <b>Face Enhance</b> — Restore old/blurry photos (FREE)</summary>

```bash
uv run scripts/face-enhance.py old-photo.jpg                                  # Default enhancement
uv run scripts/face-enhance.py old-photo.jpg --method codeformer --fidelity 0.7  # CodeFormer
uv run scripts/face-enhance.py old-photo.jpg --bg-upscale 2                   # With background upscale
```
</details>

<details>
<summary>✂️ <b>Background Remove</b> — Transparent PNG output (FREE)</summary>

```bash
uv run scripts/bg-remove.py product.jpg                        # Remove background
uv run scripts/bg-remove.py portrait.jpg --alpha-matting        # Fine edges (hair, fur)
uv run scripts/bg-remove.py character.png --model isnet-anime   # Anime-optimized
uv run scripts/bg-remove.py ./products/ -o ./transparent/       # Batch process
```
</details>

<details>
<summary>🧹 <b>Object Erase</b> — Remove unwanted objects (FREE)</summary>

```bash
uv run scripts/erase.py photo.png --mask mask.png              # Erase with mask
uv run scripts/erase.py photo.png --region 100,200,150,150     # Erase by coordinates
```
</details>

<details>
<summary>🎭 <b>Face Swap</b> — Swap faces between images (FREE)</summary>

```bash
uv run scripts/face-swap.py --source face.jpg --target photo.jpg              # Basic swap
uv run scripts/face-swap.py --source face.jpg --target group.jpg --face-index 2  # Group photo
```
</details>

<details>
<summary>🧩 <b>Smart Segment</b> — Segment anything (FREE)</summary>

```bash
uv run scripts/segment.py image.jpg --text "the dog"    # By text prompt
uv run scripts/segment.py image.jpg --point 400,300     # By point
uv run scripts/segment.py image.jpg                     # Segment everything
```
</details>

<details>
<summary>🎬 <b>Media Process</b> — FFmpeg-powered processing (FREE)</summary>

```bash
uv run scripts/media-process.py convert video.mp4 output.webm          # Convert format
uv run scripts/media-process.py compress video.mp4 --target-size 10    # Compress
uv run scripts/media-process.py frames video.mp4 --fps 1               # Extract frames
uv run scripts/media-process.py gif video.mp4 --start 5 --duration 3   # Create GIF
uv run scripts/media-process.py trim video.mp4 --start 00:01:00 --end 00:02:30
uv run scripts/media-process.py merge clip1.mp4 clip2.mp4 -o combined.mp4
uv run scripts/media-process.py info video.mp4                         # Media info
```
</details>

<details>
<summary>🎨 <b>AI Image Generation</b> — 300+ cloud models (Atlas Cloud)</summary>

```bash
# List available models
uv run scripts/ai-generate.py models --type image

# Generate with full model ID
uv run scripts/ai-generate.py image "A cat astronaut on the moon" \
  --model black-forest-labs/flux-schnell --size 1024*1024

# Google Nano Banana 2 (uses aspect_ratio + resolution)
uv run scripts/ai-generate.py image "Anime character with blue hair" \
  --model google/nano-banana-2/text-to-image --aspect-ratio 1:1 --resolution 1k

# ByteDance Seedream v5.0
uv run scripts/ai-generate.py image "Product photo, studio lighting" \
  --model bytedance/seedream-v5.0-lite --size 2048*2048

# Edit existing image
uv run scripts/ai-generate.py image "Make the sky sunset orange" \
  --model bytedance/seedream-v5.0-lite/edit --image photo.jpg
```
</details>

<details>
<summary>🎥 <b>AI Video Generation</b> — Cinema-grade AI video (Atlas Cloud)</summary>

```bash
# List available models
uv run scripts/ai-generate.py models --type video

# Wan 2.6 text-to-video
uv run scripts/ai-generate.py video "Cherry blossoms falling in slow motion" \
  --model alibaba/wan-2.6/text-to-video --size 1280*720

# Kling v3.0 Pro (cinema-grade)
uv run scripts/ai-generate.py video "Drone shot over cyberpunk city at night" \
  --model kwaivgi/kling-v3.0-pro/text-to-video --duration 10

# Image-to-video
uv run scripts/ai-generate.py video "She starts walking" \
  --model alibaba/wan-2.6/image-to-video --image portrait.jpg
```
</details>

---

## 🔗 End-to-End Workflows

Combine free local tools with cloud AI for production pipelines:

<details>
<summary>🛒 <b>E-commerce Product Pipeline</b></summary>

```bash
# 1. Generate product image with AI
uv run scripts/ai-generate.py image "Minimalist perfume bottle on marble" \
  --model bytedance/seedream-v5.0-lite --size 2048*2048

# 2. Remove background for white-bg listing
uv run scripts/bg-remove.py ./output/seedream-v5.0-lite_*.png --alpha-matting

# 3. Upscale to 4K for print
uv run scripts/upscale.py ./output/*_nobg.png --scale 4

# 4. Generate product video ad
uv run scripts/ai-generate.py video "A perfume bottle rotating elegantly" \
  --model kwaivgi/kling-v3.0-pro/text-to-video --duration 5
```
</details>

<details>
<summary>📸 <b>Old Photo Restoration</b></summary>

```bash
# 1. Enhance faces
uv run scripts/face-enhance.py grandpa-1960.jpg --method codeformer --fidelity 0.8

# 2. Upscale to modern resolution
uv run scripts/upscale.py ./output/grandpa-1960_enhanced.jpg --scale 4

# 3. Erase scratches and damage
uv run scripts/erase.py ./output/grandpa-1960_enhanced_x4.jpg --mask scratches.png
```
</details>

<details>
<summary>🎯 <b>Content Creation Pipeline</b></summary>

```bash
# 1. Generate hero image
uv run scripts/ai-generate.py image "Tech startup landing page hero" \
  --model google/nano-banana-2/text-to-image --aspect-ratio 16:9 --resolution 2k

# 2. Segment key elements
uv run scripts/segment.py ./output/text-to-image_*.png --text "main object" --mask-only

# 3. Generate promo video
uv run scripts/ai-generate.py video "Dynamic product reveal with particle effects" \
  --model bytedance/seedance-v1.5-pro/text-to-video

# 4. Create GIF for social media
uv run scripts/media-process.py gif ./output/text-to-video_*.mp4 --fps 15 --width 480
```
</details>

---

## 💰 Pricing

### 🆓 Free Local Tools — $0

All 7 local tools are completely **free and open source**. Run them as much as you want.

### ☁️ Cloud AI Generation — Pay Per Use

| Model | Atlas Cloud | fal.ai | Official API | You Save |
|-------|-------------|--------|--------------|----------|
| Flux Schnell | **$0.003**/image | $0.025/image | N/A | **88%** |
| Seedream v5.0 | **$0.032**/image | N/A | N/A | Exclusive |
| Nano Banana 2 | **$0.072**/image | N/A | $0.08/image | 10% |
| Imagen4 Ultra | **$0.054**/image | N/A | $0.06/image | 10% |
| Wan 2.6 (5s) | **$0.070**/5s | $0.50/5s | N/A | **86%** |
| Kling v3.0 Pro (5s) | **$0.204**/5s | N/A | $0.70/5s | **71%** |

> Prices shown are base prices with current promotions. Final price may vary by resolution, duration, etc.

New users get **free credits** on signup — [Get your API key →](https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-and-video-generation-skill)

---

## 🤖 Compatible AI Agents

Works with **15+ AI coding agents**:

Claude Code · Cursor · OpenAI Codex · GitHub Copilot · Gemini CLI · Windsurf · OpenCode · Kiro · Amp · Goose · Kilo Code · and more

---

## 💡 Tips

- ⚡ **GPU Acceleration** — Auto-detects CUDA (NVIDIA) and MPS (Apple Silicon), falls back to CPU
- 📁 **Batch Processing** — Most tools accept a folder path for batch processing
- 💾 **Memory** — Face swap and segmentation need 4GB+ RAM for large images
- 🚀 **Zero Setup** — All dependencies handled by `uv run`, no pip install needed
- ⏬ **First Run** — AI models are downloaded on first use (~1 GB total), subsequent runs are instant

---

<details>
<summary>📡 <b>Atlas Cloud API Reference</b></summary>

### Image Generation API

```bash
curl -X POST "https://api.atlascloud.ai/api/v1/model/generateImage" \
  -H "Authorization: Bearer $ATLAS_CLOUD_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "black-forest-labs/flux-schnell",
    "prompt": "A serene Japanese garden with cherry blossoms",
    "size": "1024*1024"
  }'
```

### Video Generation API

```bash
curl -X POST "https://api.atlascloud.ai/api/v1/model/generateVideo" \
  -H "Authorization: Bearer $ATLAS_CLOUD_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "alibaba/wan-2.6/text-to-video",
    "prompt": "Timelapse of a flower blooming",
    "size": "1280*720",
    "duration": 5
  }'
```

### Poll for Result

```bash
curl -X GET "https://api.atlascloud.ai/api/v1/model/result/{request_id}" \
  -H "Authorization: Bearer $ATLAS_CLOUD_API_KEY"
```

### Python Integration

```python
import requests, time, os

API_KEY = os.environ["ATLAS_CLOUD_API_KEY"]
BASE = "https://api.atlascloud.ai/api/v1/model"

resp = requests.post(f"{BASE}/generateImage", json={
    "model": "black-forest-labs/flux-schnell",
    "prompt": "A futuristic cityscape",
    "size": "1024*1024",
}, headers={"Authorization": f"Bearer {API_KEY}"})

request_id = resp.json()["data"]["id"]

while True:
    result = requests.get(f"{BASE}/result/{request_id}",
        headers={"Authorization": f"Bearer {API_KEY}"}).json()
    if result["data"]["status"] in ("completed", "succeeded"):
        print(result["data"]["outputs"])
        break
    time.sleep(3)
```

</details>

---

## 📄 License

MIT License. See [LICENSE](./LICENSE) for details.

---

<div align="center">

### 🏆 Gold Sponsor

**[Atlas Cloud](https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-and-video-generation-skill)** — Unified API for 300+ AI models

SOC I & II Certified · HIPAA Compliant · Up to 88% cheaper than fal.ai & official APIs

<br>

### Built With

[Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN) · [rembg](https://github.com/danielgatis/rembg) · [LaMa](https://github.com/advimman/lama) · [InsightFace](https://github.com/deepinsight/insightface) · [FastSAM](https://github.com/CASIA-IVA-Lab/FastSAM) · [FFmpeg](https://ffmpeg.org/) · [uv](https://github.com/astral-sh/uv)

</div>
