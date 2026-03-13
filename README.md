# Free Image & Video Toolkit

An AI Agent Skill for image and video processing — **7 free local AI tools** + **cloud AI generation** with 300+ models.

Works with 15+ AI coding agents: Claude Code, Cursor, OpenAI Codex, GitHub Copilot, Gemini CLI, Windsurf, OpenCode, Kiro, Amp, Goose, and more.

> **Gold Sponsor**: [Atlas Cloud](https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-video-skill) — Unified API for 300+ AI models. SOC I & II Certified | HIPAA Compliant | US-based.

---

## What's Included

### Free Local Tools (No API Key Required)

All local tools run **100% offline** on your machine. No data leaves your computer.

| Tool | Script | Powered By | What It Does |
|------|--------|-----------|--------------|
| Image Upscale | `scripts/upscale.py` | Real-ESRGAN | 2x/4x AI super resolution |
| Face Enhance | `scripts/face-enhance.py` | GFPGAN + CodeFormer | Restore blurry/old photos |
| Background Remove | `scripts/bg-remove.py` | rembg (U2-Net) | Remove backgrounds → transparent PNG |
| Object Erase | `scripts/erase.py` | LaMa Inpainting | Erase unwanted objects from images |
| Face Swap | `scripts/face-swap.py` | InsightFace | Swap faces between images |
| Smart Segment | `scripts/segment.py` | FastSAM | Segment any object by text/point/box |
| Media Process | `scripts/media-process.py` | FFmpeg | Convert, compress, trim, merge, GIF |

### Cloud AI Generation (Atlas Cloud API)

Access 300+ state-of-the-art models for AI image and video generation. The script accepts any model ID — use Atlas Cloud MCP tools or API to browse available models.

**Popular models include**: Flux Schnell, Flux Dev, Seedream v5.0, Nano Banana 2, Nano Banana Pro, Imagen4 Ultra, Qwen Image, Wan 2.6, Kling v3.0, Seedance, Vidu, Hailuo, and many more.

Browse all models: [atlascloud.ai/models](https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-video-skill)

---

## Quick Start

### Prerequisites

