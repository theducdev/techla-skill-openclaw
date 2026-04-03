---
name: mkt-bao-cao-gamma
description: Tạo báo cáo, presentation, tài liệu bằng Gamma.app API. Sử dụng khi cần tạo slide trình bày, pitch deck, báo cáo marketing đẹp mắt, hoặc social media carousel qua Gamma. Trigger khi user yêu cầu tạo presentation, tạo slide, làm báo cáo Gamma, hoặc trình bày dữ liệu dạng visual. Yêu cầu GAMMA_API_KEY.
---

# Gamma.app API

Generate beautiful presentations, documents, and social posts with AI.

## Setup

```bash
export GAMMA_API_KEY="sk-gamma-xxxxx"
```

## Quick Commands

```bash
# Generate a presentation
{baseDir}/scripts/gamma.sh generate "Your content or topic here"

# Generate with options
{baseDir}/scripts/gamma.sh generate "Content" --format presentation --cards 12

# Check generation status
{baseDir}/scripts/gamma.sh status <generationId>

# List recent generations (if supported)
{baseDir}/scripts/gamma.sh list
```

## Script Usage

### Generate

```bash
{baseDir}/scripts/gamma.sh generate "<content>" [options]

Options:
  --format       presentation|document|social|webpage (default: presentation)
  --cards        Number of cards/slides (1-60, default: 10)
  --instructions Additional instructions for styling/tone
  --amount       brief|medium|detailed|extensive (default: medium)
  --tone         Free text, e.g., "professional", "casual", "technical"
  --audience     Free text, e.g., "investors", "developers", "general"
  --image-source aiGenerated|webAllImages|noImages|pexels|placeholder (default: aiGenerated)
  --image-preset photorealistic|illustration|abstract|3D|lineArt|custom (default: illustration)
  --language     Output language, e.g., "vi", "en" (default: en)
  --export       pdf|pptx|png (export after generation)
  --wait         Wait for completion and return URL
```

### Examples

```bash
# Simple presentation
{baseDir}/scripts/gamma.sh generate "The future of AI automation" --wait

# Pitch deck with specific styling
{baseDir}/scripts/gamma.sh generate "$(cat pitch.md)" \
  --format presentation \
  --cards 15 \
  --instructions "Make it a professional pitch deck for investors" \
  --tone "professional" \
  --audience "investors" \
  --wait

# Social carousel
{baseDir}/scripts/gamma.sh generate "5 tips for productivity" \
  --format social \
  --cards 5 \
  --wait

# Document/report
{baseDir}/scripts/gamma.sh generate "Q4 2025 Performance Report" \
  --format document \
  --amount detailed \
  --wait
```

## API Reference

### Endpoint
```
POST https://public-api.gamma.app/v1.0/generations
```

### Headers
```
X-API-KEY: <your-api-key>
Content-Type: application/json
```

### Request Body

```json
{
  "inputText": "Your content (1-400,000 chars max)",
  "textMode": "generate",
  "format": "presentation|document|social|webpage",
  "numCards": 10,
  "additionalInstructions": "Styling instructions",
  "exportAs": "pdf|pptx|png",
  "textOptions": {
    "amount": "brief|medium|detailed|extensive",
    "tone": "professional (free text, max 500 chars)",
    "audience": "target audience (free text, max 500 chars)",
    "language": "vi"
  },
  "imageOptions": {
    "source": "aiGenerated|webAllImages|noImages|pexels|placeholder",
    "stylePreset": "photorealistic|illustration|abstract|3D|lineArt|custom",
    "style": "free text description (max 500 chars)"
  },
  "cardOptions": {
    "dimensions": "fluid|16x9|4x3|1x1|4x5|9x16"
  }
}
```

### Response

Initial response:
```json
{"generationId": "abc123"}
```

Poll for status:
```
GET https://public-api.gamma.app/v1.0/generations/<generationId>
```

Completed response:
```json
{
  "generationId": "abc123",
  "status": "completed",
  "gammaUrl": "https://gamma.app/docs/xxxxx",
  "credits": {"deducted": 150, "remaining": 7500}
}
```

## Format Options

| Format | Dimensions | Use Case |
|--------|------------|----------|
| presentation | fluid, 16x9, 4x3 | Pitch decks, slide shows |
| document | fluid, pageless, letter, a4 | Reports, docs |
| social | 1x1, 4x5, 9x16 | Instagram, LinkedIn carousels |
| webpage | fluid | Landing pages, web content |

## Notes

- Generation typically takes 1-3 minutes
- Credits are deducted per generation (~150-300 per deck)
- Input text can be markdown formatted
- Use `--wait` flag to block until completion and get URL directly
