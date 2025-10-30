## フロントマター

### 概要

マークダウンファイルの先頭に、フロントマター（メタデータ）を記載します。フロントマターは、ファイルの最初の行から `---`（ハイフン3個）で始まり、`---` で終わる行までの間に記載します。

### 記法

```markdown
---
key1: value1
key2: value2
key3: value3
---
```

### 設定項目

#### ブック用フロントマター（ブックの説明ファイルに記載）

| フィールド | 必須 | 説明 |
|-----------|------|------|
| `title` | ※ | ブック用カバーページのタイトルを設定 |
| `description` | ※ | ブック用カバーページの概要を設定 |
| `displayLanguage` | ※ | ブック用カバーページの言語を設定（`ja`、`en`、`ko`） |
| `prompt` | | ブック用カバーページのプロンプトを設定 |
| `difficulty` | | 難易度（例: 1, 2, 3, 4, 5=最大難易度） |
| `duration` | | 希望所要時間（分）。個別ページの合計がブックの時間より大きくなる前提でOK |

#### ページ用フロントマター（各ページのマークダウンファイルに記載）

| フィールド | 必須 | 説明 |
|-----------|------|------|
| `title` | ※ | 章やワークのタイトル（例: "変数とデータ型"） |
| `slug` | ※ | URL用の識別子（例: `chapter01/work02`）。ファイル名を元に作成し、分かりやすくしましょう |
| `description` | ※ | ページの概要 |
| `type` | ※ | コンテンツタイプ：`explain`（説明）、`work`（ワーク）、`exercise`（練習問題）、`practice`（発展問題）、`column`（コラム） |
| `document_type` | | ドキュメントタイプ（デフォルト: `markdown`）。以下から選択：<br>- `markdown`：マークダウン<br>- `youtube`：動画<br>- `google-slide`：Googleスライド<br>- `google-document`：Googleドキュメント |
| `document_url` | | `document_type`がマークダウン以外の場合に使用するURL |
| `relation` | | 関連ページのslug（カンマ区切り）。例: `chapter01/work01,chapter01/work02` |
| `difficulty` | | 難易度（例: 1, 2, 3, 4, 5=最大難易度） |
| `displayLanguage` | | ページの言語（`ja`、`en`、`ko`） |
| `duration` | | 希望所要時間（分） |

**注：**
- `※` は必須項目です
- `seq`（連続番号）、`chapter_no`（チャプター番号）、`page_no`（ページ番号）、`chapter_title`、`chapter_slug` はシステム側で自動採番・生成されるため、フロントマターでは設定しません
- `document_type` の記載がない場合は、デフォルトで `markdown` として扱われます

### 使用例

**ブック用フロントマター：**
```markdown
---
title: JavaScriptの基礎
description: JavaScriptの基本的な概念を学ぶコース
displayLanguage: ja
prompt: JavaScriptの初心者向けコースです
difficulty: 2
duration: 120
---
```

**ページ用フロントマター（マークダウン）：**
```markdown
---
title: 変数とデータ型
slug: chapter01/work01
description: JavaScriptの変数宣言とデータ型について学びます
type: work
difficulty: 1
displayLanguage: ja
duration: 15
relation: chapter01/work02,chapter01/work03
---
```

**ページ用フロントマター（動画）：**
```markdown
---
title: 変数とデータ型の解説動画
slug: chapter01/video01
description: 変数とデータ型について、動画で詳しく解説します
type: explain
document_type: youtube
document_url: https://www.youtube.com/watch?v=xxxxx
difficulty: 1
displayLanguage: ja
duration: 10
---
```

**ページ用フロントマター（Googleスライド）：**
```markdown
---
title: 変数とデータ型のスライド
slug: chapter01/slide01
description: 変数とデータ型についてのスライド資料
type: explain
document_type: google-slide
document_url: https://docs.google.com/presentation/d/xxxxx
difficulty: 1
displayLanguage: ja
duration: 20
---
```

### 記載位置

フロントマターは、**マークダウンファイルの最初に記載**します。コンテンツ本体の前に配置してください。

```markdown
---
title: ページタイトル
slug: chapter01/work01
description: ページの説明
type: work
---

# ページタイトル

ここからコンテンツが始まります。
```
