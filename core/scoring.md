---
name: scoring
description: Оценка ИИ-подобности русского текста (0–100)
version: 2.0.0
---

# Scoring: оценка 0–100

Score — **сигнал для редактуры**, не вердикт об авторе.

## Формула (упрощённая для skill)

```
base = 0

FOR each pattern hit:
  base += severity_weight × count
  # critical: 8, high: 5, medium: 3, low: 1

FOR each SUSPECT paragraph (4.6–4.7):
  base += 4

lexicon_bonus = min(15, lexicon_density × 2)

stylometry_bonus = 0
IF burstiness_band == low: stylometry_bonus += 6
IF mattr_band == low: stylometry_bonus += 6

raw = base + lexicon_bonus + stylometry_bonus
score = min(100, round(raw × scale_factor))
# scale_factor ≈ 0.85 для типичного абзаца ~150 слов
```

Нормализация: для текста <100 слов — score может быть шумным; помечай `confidence: low`.

## Уровни

| Score | Интерпретация |
|-------|---------------|
| 0–15 | Чистый живой текст |
| 16–30 | Лёгкие штампы, точечная правка |
| 31–50 | Заметная ИИ-обёртка |
| 51–70 | Сильный шаблон, нужна переработка |
| 71–100 | Почти полностью шаблонный текст |

## CI-гейт

`--score --exit-on 30` → если score > 30, в footer: `gate: FAIL`.

## MPS (Meaning Preservation Score)

После rewrite:

```
MPS = (passed_anchors + 0.5 × soft_fail) / total_anchors × 100
```

Если якорей не было → `MPS: N/A`, ouroboros не блокирует по MPS.

Порог: MPS < 70 → откат итерации ouroboros.

## Вывод score

```text
Score: 42/100 (confidence: medium)
Hot paragraphs: P2, P5
Top patterns: ru-filler#3, ru-language#7, ru-style#2
Lexicon density: 4.1/1000
```
