# Café Le Pont（るぽん）公式サイト

福島県白河市のカフェ「Café Le Pont（るぽん）」のウェブサイト。GitHub Pages で公開する構成です。

## 構成

```
rupon/
├─ index.html              シングルページのLP
├─ assets/
│  ├─ css/style.css        スタイル
│  ├─ img/                 サイトで使用する画像（公開対象）
│  │  ├─ logo.png          明るい背景用（濃色インク）
│  │  ├─ logo-light.png    濃紺背景用（クリーム）
│  │  ├─ logo-180.png      ファビコン / apple-touch-icon
│  │  └─ photos/           Web最適化済みの店舗写真 12枚（約1.0MB）
│  ├─ photos/              取得した写真の原本 35枚（.gitignore で非公開）
│  └─ src/                 支給素材の原本（.gitignore で非公開）
├─ robots.txt              確認中はクローラをブロック
├─ .nojekyll
├─ RESEARCH.md             掲載情報の出典と調査メモ
└─ README.md
```

## ブランド

コンセプトボード（支給素材 `assets/src/concept-board.jpg`）に準拠。

| 項目 | 内容 |
|---|---|
| 正式表記 | Café Le Pont（るぽん） |
| タグライン | 人と人、街と人、食と人をつなぐ／白河の小さなフランスの架け橋 |
| フランス語コピー | *Un pont entre les gens, les saveurs et le cœur.*（人と味と心をつなぐ橋） |
| 創業表記 | depuis 2024 |
| フッターコピー | Le Pont　つなぐ、やさしい時間 〜 |

### カラー（コンセプトボードから抽出）

| 用途 | 値 |
|---|---|
| ネイビー（主色） | `#152232` |
| ネイビー（濃淡） | `#1E3047` / `#2A3E56` |
| クリーム | `#EAE0D4` |
| ペーパー | `#FAF6EF` / `#F2EBE0` |
| ゴールド | `#A98C55` / `#C7AE7C` |

### フォント

- 欧文・数字: Cormorant Garamond（ロゴのセリフ体に合わせた高コントラスト明朝）
- 和文見出し: Noto Serif JP
- 和文本文: Noto Sans JP

### ロゴの生成方法

支給された `assets/src/logo-original.jpg`（白背景JPEG）から、
輝度をアルファに復元して背景を透過し、余白をトリムして生成しています。
フランス国旗は彩度でマスクを分けているため色が保持されます。
再生成が必要な場合は git 履歴のコミット「ブランド資産の取り込み」を参照してください。

## 掲載情報の出典

- コンセプトボード・ロゴ（店舗支給、2026-08-19 受領）
- 食べログ https://tabelog.com/fukushima/A0703/A070301/7020106/
- ふくしまほんものの旅 https://www.tif.ne.jp/hontabi/info.html?info=286

詳細は `RESEARCH.md` を参照。

## 公開前チェックリスト

### 1. 要確認（情報の食い違い・不足）

- [ ] **創業年** — コンセプトボードは「depuis 2024」、食べログ／観光協会は「2025年に誕生」。
      サイトは支給素材に合わせて **2024** で記載中。どちらが正か要確認。
- [ ] **夜営業の曜日** — 店頭ポスターは「営業夜（木)(金)(土)」= 木金土のみ。
      食べログは日曜も夜営業と読める記載。サイトは**店頭ポスターに合わせて木・金・土**で記載中。
- [ ] 郵便番号（未記載）
- [ ] メニューの正式名称と価格（判明しているのは「セット +¥330 税込でソフトクリーム」のみ）
- [ ] 運営法人名・就労支援事業所との関係（フッターに載せるか判断）
- [ ] 祝日の扱い（ランチは祝日営業と確認済み、夜は不明）

### 2. 写真素材

食べログの**「お店から」タブ（`dtlphotolst/smp2/`）** に掲載されている店舗提供写真 35枚を取得し、
うち 12枚を Web 用に最適化して使用しています。

- **店舗提供写真のため権利は店舗側にありますが**、取得元は食べログです。
  正式公開前に、店舗から原本データを直接受け取る形に切り替えることを推奨します。
- コンセプトボードの写真はすべて**イメージ画像**（ボード内に「Instagram の世界観イメージ」と明記）のため未使用。
- `assets/src/tif-seiro-set.jpg` は観光協会掲載画像。第三者素材のため未使用・非公開。

内訳: 料理28 / 内観3 / 外観3 / その他1（店頭ポスター）。原本は 715〜946px 幅。
ヒーローに全画面写真を使うには解像度が不足するため、ヒーローはロゴ主体のままとし、
写真はギャラリー帯とメニューカードで使っています。

#### 取得方法のメモ

- `https://tblg.k-img.com/resize/...` は **403 Forbidden**（ホットリンク保護）
- `https://tblg.k-img.com/restaurant/images/Rvw/<id>/<hash>.jpg` は Referer 付きで **200**、これが原寸
- サムネイルのURL（`150x150_square_<hash>.jpg` 等）から `<hash>` を抜けば原寸が取れる
- 各カテゴリページの先頭に店舗メイン写真が重複して出るため、ハッシュ照合で重複排除が必要

### 3. 公開設定

確認フェーズ中は検索避けをかけています。**正式公開時に以下を解除**してください。

- `index.html` の `<meta name="robots" content="noindex, nofollow">` を削除
- `robots.txt` を `Disallow: /` から `Allow: /` に変更

## ローカル確認

```bash
cd rupon
python -m http.server 8000
# → http://localhost:8000
```

## GitHub Pages へのデプロイ

```bash
cd rupon
gh repo create rupon --public --source=. --push
gh api -X POST repos/:owner/rupon/pages -f "source[branch]=main" -f "source[path]=/"
```

公開URL: `https://<account>.github.io/rupon/`
