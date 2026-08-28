# 嫉妬辞書（Shitto-Mania / Jealousy Dictionary）

日本語と英語の両方で説明しています。  

---

## プロジェクト概要 / Project Overview

### 日本語

本リポジトリは、婦人公論.jp連載『嫉妬マニア』（斉藤ナミ氏）を対象に構築した、構造化言語資源とNLP2026実験データを公開するためのリポジトリです。

NLP2026では、全321エピソードを対象に25項目の構造化メタデータを作成し、RAGにおいてAIが正しい参照先へ到達できる性質を「参照可能性（Referenceability）」として評価しました。

本研究は、嫉妬という感情そのものを分類・分析する感情分析研究ではありません。主な研究対象は、同じ情報源でも「どのように構造化して記述するか」によって検索・参照性能がどのように変わるか、という言語資源設計の問題です。

### English

This repository contains the structured language resource and experimental data used in the NLP2026 study based on the *Shitto-Mania* essay series by Nami Saito, published on Fujinkoron.jp.

For NLP2026, 321 episodes were represented using 25 structured metadata fields, and evaluated in a RAG reference-retrieval setting. The study introduces **Referenceability** as an evaluation axis for whether an AI system can reach the correct reference point.

This is **not a sentiment-analysis or emotion-classification study**. The primary research question is how the representation and structuring of the same source material affect retrieval and reference performance.


---

## 利用条件 / Usage Policy
本データセットは、斉藤ナミ氏の著作「嫉妬マニア」（婦人公論.jp連載）を元に作成されています。
**著作権は斉藤ナミ氏に帰属します。**

- **学術研究・教育目的での利用のみ可**
- **商用利用（営利目的での利用・二次販売・生成AI学習への商業利用など）は禁止**
- 利用時には出典（斉藤ナミ「嫉妬マニア」婦人公論.jp）を明記してください。

This dataset is provided **for research and educational purposes only**.
Commercial use, resale, or use in commercial AI training is **prohibited**.
Copyright © Nami Saito.

---
## 重要性 / Why It Matters

* **日本語**
  AIが正しい情報を参照できるかどうかは、情報量だけでなく、情報がどのように構造化・記述されているかにも左右されます。
  本データセットと実験は、同じ情報源であっても、構造化メタデータと本文テキストでは検索・参照性能が大きく異なり得ることを示しています。
  NLP2026では、この「AIが正しい参照先へ到達しやすい性質」を「参照可能性（Referenceability）」として評価しました。

* **English**
  Whether an AI system can reach the correct reference depends not only on the amount of information available, but also on how that information is structured and represented.
  This dataset and the accompanying experiments examine how retrieval and reference performance can differ substantially between structured metadata and body text derived from the same source material.
  The NLP2026 study evaluates this property as **Referenceability**.


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
```
---

## NLP2026 Paper / AI Referenceability

"AI Referenceability" is the public-facing term I use for the practical quality axis of whether AI can reach the correct reference point. The NLP2026 paper proposes "Referenceability" as the evaluation axis tested in RAG Reference Retrieval.

- **Technical Note / DOI**: [AI Referenceability: A Framework for Designing Knowledge That AI Can Reliably Retrieve and Reference](https://doi.org/10.5281/zenodo.22073908) — DOI: `10.5281/zenodo.22073908`
- **ORCID**: [Jun Ikematsu — 0009-0007-9651-5541](https://orcid.org/0009-0007-9651-5541)
- Paper: [NLP2026 Q5-8](https://www.anlp.jp/proceedings/annual_meeting/2026/pdf_dir/Q5-8.pdf)
- Canonical overview (English): [What Is AI Referenceability?](https://note.com/ikematsu/n/na8afe18d94a4)
- 日本語の正本記事: [AI参照可能性とは何か？](https://note.com/ikematsu/n/n628d654a83da)
- Experimental data: [`nlp2026/`](https://github.com/junikematsu/shitto-mania-dic/tree/main/nlp2026)
- Hugging Face: [Dataset Card](https://huggingface.co/datasets/samuraijun/shitto-mania-dic)
