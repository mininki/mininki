# 한서린 — 이미지 생성 프롬프트

이미지 모델은 영어 프롬프트에서 품질이 가장 안정적이라 원문은 영어로 작성했습니다.
`[CHARACTER]` 블록은 모든 컷에 공통으로 붙여 일관성을 유지합니다.

---

## 공통 캐릭터 블록 `[CHARACTER]`

```
a beautiful 27-year-old Korean woman, professional concert cellist,
soft oval face with a gentle jawline, almond-shaped dark brown eyes with subtle inner double eyelids,
small straight nose, full lips with dusty rose MLBB lipstick,
a tiny beauty mark just under her left eye,
luminous warm-toned skin with natural texture and fine pores, satin-finish glow,
long dark brown-black hair reaching her waist with soft loose waves at the ends,
small pearl drop earrings, slender long neck and graceful long fingers
```

## 공통 악기 블록 `[CELLO]`

```
an antique 18th-century Italian cello with deep amber-red varnish,
worn varnish on the lower bout, visible flamed maple grain, ebony fingerboard, black tailpiece
```

## 공통 네거티브 프롬프트 (SDXL / Flux 등)

```
cartoon, anime, illustration, 3d render, cgi, doll-like, plastic skin, airbrushed, over-smoothed skin,
uncanny, deformed hands, extra fingers, missing fingers, fused fingers, extra strings,
broken cello, wrong f-holes, bow merged with body, asymmetrical eyes,
heavy makeup, oversaturated, harsh shadows, watermark, text, logo, low resolution, blurry
```

---

## 1. 마스터 컷 — S1 "Emerald Nocturne" (기준 얼굴 확정용)

```
Photorealistic studio portrait of [CHARACTER],
wearing a deep emerald green silk satin one-shoulder evening gown with a fluid bias cut,
seated on a hidden stool, holding [CELLO] upright beside her,
her right hand gently wrapped around the cello neck near the scroll,
head slightly tilted, warm gentle smile, looking at the camera,
seamless medium gray backdrop with a subtle radial gradient,
large softbox key light from camera left, soft fill, faint rim light on hair and shoulder,
classical music concert profile photo, shot on Canon EOS R5, 85mm f/1.8, ISO 100,
knee-up framing, shallow depth of field, ultra detailed, 8k, natural color grading
```

## 2. S2 "Moonlit Ice" — 고요한 카리스마

```
Photorealistic studio portrait of [CHARACTER], hair worn straight and sleek with a center part,
wearing a pale ice blue strapless taffeta gown with a sculpted neckline and a thin black velvet ribbon belt,
standing beside [CELLO], the scroll at the height of her face, both hands resting on the upper bout,
serene composed expression, calm direct gaze, lips closed,
seamless dark charcoal backdrop, soft frontal beauty light, gentle falloff into darkness,
elegant and mysterious mood, shot on Sony A7R V, 85mm f/1.4,
waist-up framing, ultra realistic skin texture, 8k
```

## 3. S3 "Midnight Lace" — 화사한 하이키

```
Photorealistic studio portrait of [CHARACTER], voluminous soft waves,
wearing a midnight navy lace slip dress with thin straps,
holding [CELLO] horizontally across her body, forearms resting crossed on top of the cello's upper bout,
bright radiant smile showing a hint of teeth, looking at the camera,
seamless ivory warm beige backdrop, high-key lighting, very soft shadows,
fresh and luminous mood, shot on Canon EOS R5, 70mm f/2.8,
waist-up framing, ultra detailed, 8k
```

## 4. 무대 연주 컷 — 콘서트홀

```
Photorealistic photo of [CHARACTER], hair in a low chignon with a few loose face-framing strands,
wearing a deep emerald green silk one-shoulder gown,
performing [CELLO] on stage in a grand wooden concert hall, bow on the A string,
eyes closed, deeply immersed expression, correct cello playing posture, cello endpin on the floor,
warm golden stage spotlight from above, dark audience seats softly blurred,
captured mid-performance, shot on Sony A1, 135mm f/2, cinematic, ultra realistic, 8k
```

## 5. 클로즈업 뷰티 컷

```
Extreme close-up beauty portrait of [CHARACTER], hair in a low chignon,
cheek resting lightly against the scroll of [CELLO],
soft half smile, eyes looking just past the camera,
Rembrandt soft lighting, dark gray background,
visible skin texture, catchlights in eyes, beauty mark under left eye clearly visible,
shot on Canon EOS R5, 100mm macro f/2.8, ultra detailed, 8k
```

---

## 툴별 세팅

| 툴 | 권장 세팅 |
|---|---|
| **Midjourney v7** | `--ar 2:3 --style raw --stylize 150` · 마스터 컷 확정 후 `--oref <기준이미지URL> --ow 100` |
| **Flux.1 dev / pro** | 896×1344, guidance 3.0~3.5, steps 28~40 (Flux는 네거티브 프롬프트 미지원 → 생략) |
| **SDXL (RealVisXL, Juggernaut XL 등 실사 모델)** | 832×1216, CFG 4~6, DPM++ 2M Karras, 30~40 steps, 네거티브 프롬프트 사용, ADetailer(face/hand) 권장 |
| **ChatGPT / Gemini 이미지 생성** | `[CHARACTER]`·`[CELLO]` 블록을 본문에 그대로 풀어서 붙여넣기, "세로 2:3 비율" 명시 |

### 손·악기 디테일 보정 팁
- 손가락이 뭉개지면 프롬프트에 `anatomically correct hands, five fingers` 추가 후 인페인팅.
- 첼로 줄이 4개가 아니거나 f홀이 이상하면 해당 부위만 인페인팅 (`four strings, symmetrical f-holes`).
- 활은 실패율이 높으므로 프로필 컷(1~3, 5)에서는 활을 빼는 편이 안정적.
