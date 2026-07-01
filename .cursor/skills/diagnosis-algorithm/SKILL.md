---
name: diagnosis-algorithm
description: >-
  Implements 6-axis vector matching for idol recommendation. Covers user vector
  generation, distance calculation, idol master data, and Strategy-based scoring.
  Use when working on diagnosis algorithm, score calculation, vector matching,
  idol master data, or recommendation logic.
---

# Diagnosis Algorithm

## Flow

1. User answers questions → generate 6-dimensional user vector (each axis -1.0 to 1.0)
2. Compare against 38 pre-defined idol master vectors
3. Calculate vector distance (similarity) → return nearest idol

## 6 Evaluation Axes

| Key | -1.0 | +1.0 |
|-----|------|------|
| `relationship` | 育成・親近感 | 心酔・カリスマ |
| `performance` | 王道・アイドル性 | 独自性・アーティスト |
| `visual` | 可愛い・ポップ | 美人・クール |
| `character` | わちゃわちゃ | 孤高・スター性 |
| `age_attribute` | 年下感（守りたい） | 年上感（頼りたい） |
| `behavior` | 天然・マイペース | しっかり・知的 |

## Idol Master Data Format

```json
{
  "idol_id": "idol_001",
  "name": "サンプル アイドル",
  "scores": {
    "relationship": -0.8,
    "performance": 0.5,
    "visual": -0.3,
    "character": 0.2,
    "age_attribute": -0.6,
    "behavior": 0.4
  }
}
```

Full spec: [README.md](../../README.md) §4–§6.

## Implementation Checklist

- [ ] Distance function is swappable via Strategy pattern
- [ ] Axis key names match across schemas and master data
- [ ] Tie-break rule defined for equal distances
- [ ] User vector generation logic is separate from matching logic
