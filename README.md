# 嫉妬辞書（Shitto-Mania / Jealousy Dictionary）

日本語と英語の両方で説明しています。  
Copy & paste this entire text into your `README.md`.  
Change **jun.ikematsu@gmail.com** to your actual contact email.

---

## プロジェクト概要 / Project Overview
- **日本語**  
  「婦人公論.jp」連載『嫉妬マニア』の記事群から、感情「嫉妬」に関する言葉や文脈を抽出し、  
  AIが学習しやすい形（CSV / JSON）に構造化したデータセットです。  
  英語中心のAIモデルに対し、日本語の感情データを提供することで性能と公平性の向上に貢献します。

- **English**  
  The *Jealousy Dictionary* (Shitto-Mania) is a **high-quality Japanese single-language dataset**  
  extracted from the *Shitto-Mania* essay series published on *Fujinkoron.jp*.  
  It provides structured Japanese text and emotional context (“jealousy”) for AI training,  
  helping global AI models reduce English-centric bias and improve fairness.

本プロジェクトは、エッセイスト斉藤ナミ氏の【著者協力】（素材提供・コメント）を得て制作しました。
最終的な分析・設計は池松潤が行いました。
This project was conducted with the cooperation of essayist Nami Saito (material provision and comments).
All final analysis, design, and publication decisions are the responsibility of Jun Ikematsu.

---

## 重要性 / Why It Matters
- **日本語**  
  世界のAIモデルは英語に偏っており、多言語モデルにおける日本語データはわずか0.1%未満です。  
  本辞書は、日本語特有の感情表現（特に嫉妬）をAIが正しく理解するために不可欠なリソースです。

- **English**  
  Most AI models are English-centric, and Japanese data represents less than 0.1%  
  in large multilingual models.  
  This dataset offers high-quality single-language Japanese data to help  
  AI developers improve model fairness and performance.

---

## 利用例 / Use Cases
- **日本語**  
  - 日本語RAGシステムにおける感情を考慮した回答生成  
  - 日本語センチメント分析や感情分類  
  - LLMのファインチューニングやバイアス評価  
- **English**  
  - RAG systems with Japanese emotional nuance  
  - Sentiment or emotion analysis tasks in Japanese  
  - Fine-tuning large language models or bias evaluation

---

## データ形式 / Data Format
| 列 / Column | 内容 (日本語) / Description (English) |
|---|---|
| `term` | キーワード / Key word or phrase |
| `definition_ja` | 日本語定義 / Definition in Japanese |
| `context` | 使用例や文章 / Usage example or context |
| `polarity` | 感情極性（正/負/中立） / Emotional polarity (positive/negative/neutral) |
| `source` | 出典記事IDやURL / Source article ID or URL |

サンプルデータはこちら / Sample CSV → **[sample_data.csv](./sample_data.csv)**

---

## データセットの統計情報 / Dataset Statistics
- **日本語**
  - **総記事数**: 18件
  - **出典**: [「婦人公論.jp」連載『嫉妬マニア』](https://fujinkoron.jp/category/shitto_mania)

- **English**
  - **Total Entries**: 18
  - **Source**: [*Shitto-Mania* series on *Fujinkoron.jp*](https://fujinkoron.jp/category/shitto_mania)

## 使い方サンプル / Quick Usage Example (Python)
```python
import pandas as pd

url = "https://raw.githubusercontent.com/junikematsu/shitto-mania-dic/main/sample_data.csv"
df = pd.read_csv(url)
print(df.head())

for _, row in df.iterrows():
    print(row["term"], ":", row["definition_ja"])
