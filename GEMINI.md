# OHAYO CENTER (`ohayocenter.com`) サイト専用ルール

このフォルダは **OHAYO CENTER**（オンライン日本語レッスン＆日本語学習教材サイト）の GitHub Pages 用リポジトリです。このフォルダ内で作業するときは、以下のルールに従ってください。

---

## 1. サイト基本情報
- **公開URL**: `https://ohayocenter.com/`
- **GitHub リポジトリ**: `ohayocenter/ohayocenter.github.io`（公開ブランチ: `main`）
- **構成**: ビルドツールを使わない純粋な静的サイト（HTML / CSS / JavaScript を各 `.html` ファイルにまとめる方式）
- **重要ファイル・レイアウト方針**:
  - `CNAME`（独自ドメイン設定: `ohayocenter.com`）は **絶対に削除・変更しない**。
  - `index.html` の **Lesson Course（料金・決済・予約）は既存生徒がすぐ使えるようトップ上部に固定**し、予約リンク・支払いリンク・特定商取引法に基づく表記・プライバシーポリシーなどは明示的な指示がない限り変更しない。
  - 教材ページの下部では **体験レッスン案内を主役** にし、**Buy Me a Coffee は脇役としてその下に残す**。

---

## 2. ファイル構成・命名ルール
- **HTMLページ**: ルート直下に配置する（例: `index.html`, `audioblog.html`, `adj.html`, `idioms.html`, `onomato.html`, `trip-*.html`）。
- **画像ファイル**:
  - 軽量な **`.webp`** 形式を基本とし、容量の大きい `.png` ファイルは置かない（ファビコンの `icon.png` や OGP 画像の `.jpg` などの例外を除く）。
  - テーマ別フォルダ（`images/`, `trip-img/` など）がある場合は既存構成に合わせる。
- **音声ファイル**:
  - 教材ごとの専用フォルダ（`adj-audio/`, `anime-audio/`, `fc-audio/`, `hira-word-audio/`, `kana-audio/`, `kata-word-audio/`, `kata2-word-audio/`, `trip-audio/`, `trip1-audio/` など）に `.mp3` 形式で整理する。
  - Audio Blog 用はルート直下に `vol{番号}-1.mp3` / `vol{番号}-2.mp3` およびサムネイル `vol{番号}.webp` で揃える。
- **ファイル名チェック**:
  - 二重拡張子（例: `.html.html`）や大文字・小文字の不一致によるリンク切れを防ぐため、HTML内の参照パスと実際のファイル名が完全一致しているか必ず確認する。

---

## 3. デザイン・共通仕様
既存の親しみやすい雰囲気を保つため、新規ページ作成や修正時は以下を基本とする。

- **ブランドカラー**:
  - メイン（オレンジ）: `#ff9f43`（`--primary`）
  - 薄い背景オレンジ: `#fff5eb`（`--primary-light`）
  - 見出し・ロゴ文字: `#2c3e50`（`--dark`）
  - 本文文字: `#444`（`--text`）
- **フォント**: Google Fonts の `Noto Sans JP`（本文）と `Sawarabi Mincho`（ロゴ・見出し）を使用。
- **ファビコン**: すべてのページで共通の `icon.png` を指定する（`rel="icon"`, `rel="apple-touch-icon"`, `sizes="192x192"`）。
- **上部ナビゲーション**:
  - `OHAYO CENTER` ロゴ＋ `LESSONS` / `PROFILE` / `MATERIAL` へのリンクを上部固定（高さ `70px`）で配置する。
  - モバイル表示（幅 `600px` 以下）でも文字が折り返されたり横スクロールが発生したりしないようにする。
- **SNS共有設定（OGP / Twitter Card）**:
  - 新規ページ作成・大幅更新時は `og:type`, `og:site_name`（`OHAYO CENTER`）, `og:title`, `og:description`, `og:url`（`https://ohayocenter.com/<ファイル名>`）, `og:image`（標準は `https://ohayocenter.com/og-image-onigiri.jpg`）, `twitter:card`（`summary_large_image`）を設定する。

---

## 4. コンテンツ追加時のチェックポイント
- **新しい教材ページを追加したとき**:
  - `index.html` の該当カテゴリ（Culture & Fun / Travel / Beginner / Intermediate / Advanced）にカードを追加するか確認する。
  - 必要に応じて `index.html` の **What's New（`.update-board`）** の先頭に更新情報を追記する（日付形式: `YYYY.MMM.DD` 例: `2026.NOV.22`）。
- **Audio Blog を追加したとき**:
  - `audioblog.html` の `blogPosts` 配列の先頭に新しいエピソードを追加し、対応する `.mp3` と `.webp` が揃っているか確認する。
- **学習者向けの表記**:
  - 英語の説明文や日本語教材の本文は、海外の学習者にとって自然でわかりやすい表現にする（日本語教材本文や英語UIの言語は、ページ本来の言語に合わせる）。

---

## 5. 編集・GitHub 反映（公開）の安全ルール
- **機密情報の厳禁**: ID・パスワード・APIキー・個人情報・非公開メモなどの機密情報は、**`GEMINI.md` を含むすべてのファイルに絶対に書かない・GitHub へ上げない**こと（このリポジトリは公開リポジトリのため）。
- **作業前の確認**: 編集前に GitHub とのズレ（未取り込みの更新）がないか確認し、古い状態のまま作業を始めない。
- **影響範囲を絞る**: 依頼された箇所以外の既存デザインや動作を勝手に書き換えない。別のリンク切れや不具合を見つけた場合は、勝手に直さずユーザーへ報告して確認する。
- **公開前の承認**: `main` ブランチへのプッシュ（`git push`）はそのまま本番サイト（`ohayocenter.com`）に公開されるため、**変更内容の要約を説明し、ユーザーの許可を得てから実行する**。
- **コミットメッセージ**: 何を更新したか後から見返してわかる簡潔なメッセージにする（例: `Add Audio Blog Vol.8`, `Update index.html links`）。
- **変更後の確認**: HTML・画像・音声のパスミスや、PC・スマホ両方での表示崩れがないかチェックしてから完了報告する。