- Python 3.10+
- [uv](https://docs.astral.sh/uv/getting-started/installation/) (`curl -LsSf https://astral.sh/uv/install.sh | sh`)
- FFmpeg (`brew install ffmpeg` / `apt install ffmpeg`)

### Installation

```bash
# Install as a skill (works with Claude Code, Cursor, Codex, etc.)
npx skills add ristponex/free-image-video-skill

# Or clone directly
git clone https://github.com/ristponex/free-image-video-skill.git
cd free-image-video-skill
```

### For Cloud AI Generation

```bash
# Set your Atlas Cloud API key
export ATLAS_CLOUD_API_KEY=your_key_here

# Or add to .env file
echo 'ATLAS_CLOUD_API_KEY=your_key_here' >> .env
```

Get your API key at [atlascloud.ai](https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-video-skill) — new users get free credits, no credit card required.

---

## Usage Examples

### Image Upscale (Real-ESRGAN) — FREE

```bash
# 4x upscale
uv run scripts/upscale.py input.jpg

# 2x upscale
uv run scripts/upscale.py input.jpg --scale 2

# Upscale with face enhancement
uv run scripts/upscale.py input.jpg --face-enhance

# Batch process a folder
uv run scripts/upscale.py ./photos/ --scale 4
```

### Face Enhance (GFPGAN / CodeFormer) — FREE

```bash
# GFPGAN (default)
uv run scripts/face-enhance.py old-photo.jpg

# CodeFormer with fidelity control
uv run scripts/face-enhance.py old-photo.jpg --method codeformer --fidelity 0.7

# With background upscale
uv run scripts/face-enhance.py old-photo.jpg --bg-upscale 2
```

### Background Remove (rembg) — FREE

```bash
# Remove background
uv run scripts/bg-remove.py product.jpg

# Fine edges (hair, fur)
uv run scripts/bg-remove.py portrait.jpg --alpha-matting

# Anime-optimized model
uv run scripts/bg-remove.py character.png --model isnet-anime

# Batch process
uv run scripts/bg-remove.py ./products/ -o ./transparent/
```

### Object Erase (LaMa) — FREE

```bash
# Erase with mask
uv run scripts/erase.py photo.png --mask mask.png

# Erase by coordinates (x,y,w,h)
uv run scripts/erase.py photo.png --region 100,200,150,150
```

### Face Swap (InsightFace) — FREE

```bash
# Swap faces
uv run scripts/face-swap.py --source face.jpg --target photo.jpg

# Specify which face in group photo
uv run scripts/face-swap.py --source face.jpg --target group.jpg --face-index 2
```

### Smart Segment (FastSAM) — FREE

```bash
# Segment by text
uv run scripts/segment.py image.jpg --text "the dog"

# Segment by point
uv run scripts/segment.py image.jpg --point 400,300

# Segment everything
uv run scripts/segment.py image.jpg
```

### Media Process (FFmpeg) — FREE

```bash
# Convert format
uv run scripts/media-process.py convert video.mp4 output.webm

# Compress to target size
uv run scripts/media-process.py compress video.mp4 --target-size 10

# Extract frames
uv run scripts/media-process.py frames video.mp4 --fps 1

# Create GIF
uv run scripts/media-process.py gif video.mp4 --start 5 --duration 3

# Trim
uv run scripts/media-process.py trim video.mp4 --start 00:01:00 --end 00:02:30

# Merge
uv run scripts/media-process.py merge clip1.mp4 clip2.mp4 -o combined.mp4

# Media info
uv run scripts/media-process.py info video.mp4
```

### AI Image Generation (Atlas Cloud)

```bash
# Ultra-fast with Flux Schnell ($0.003/image)
uv run scripts/ai-generate.py image "A cat astronaut on the moon" --model flux-schnell

# High quality with Seedream
uv run scripts/ai-generate.py image "Product photo, studio lighting" --model seedream

# Google Nano Banana
uv run scripts/ai-generate.py image "Anime character with blue hair" --model nano-banana

# Edit existing image
uv run scripts/ai-generate.py image "Make the sky sunset orange" --model seedream-edit --image photo.jpg

# Multiple images
uv run scripts/ai-generate.py image "Logo design" --model flux-schnell --count 4

# NSFW (disable safety filter)
uv run scripts/ai-generate.py image "Artistic figure study" --model flux-dev --nsfw
```

### AI Video Generation (Atlas Cloud)

```bash
# Cost-effective with Wan 2.6 ($0.070/5s)
uv run scripts/ai-generate.py video "Cherry blossoms falling in slow motion" --model wan-2.6

# Cinema-grade with Kling v3 Pro
uv run scripts/ai-generate.py video "Drone shot over cyberpunk city at night" --model kling-v3-pro --duration 10

# Image-to-video
uv run scripts/ai-generate.py video "She starts walking" --model wan-2.6-i2v --image portrait.jpg

# Anime-style with Vidu
uv run scripts/ai-generate.py video "Anime sword fight scene" --model vidu-pro

# List all models and pricing
uv run scripts/ai-generate.py models
```

---

## End-to-End Workflows

Combine free local tools with cloud AI for production workflows:

### E-commerce Product Pipeline

```bash
# 1. Generate product image with AI
uv run scripts/ai-generate.py image "Minimalist perfume bottle on marble" --model seedream

# 2. Remove background for white-bg listing
uv run scripts/bg-remove.py ./output/seedream_*.png --alpha-matting

# 3. Upscale to 4K for print
uv run scripts/upscale.py ./output/*_nobg.png --scale 4

# 4. Generate product video ad
uv run scripts/ai-generate.py video "A perfume bottle rotating elegantly, soft lighting" --model kling-v3-pro
```

### Old Photo Restoration

```bash
# 1. Enhance faces
uv run scripts/face-enhance.py grandpa-1960.jpg --method codeformer --fidelity 0.8

# 2. Upscale to modern resolution
uv run scripts/upscale.py ./output/grandpa-1960_enhanced.jpg --scale 4

# 3. Erase scratches and damage
uv run scripts/erase.py ./output/grandpa-1960_enhanced_x4.jpg --mask scratches.png
```

### Content Creation Pipeline

```bash
# 1. Generate hero image
uv run scripts/ai-generate.py image "Tech startup landing page hero, abstract" --model nano-banana

# 2. Segment key elements
uv run scripts/segment.py ./output/nano-banana_*.png --text "main object" --mask-only

# 3. Generate promo video
uv run scripts/ai-generate.py video "Dynamic product reveal with particle effects" --model seedance

# 4. Create GIF for social media
uv run scripts/media-process.py gif ./output/seedance_*.mp4 --fps 15 --width 480
```

---

## Local AI Models

Models are downloaded automatically on first use and cached locally:

| Tool | Model | Size | Cache Path |
|------|-------|------|------------|
| Upscale | RealESRGAN_x4plus | ~64 MB | `~/.cache/realesrgan/` |
| Face Enhance | GFPGANv1.4 | ~348 MB | `~/.cache/gfpgan/` |
| Face Enhance | CodeFormer | ~376 MB | `~/.cache/codeformer/` |
| Background Remove | U2-Net | ~176 MB | `~/.u2net/` |
| Object Erase | LaMa | ~200 MB | `~/.cache/lama/` |
| Face Swap | buffalo_l + inswapper | ~500 MB | `~/.insightface/` |
| Smart Segment | FastSAM-s | ~23 MB | auto by ultralytics |

Total first-run download: ~1.5 GB. All subsequent runs are instant.

---

## Tips

- **GPU Acceleration**: Tools auto-detect CUDA (NVIDIA) and MPS (Apple Silicon), falling back to CPU
- **Batch Processing**: Most tools accept a folder path for batch processing
- **Memory**: Face swap and segmentation need 4GB+ RAM for large images
- **First Run**: First execution downloads AI models — be patient, subsequent runs are instant
- **Zero Setup**: All Python dependencies are handled by `uv run` — no pip install needed

---

## Agent Skill Integration

Install as a skill for any AI coding agent:

```bash
npx skills add ristponex/free-image-video-skill
```

Compatible with: Claude Code, Cursor, OpenAI Codex, GitHub Copilot, Gemini CLI, Windsurf, OpenCode, Kiro, Amp, Goose, Kilo Code, and more.

---

## Atlas Cloud API Reference

### Authentication

```bash
export ATLAS_CLOUD_API_KEY=your_key_here
```

### Image Generation API

```bash
curl -X POST "https://api.atlascloud.ai/api/v1/model/generateImage" \
  -H "Authorization: Bearer $ATLAS_CLOUD_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "black-forest-labs/flux-schnell",
    "prompt": "A serene Japanese garden with cherry blossoms",
    "size": "1024*1024",
    "num_images": 1
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

# Generate image
resp = requests.post(f"{BASE}/generateImage", json={
    "model": "black-forest-labs/flux-schnell",
    "prompt": "A futuristic cityscape",
    "size": "1024*1024",
}, headers={"Authorization": f"Bearer {API_KEY}"})

request_id = resp.json()["data"]["id"]

# Poll for result
while True:
    result = requests.get(f"{BASE}/result/{request_id}",
        headers={"Authorization": f"Bearer {API_KEY}"}).json()
    if result["data"]["status"] in ("completed", "succeeded"):
        print(result["data"]["outputs"])
        break
    time.sleep(3)
```

---

## Pricing

### Free Local Tools — $0

All 7 local tools are completely free and open source. Run them as much as you want.

### Cloud AI Generation — Pay Per Use

| Category | Model | Starting Price |
|----------|-------|---------------|
| Image | Flux Schnell | $0.003/image |
| Image | Nano Banana 2 | $0.020/image |
| Image | Seedream v5.0 | $0.032/image |
| Video | Wan 2.6 | $0.014/s |
| Video | Vidu Q3 Turbo | $0.007/s |
| Video | Seedance v1 Pro | $0.044/s |
| Video | Kling v3.0 Pro | $0.042/s |

New users get free credits on signup. [Get your API key →](https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-video-skill)

---

## License

MIT License. See [LICENSE](./LICENSE) for details.

---

## Acknowledgments

### Gold Sponsor

**[Atlas Cloud](https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-video-skill)** — Unified API for 300+ AI models. Enterprise-grade infrastructure with SOC I & II certification and HIPAA compliance.

### Open Source Projects

This toolkit builds on these incredible open-source projects:

- [Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN) — Image super resolution
- [GFPGAN](https://github.com/TencentARC/GFPGAN) — Face restoration
- [CodeFormer](https://github.com/sczhou/CodeFormer) — Face restoration with controllable fidelity
- [rembg](https://github.com/danielgatis/rembg) — Background removal
- [LaMa](https://github.com/advimman/lama) — Large mask inpainting
- [InsightFace](https://github.com/deepinsight/insightface) — Face analysis and swapping
- [FastSAM](https://github.com/CASIA-IVA-Lab/FastSAM) — Fast segment anything
- [FFmpeg](https://ffmpeg.org/) — Multimedia processing
- [uv](https://github.com/astral-sh/uv) — Python package management
