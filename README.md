# 嫉妬マニア AI辞書データセット (Jealousy Mania AI Dictionary)

## 概要

これは、婦人公論.jpで連載されたエッセイ『嫉妬マニア』（著者：斉藤ナミ）の連載記事を元に作成した、AI向けの「嫉妬プロフィール帳」データセットです。本データセットの作成は、著者の斉藤ナミさんとの共同作業です。

人間の複雑な感情である「嫉妬」に関する語彙や文脈を、AIが学習できるように構造化しました。

## スキーマ
|列名|説明|
|---|---|
|番号|#1-#18|
|掲載日|YYYY/MM/DD|
|記事タイトル|正式タイトル|
|嫉妬の方向|本人→他者/他者→本人/双方向|
|分析対象|主体嫉妬/被嫉妬/概念探求|
|嫉妬の対象|総括ラベル（人物名に限定しない）|
|嫉妬の構造（3分類）|ゼロサム/不可侵領域/正当性希求（=自己理想嫉妬など）|
|…|他の列も続く|

## 使い方

データセットの詳しい仕様やPythonを使った分析方法は、以下のQiita記事で解説しています。

* **Qiita記事:** [AIと人間の「嫉妬」を分析してみた 〜連載『嫉妬マニア』の感情データセット公開〜](ここにあなたのQiita記事のURLを貼る)

## 関連リンク

* **斉藤ナミさんのnote (解説・対談記事):** [不倫バッシングは正義？それとも嫉妬？―#嫉妬マニア 連載記事・対談―](https://note.com/panko73/n/n1fd822067498)
* **データセット作成の元になった連載記事:**
    * [婦人公論.jp 斉藤ナミ 著者ページ](https://fujinkoron.jp/articles/-/18808)

## ライセンス

このデータセットは、[クリエイティブ・コモンズ 表示 - 継承 4.0 国際 ライセンス (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/deed.ja) の下に提供されています。

# Jealousy Dictionary (Shitto-Mania)
*A Japanese emotion dataset for AI — あなたの AI に“嫉妬”を理解させるために*

---

## What is this?
Jealousy Dictionary (“Shitto-Mania”) is a **high-quality, single-language Japanese dataset** focused on emotional nuance, extracted from the “嫉妬マニア” series.  
It is designed to support AI models in *understanding emotional context*, particularly jealousy, which is often subtle and culture-specific.

## Why it matters
Many AI models are English‐centric, and Japanese data is underrepresented (<0.1% in large multilingual models).  
By providing structured emotion data, this dataset helps global AI developers **reduce language bias** and **improve performance on Japanese tasks**.

## Use Cases
- RAG systems with Japanese output and emotion-sensitive tone  
- Sentiment / emotion analysis tasks specific to Japanese  
- Fine-tuning large language models to better handle Japanese idioms and emotional nuance  
- Cross-lingual model evaluation for bias analysis

---

## Data Format & Structure
Data is available in **CSV / JSON**. Below are core columns:

| Column | Description |
|---|---|
| `term` | A keyword or phrase (in Japanese) |
| `definition_ja` | Definition or explanation in Japanese |
| `context` | Example sentence or usage context |
| `polarity` | Emotional polarity (positive / negative / neutral) |
| `source` | Article ID, URL, or publication metadata |

You can also preview a **[sample CSV](./sample_data.csv)** to see data structure.

---

## Usage Example (Python)
```python
import pandas as pd

url = "https://raw.githubusercontent.com/junikematsu/shitto-mania-dic/main/sample_data.csv"
df = pd.read_csv(url)
print(df.head())

for _, row in df.iterrows():
    print(row["term"], ":", row["definition_ja"])


データを利用する際は、クレジットの表示をお願いします。
