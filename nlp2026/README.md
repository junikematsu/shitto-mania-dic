# NLP2026 Experiment Data

嫉妬AI辞書（Jealousy AI Dictionary）のNLP2026論文で使用した実験データです。

## Files

| File | Description |
|------|-------------|
| `nami_episode_table_cleaned_with_core_text.csv` | Dataset (321 episodes, 25 metadata fields + core_text) |
| `reference_queries_autogen_400.csv` | Evaluation queries (400 queries, 4 styles x 100) |
| `experiment_results_all_conditions.csv` | Experiment results (1,600 rows: 400 queries x 4 conditions) |

## データセット概要 / Dataset Overview

- **原典 / Source**: 婦人公論.jp 連載『嫉妬マニア』（著者：斉藤ナミ氏、2025年3月〜12月）
- **エピソード数 / Episodes**: 321件
- **メタデータ項目 / Metadata fields**: 25項目（構造化メタデータ）
- **評価クエリ / Evaluation queries**: 400件（4種類 x 100件）
- **実験条件 / Conditions**: 4条件（core_text, long_text_only, core_plus_long, short_text）

## 主要結果 / Key Results

構造クエリ（STRUCT, n=300）における Recall@10：

| Condition | R@10 |
|-----------|------|
| core_text（構造化メタデータのみ） | **59.0%** |
| long_text_only（本文のみ） | 5.3% |
| core_plus_long（メタデータ+本文） | 58.3% |

構造化メタデータのみの表現は、本文のみの表現より **11.1倍** 優れた検索性能を示した（p < 0.001）。

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
