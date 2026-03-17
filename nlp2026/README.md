# NLP2026 Experiment Data

嫉妬AI辞書（Jealousy AI Dictionary）のNLP2026論文で使用した実験データです。

## English Summary

This repository contains the dataset and additional experiment results for our NLP2026 study on language resource design in the RAG era.

Using a 321-episode Japanese dataset derived from the essay series *Shitto Mania*, we test whether structured metadata improves retrieval accuracy compared to full text.

**Key finding:** structured metadata alone outperforms full text by **11.1×** in TF-IDF retrieval (**59.0% vs 5.3% Recall@10**, p < 0.001). The advantage also persists in dense retrieval (E5).

Our central claim is simple: in the RAG era, language resources should be designed not only as text for humans to read, but as **referenceable specifications for AI systems**.

## Files

| File | Description |
| --- | --- |
| `nami_episode_table_cleaned_with_core_text.csv` | Dataset (321 episodes, 25 metadata fields + core_text) |
| `reference_queries_autogen_400.csv` | Evaluation queries (400 queries, 4 styles × 100) |
| `experiment_results_all_conditions.csv` | Experiment results: TF-IDF (1,600 rows: 400 queries × 4 conditions) |
| `nlp2026_extended_per_query_results.csv` | **[New]** Extended experiment results: TF-IDF + Dense (1,600 rows: 400 queries × 4 conditions) |

## データセット概要 / Dataset Overview

- **原典 / Source**: 婦人公論.jp 連載『嫉妬マニア』（著者：斉藤ナミ氏、2025年3月〜12月）
  - https://fujinkoron.jp/category/shitto_mania
- **エピソード数 / Episodes**: 321件
- **メタデータ項目 / Metadata fields**: 25項目（構造化メタデータ）
- **評価クエリ / Evaluation queries**: 400件（4種類 × 100件）

## 主要結果 / Key Results（論文報告）

論文で報告したTF-IDFによる実験結果。構造クエリ（STRUCT, n=300）における Recall@10：

| Condition | R@10 |
| --- | --- |
| core_text（構造化メタデータのみ） | **59.0%** |
| long_text_only（本文のみ） | 5.3% |
| core_plus_long（メタデータ+本文） | 58.3% |

構造化メタデータのみの表現は、本文のみの表現より **11.1倍** 優れた検索性能を示した（p < 0.001）。

## 追加実験 / Extended Experiment: TF-IDF vs Dense Retrieval

論文報告後、TF-IDF（疎ベクトル）に加えてDense Retrieval（密ベクトル: multilingual-e5-large）による追加実験を実施し、「参照可能性」が検索手法に依存しない汎用的な設計原理であることを検証した。

### 実験条件 / Conditions

| Condition | Retrieval | Document Representation |
| --- | --- | --- |
| `tfidf_core_text` | TF-IDF (sparse) | 構造化メタデータのみ |
| `tfidf_long_text` | TF-IDF (sparse) | 本文テキストのみ |
| `dense_e5_core_text` | multilingual-e5-large (dense) | 構造化メタデータのみ |
| `dense_e5_chunked_long_text` | multilingual-e5-large (dense) | 本文テキスト（チャンク分割） |

### 全体結果 / Overall Results（全400クエリ）

| Condition | Hit@10 | Avg Rank |
| --- | --- | --- |
| **tfidf_core_text** | **69.2%** | **13.2** |
| dense_e5_core_text | 53.0% | 42.2 |
| tfidf_long_text | 29.0% | 114.3 |
| dense_e5_chunked_long_text | 28.0% | 51.1 |

### 構造クエリのみ / STRUCT Queries Only（n=300, shorttext除外）

| Condition | Hit@10 | Avg Rank |
| --- | --- | --- |
| **tfidf_core_text** | **59.0%** | **17.2** |
| dense_e5_core_text | 37.3% | 55.8 |
| dense_e5_chunked_long_text | 6.3% | 66.9 |
| tfidf_long_text | 5.3% | 152.0 |

### クエリスタイル別 / Results by Query Style

| Condition | shorttext | comparison | distance_effort | behavior |
| --- | --- | --- | --- | --- |
| tfidf_core_text | 100.0% | 61.0% | 51.0% | 65.0% |
| dense_e5_core_text | 100.0% | 44.0% | 17.0% | 51.0% |
| tfidf_long_text | 100.0% | 5.0% | 7.0% | 4.0% |
| dense_e5_chunked_long_text | 93.0% | 8.0% | 7.0% | 4.0% |

### 追加実験の知見 / Key Findings

1. **汎用性**: 構造化メタデータ（core_text）の優位性は、TF-IDFだけでなくDense Retrievalでも成立する（STRUCT: 37.3% vs 6.3%、5.9倍）。「参照可能性」は検索手法に依存しない言語資源設計の原理である。

2. **設計 > 計算力**: TF-IDF + core_text（69.2%）が Dense E5 + core_text（53.0%）を上回った。高コストのベクトル検索でも、適切に設計されたメタデータ＋TF-IDFには及ばない。ペア分析では、構造クエリの67%でTF-IDFがDense E5に勝利した。

3. **Dense検索はlong_textを救わない**: Dense E5 + chunked_long_text のSTRUCT Hit@10 は 6.3% で、TF-IDF + long_text の 5.3% とほぼ同水準。意味ベクトルによる検索でも、構造化されていない本文からの検索精度は低いままである。

4. **クエリ特性との相互作用**: `distance_effort`（距離・努力）クエリではDense E5 coreが17.0%と特に低く、カテゴリカル情報のexact matchが重要な検索タスクではTF-IDFが大きく優位。一方、`behavior`（行動パターン）クエリではDense E5 coreが51.0%と比較的健闘し、行動記述とembedding空間の親和性を示唆。

## 利用条件 / Usage Policy

本データセットは、斉藤ナミ氏の著作「嫉妬マニア」（婦人公論.jp連載）を元に作成されています。
**著作権は斉藤ナミ氏に帰属します。**

- **学術研究・教育目的での利用のみ可**
- **商用利用（営利目的での利用・二次販売・生成AI学習への商業利用など）は禁止**
- 利用時には出典（斉藤ナミ「嫉妬マニア」婦人公論.jp）を明記してください。

This dataset is based on "Shitto-Mania" by Nami Saito, serialized on Fujinkoron.jp.
**Copyright © Nami Saito. All rights reserved.**

- **For research and educational purposes only.**
- **Commercial use, resale, or use in commercial AI training is prohibited.**
- Please credit: Nami Saito, "Shitto-Mania," Fujinkoron.jp.

## 著者協力 / Author Cooperation

本プロジェクトは、エッセイスト斉藤ナミ氏の【著者協力】（素材提供・コメント・全エピソードのラベル確認・メタデータのサンプル確認）を得て制作しました。最終的な分析・設計・公開判断は池松潤が行いました。

This project was conducted with the cooperation of essayist Nami Saito (material provision, comments, label verification for all episodes, and sample review of metadata). All final analysis, design, and publication decisions are the responsibility of Jun Ikematsu.

## Reference

池松 潤 (2026). RAG時代の言語資源設計原理 ー構造化テキストによる「参照可能性」の実証. 言語処理学会第32回年次大会.
https://anlp.jp/proceedings/annual_meeting/2026/pdf_dir/Q5-8.pdf

## License

See [LICENSE](../LICENSE) in the root directory.
