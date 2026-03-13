<div align="center">

# 무료 이미지 & 비디오 툴킷

**7개 무료 로컬 AI 도구 + 300개 이상의 클라우드 AI 모델 — 모든 AI 에이전트를 위한 하나의 스킬**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://python.org)
[![uv](https://img.shields.io/badge/uv-package%20manager-blueviolet)](https://docs.astral.sh/uv/)

[English](./README.md) · [中文](./README_zh.md) · [日本語](./README_ja.md) · [한국어](./README_ko.md)

<br>

**15개 이상의 AI 코딩 에이전트 지원**

Claude Code · Cursor · OpenAI Codex · GitHub Copilot · Gemini CLI · Windsurf · OpenCode · Kiro · Amp · Goose 등

</div>

<br>

> **골드 스폰서**: [Atlas Cloud](https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-video-skill) — 300개 이상의 AI 모델 통합 API. SOC I & II 인증 · HIPAA 준수 · 미국 인프라.

---

## 포함 내용

### 무료 로컬 도구 — API 키 불필요, 클라우드 불필요, 100% 오프라인

모든 로컬 도구는 사용자의 컴퓨터에서 실행됩니다. **데이터가 외부로 전송되지 않습니다.**

| # | 도구 | 스크립트 | 기술 기반 | 기능 |
|---|------|---------|----------|------|
| 1 | **이미지 업스케일** | `scripts/upscale.py` | Real-ESRGAN | 2x/4x AI 초해상도 |
| 2 | **얼굴 보정** | `scripts/face-enhance.py` | Real-ESRGAN | 흐릿한/오래된 사진 복원 |
| 3 | **배경 제거** | `scripts/bg-remove.py` | rembg (U2-Net) | 배경 제거 → 투명 PNG |
| 4 | **객체 제거** | `scripts/erase.py` | LaMa Inpainting | 원하지 않는 객체 매끄럽게 제거 |
| 5 | **얼굴 교체** | `scripts/face-swap.py` | InsightFace | 이미지 간 얼굴 교체 |
| 6 | **스마트 분할** | `scripts/segment.py` | FastSAM | 텍스트/포인트/박스로 객체 분할 |
| 7 | **미디어 처리** | `scripts/media-process.py` | FFmpeg | 변환, 압축, 자르기, 병합, GIF |

### 클라우드 AI 생성 — Atlas Cloud API로 300개 이상의 모델

| # | 도구 | 스크립트 | 기능 |
|---|------|---------|------|
| 8 | **AI 생성** | `scripts/ai-generate.py` | 300개 이상의 클라우드 AI 모델로 이미지 & 비디오 생성 |

**인기 모델**: Flux Schnell · Seedream v5.0 · Nano Banana 2 · Imagen4 Ultra · Wan 2.6 · Kling v3.0 · Seedance · Vidu · Hailuo 등

```bash
# 사용 가능한 모델 및 가격 보기
uv run scripts/ai-generate.py models
```

---

## 빠른 시작

### 필수 조건

| 요구 사항 | 설치 |
|----------|------|
| Python 3.10+ | [python.org](https://python.org) |
| uv | `curl -LsSf https://astral.sh/uv/install.sh \| sh` |
| FFmpeg | `brew install ffmpeg` / `apt install ffmpeg` |

### 설치

```bash
# 방법 1: AI 에이전트 스킬로 설치
npx skills add ristponex/free-image-video-skill

# 방법 2: 직접 클론
git clone https://github.com/ristponex/free-image-video-skill.git
cd free-image-video-skill
```

### 클라우드 AI 설정 (선택 사항)

```bash
# Atlas Cloud API 키 설정
export ATLAS_CLOUD_API_KEY=your_key_here

# 또는 .env 파일에 추가
echo 'ATLAS_CLOUD_API_KEY=your_key_here' >> .env
```

[atlascloud.ai](https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-video-skill)에서 API 키 받기 — 신규 사용자는 **무료 크레딧**을 받습니다. 신용카드 불필요.

---

## 사용법

모든 스크립트는 `uv run`을 사용합니다 — 의존성은 첫 실행 시 **자동 설치**됩니다. 설정 불필요.

<details>
<summary><b>이미지 업스케일</b> — 2x/4x AI 초해상도 (무료)</summary>

```bash
uv run scripts/upscale.py input.jpg                   # 4x 업스케일 (기본값)
uv run scripts/upscale.py input.jpg --scale 2          # 2x 업스케일
uv run scripts/upscale.py input.jpg --face-enhance     # 얼굴 보정 포함
uv run scripts/upscale.py ./photos/ --scale 4          # 폴더 일괄 처리
```
</details>

<details>
<summary><b>얼굴 보정</b> — 오래된/흐릿한 사진 복원 (무료)</summary>

```bash
uv run scripts/face-enhance.py old-photo.jpg                                  # 기본 보정
uv run scripts/face-enhance.py old-photo.jpg --method codeformer --fidelity 0.7  # CodeFormer
uv run scripts/face-enhance.py old-photo.jpg --bg-upscale 2                   # 배경 업스케일 포함
```
</details>

<details>
<summary><b>배경 제거</b> — 투명 PNG 출력 (무료)</summary>

```bash
uv run scripts/bg-remove.py product.jpg                        # 배경 제거
uv run scripts/bg-remove.py portrait.jpg --alpha-matting        # 정밀 엣지 (머리카락, 털)
uv run scripts/bg-remove.py character.png --model isnet-anime   # 애니메이션 최적화
uv run scripts/bg-remove.py ./products/ -o ./transparent/       # 일괄 처리
```
</details>

<details>
<summary><b>객체 제거</b> — 매끄러운 제거 (무료)</summary>

```bash
uv run scripts/erase.py photo.png --mask mask.png              # 마스크로 제거
uv run scripts/erase.py photo.png --region 100,200,150,150     # 좌표로 제거
```
</details>

<details>
<summary><b>얼굴 교체</b> — 이미지 간 얼굴 교체 (무료)</summary>

```bash
uv run scripts/face-swap.py --source face.jpg --target photo.jpg              # 기본 교체
uv run scripts/face-swap.py --source face.jpg --target group.jpg --face-index 2  # 단체 사진
```
</details>

<details>
<summary><b>스마트 분할</b> — 모든 것을 분할 (무료)</summary>

```bash
uv run scripts/segment.py image.jpg --text "the dog"    # 텍스트 프롬프트
uv run scripts/segment.py image.jpg --point 400,300     # 포인트 지정
uv run scripts/segment.py image.jpg                     # 전체 분할
```
</details>

<details>
<summary><b>미디어 처리</b> — FFmpeg 기반 (무료)</summary>

```bash
uv run scripts/media-process.py convert video.mp4 output.webm          # 형식 변환
uv run scripts/media-process.py compress video.mp4 --target-size 10    # 압축
uv run scripts/media-process.py frames video.mp4 --fps 1               # 프레임 추출
uv run scripts/media-process.py gif video.mp4 --start 5 --duration 3   # GIF 생성
uv run scripts/media-process.py trim video.mp4 --start 00:01:00 --end 00:02:30
uv run scripts/media-process.py merge clip1.mp4 clip2.mp4 -o combined.mp4
uv run scripts/media-process.py info video.mp4                         # 미디어 정보
```
</details>

<details>
<summary><b>AI 이미지 생성</b> — 300개 이상의 클라우드 모델 (Atlas Cloud)</summary>

```bash
uv run scripts/ai-generate.py models --type image

uv run scripts/ai-generate.py image "A cat astronaut on the moon" \
  --model black-forest-labs/flux-schnell --size 1024*1024

uv run scripts/ai-generate.py image "Anime character with blue hair" \
  --model google/nano-banana-2/text-to-image --aspect-ratio 1:1 --resolution 1k
```
</details>

<details>
<summary><b>AI 비디오 생성</b> — 시네마 등급 AI 비디오 (Atlas Cloud)</summary>

```bash
uv run scripts/ai-generate.py models --type video

uv run scripts/ai-generate.py video "Cherry blossoms falling in slow motion" \
  --model alibaba/wan-2.6/text-to-video --size 1280*720

uv run scripts/ai-generate.py video "Drone shot over cyberpunk city at night" \
  --model kwaivgi/kling-v3.0-pro/text-to-video --duration 10
```
</details>

---

## 가격

### 무료 로컬 도구 — $0

7개 로컬 도구 모두 완전히 **무료이며 오픈소스**입니다.

### 클라우드 AI 생성 — 사용량 기반 과금

| 모델 | Atlas Cloud | fal.ai | 공식 API | 절약 |
|------|-------------|--------|---------|------|
| Flux Schnell | **$0.003**/장 | $0.025/장 | N/A | **88%** |
| Seedream v5.0 | **$0.032**/장 | N/A | N/A | 독점 |
| Nano Banana 2 | **$0.072**/장 | N/A | $0.08/장 | 10% |
| Wan 2.6 (5초) | **$0.070**/5초 | $0.50/5초 | N/A | **86%** |
| Kling v3.0 Pro (5초) | **$0.204**/5초 | N/A | $0.70/5초 | **71%** |

신규 사용자는 **무료 크레딧**을 받습니다 — [API 키 받기 →](https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-video-skill)

---

## 라이선스

MIT License. 자세한 내용은 [LICENSE](./LICENSE)를 참조하세요.

---

<div align="center">

### 골드 스폰서

**[Atlas Cloud](https://www.atlascloud.ai?utm_source=github&utm_campaign=free-image-video-skill)** — 300개 이상의 AI 모델 통합 API

SOC I & II 인증 · HIPAA 준수 · 미국 인프라

<br>

### 사용 기술

[Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN) · [rembg](https://github.com/danielgatis/rembg) · [LaMa](https://github.com/advimman/lama) · [InsightFace](https://github.com/deepinsight/insightface) · [FastSAM](https://github.com/CASIA-IVA-Lab/FastSAM) · [FFmpeg](https://ffmpeg.org/) · [uv](https://github.com/astral-sh/uv)

</div>
