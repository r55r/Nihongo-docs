# DESIGN.md

## UI Design Rules

このプロジェクトの UI は、Duolingo のように「迷わない」「楽しい」「次にやることが一目でわかる」体験を目指す。  

このドキュメントは、適宜更新してください。

---

## 1. Core Principles

### 1.1 One Screen, One Main Action

各画面には、ユーザーが次に取るべき主要アクションを 1 つだけ明確に置く。

Good:

- 「次へ」
- 「始める」
- 「回答する」
- 「続ける」

Avoid:

- 同じ強さのボタンを複数並べる
- 画面内に判断ポイントを増やしすぎる
- 重要なアクションをテキストリンクだけにする

---

### 1.2 Progress Should Always Be Visible

ユーザーが「今どこにいて、どれくらい進んだか」を常に理解できるようにする。

Use:

- プログレスバー
- ステップ表示
- レベル表示
- 完了チェック
- 連続達成日数
- 小さな達成演出

Avoid:

- 終了までの距離がわからない長いフォーム
- 成功したかどうかが曖昧な操作
- 画面遷移後に進捗が消える UI

---

### 1.3 Friendly, Not Childish

親しみやすくするが、幼稚にしすぎない。

Good:

- やさしい言葉
- 丸みのあるカード
- 明るい余白
- ポジティブなフィードバック
- 小さなアニメーション

Avoid:

- 過剰な装飾
- ふざけすぎた文言
- 情報量を削りすぎて意味が曖昧になる表現
- ユーザーを子ども扱いするトーン

---

## 2. Layout Rules

### 2.1 Use Card-Based Layouts

情報はカード単位で整理する。  
1 つのカードには 1 つの意味・目的だけを持たせる。

Card examples:

- レッスンカード
- クイズカード
- 達成カード
- 通知カード
- 設定項目カード

Card rules:

- 角丸を使う
- 十分な余白を取る
- 見出し、説明、アクションを明確に分ける
- 押せるカードは押せる見た目にする

---

### 2.2 Keep Screens Vertically Simple

基本レイアウトは縦方向に整理する。

Preferred order:

1. Header
2. Progress / Status
3. Main content
4. Primary action
5. Secondary action

Avoid:

- 左右に複雑な情報を詰め込む
- メイン操作を画面上部・中部・下部に分散させる
- スクロールしないと主要アクションが見えない画面

---

### 2.3 Primary Action Stays Near the Bottom

主要ボタンは、特にモバイルでは画面下部に固定または配置する。

Rules:

- Primary button は画面下部に置く
- Secondary action は控えめに表示する
- 危険操作は primary button と同じ見た目にしない
- ボタンラベルは動詞から始める

Good:

- 「次へ」
- 「回答する」
- 「レッスンを始める」
- 「もう一度挑戦する」

Avoid:

- 「OK」
- 「送信」
- 「確認」
- 「実行」

ただし、文脈上明確な場合のみ短いラベルを許可する。

---

### 2.4 Make Screens Understandable at a Glance

学習画面は、文字を読まなくても大まかな意味が伝わるようにする。

Use:

- 目的がわかる画像またはイラスト
- レッスン種別を示すアイコン
- 進捗が見えるカード
- レベル、streak、完了状態の視覚表示
- 1カード1メッセージの短いラベル

Avoid:

- 説明文だけで理解させる画面
- 長い段落を複数並べる
- 見出し、説明、補足がすべて同じ強さに見えるUI
- 画像やアイコンが意味を持たない装飾だけになる状態

---

## 3. Visual Style

### 3.1 Use Rounded, Soft Shapes

UI 全体は丸みのある形状を基本にする。

Recommended:

- Buttons: large radius
- Cards: medium radius
- Inputs: medium radius
- Badges: pill shape
- Icons: rounded style

Avoid:

- 鋭い角
- 硬い罫線だらけの UI
- 無機質な管理画面風レイアウト

---

### 3.2 Use Color as Guidance, Not Decoration

色は意味を持たせて使う。

Color roles:

- Primary: 主要アクション
- Success: 正解、完了、達成
- Warning: 注意、未完了
- Error: 間違い、失敗
- Neutral: 背景、枠、補助情報

Rules:

- Primary color は最重要ボタンに限定する
- Error color は本当に必要な箇所だけに使う
- 成功時は明るくポジティブに見せる
- 背景色は淡く、コンテンツを邪魔しない色にする

Avoid:

- 画面内に強い色を多用する
- 色だけで状態を伝える
- 成功・警告・エラーの色を曖昧にする

---

### 3.3 Icons Should Explain, Not Decorate

アイコンは意味を補助するために使う。

Good:

- レッスン種別のアイコン
- 完了チェック
- ロック状態
- 連続記録
- ヒント
- 音声再生

Avoid:

- 意味のない装飾アイコン
- ラベルなしでは理解できないアイコン
- 同じ意味に複数のアイコンを使う

---

## 4. Typography

### 4.1 Text Must Be Short and Direct

文言は短く、具体的にする。

Good:

- 「よくできました」
- 「あと 1 問です」
- 「もう一度試しましょう」
- 「ヒントを見る」
- 「5 分で完了します」

Avoid:

- 「処理が正常に完了しました」
- 「入力内容に不備があります」
- 「以下の内容をご確認のうえ、次の操作を行ってください」

---

### 4.2 Use Encouraging Microcopy

失敗時もユーザーを責めない。

Good:

- 「惜しいです。もう一度試しましょう」
- 「ここだけ確認してみましょう」
- 「ヒントを使えます」
- 「次はうまくいきます」

Avoid:

- 「間違っています」
- 「無効な入力です」
- 「エラーが発生しました」
- 「失敗しました」

必要な場合は、原因と次の行動を必ずセットで示す。

Example:

```text
メールアドレスの形式が違うようです。
例: name@example.com
````

---

## 5. Interaction Rules

### 5.1 Give Immediate Feedback

ユーザー操作には即座に反応する。

Required feedback:

* ボタン押下時の visual feedback
* 回答後の正誤表示
* 保存完了表示
* ローディング状態
* 無効状態
* 達成時の小さな演出

Avoid:

* 押したかわからないボタン
* 保存されたかわからないフォーム
* 無音・無反応の状態変化
* 長いローディングで説明がない状態

---

### 5.2 Use Small Rewards

完了・継続・成功には小さな報酬を与える。

Examples:

* チェックマーク
* XP / points
* バッジ
* 連続記録
* 完了アニメーション
* 「あと少し」の励まし
* 次の目標の提示

Rules:

* 報酬は短く表示する
* 操作を邪魔しない
* 成果と報酬の関係を明確にする
* 過剰な演出でテンポを悪くしない

---

### 5.3 Make Failure Recoverable

失敗してもすぐにやり直せる UI にする。

Rules:

* 間違いはその場で説明する
* 次に何をすればよいか示す
* 入力内容は消さない
* 戻る操作を安全にする
* やり直しボタンを明確にする

Good:

```text
惜しいです。
「their」は「彼らの」という意味です。
もう一度試しましょう。
```

Avoid:

```text
不正解です。
```

---

## 6. Component Rules

### 6.1 Buttons

Primary button:

* 最も目立つ色
* 画面に原則 1 つ
* 大きめのタップ領域
* 明確な動詞ラベル

Secondary button:

* Primary より弱い見た目
* 境界線またはテキストボタン
* 重要度を下げる

Danger button:

* 削除・リセットなどに限定
* 確認ステップを入れる
* Primary と同じ色にしない

---

### 6.2 Cards

Cards should:

* 1 カード 1 目的
* アイコンまたはステータスを持つ
* 押せる場合は hover / pressed state を持つ
* 完了・未完了・ロック状態を明確にする

Card states:

* Available
* In progress
* Completed
* Locked
* Disabled

---

### 6.3 Progress Indicators

Progress indicators should:

* 現在位置を示す
* 完了量を示す
* 残り量を暗示する
* 成功時に変化する

Examples:

```text
3 / 10
あと 2 問
70% 完了
Day 5 streak
```

Avoid:

* 意味のないゲージ
* 進捗が戻るように見える表現
* 実際の進行と一致しない表示

---

### 6.4 Forms

Forms should feel like guided steps.

Rules:

* 入力項目は一度に出しすぎない
* 1 画面 1〜3 項目を基本にする
* 入力例を表示する
* エラーは該当項目の近くに出す
* 送信前より入力中に支援する
* 成功後は明確な完了表示を出す

Avoid:

* 長い一括フォーム
* 上部にまとめて出るエラー一覧だけ
* Placeholder だけに頼るラベル
* 必須項目だらけの画面

---

## 7. Motion and Animation

### 7.1 Motion Should Clarify State

アニメーションは状態変化を理解しやすくするために使う。

Use motion for:

* 正解・完了
* カードの出現
* ステップ遷移
* レベルアップ
* ボタン押下
* ローディング

Avoid:

* 意味のないループアニメーション
* 操作を待たせる長い演出
* 毎回大きく動く UI
* 画面酔いを起こす動き

---

### 7.2 Keep Animations Short

Recommended:

* Button feedback: 100–200ms
* Card transition: 150–300ms
* Success animation: 500–1200ms
* Celebration: 1–2 seconds max

---

## 8. Accessibility Rules

### 8.1 Do Not Rely on Color Alone

状態は色だけでなく、テキスト・アイコン・形でも示す。

Good:

* 緑 + チェック + 「完了」
* 赤 + エラー文 + 該当項目の説明
* グレー + ロックアイコン + 「まだ利用できません」

---

### 8.2 Tap Targets Must Be Large Enough

Interactive elements should be easy to tap.

Rules:

* 主要ボタンは十分な高さを持たせる
* アイコンボタンにはラベルまたは accessible name を付ける
* 小さなテキストリンクだけを主要操作にしない
* 隣接するタップ領域には十分な間隔を空ける

---

### 8.3 Copy Must Be Understandable

専門用語を避け、行動に直結する表現にする。

Avoid:

* 「認証プロセスを開始」
* 「セッションが無効化されました」
* 「パラメータが不足しています」

Prefer:

* 「ログインしてください」
* 「もう一度開いてください」
* 「名前を入力してください」

---

## 9. Gamification Rules

### 9.1 Gamification Must Support the Goal

ポイント・バッジ・連続記録は、ユーザーの目的達成を助けるために使う。

Use when:

* 継続を促す
* 進歩を見せる
* 完了を祝う
* 次の行動を示す

Avoid:

* 意味のないポイント付与
* 競争を煽りすぎるランキング
* ユーザーを焦らせる過剰な通知
* 本来のタスクより報酬が目立つ設計

---

### 9.2 Show the Next Achievable Goal

ユーザーには常に「次に達成できそうな目標」を見せる。

Examples:

* 「あと 1 問で完了」
* 「あと 5 XP でレベルアップ」
* 「今日の目標まであと 3 分」
* 「次のレッスンを解放できます」

---

## 10. Empty, Loading, and Error States

### 10.1 Empty States Should Invite Action

空状態は単なる空白にしない。

Good:

```text
まだレッスンがありません。
最初のレッスンを作成しましょう。
[レッスンを作成]
```

Avoid:

```text
データがありません。
```

---

### 10.2 Loading States Should Feel Lightweight

Loading rules:

* Skeleton UI を優先する
* 長い処理では説明を出す
* ボタンは loading state にする
* 二重送信を防ぐ

---

### 10.3 Error States Should Explain Recovery

Error message must include:

1. 何が起きたか
2. なぜ問題か
3. 次に何をすればよいか

Good:

```text
保存できませんでした。
通信が不安定なようです。
少し待ってからもう一度試してください。
```

Avoid:

```text
エラーが発生しました。
```

---

## 11. Navigation Rules

### 11.1 Keep Navigation Shallow

主要機能へは 1〜2 タップで到達できるようにする。

Rules:

* 重要画面を深い階層に置かない
* 戻る操作を予測可能にする
* 現在地を明確にする
* 未完了タスクへすぐ戻れるようにする

---

### 11.2 Always Offer a Clear Continue Path

中断後に再開しやすくする。

Examples:

* 「前回の続きから始める」
* 「今日の目標を続ける」
* 「未完了のレッスンに戻る」

---

## 12. Tone and Voice

### 12.1 Voice Principles

文体は以下を守る。

* 明るい
* 短い
* 具体的
* 励ます
* 責めない
* 命令しすぎない

---

### 12.2 Message Examples

Success:

```text
よくできました！
```

Progress:

```text
あと少しです。
```

Failure:

```text
惜しいです。もう一度試しましょう。
```

Hint:

```text
ヒントを見てみましょう。
```

Completion:

```text
今日の目標を達成しました。
```

---

## 13. Anti-Patterns

Do not use:

* 1 画面に複数の primary buttons
* 説明なしのアイコンだけナビゲーション
* 色だけに依存した状態表示
* 長すぎるフォーム
* 冷たいエラーメッセージ
* 押せるかどうかわからないカード
* 情報を詰め込みすぎたダッシュボード
* 過剰なアニメーション
* ユーザーを責める文言
* ブランドやキャラクターの模倣

---

## 14. Acceptance Checklist

UI を実装・レビューするときは、以下を確認する。

* [ ] この画面の主要アクションは 1 つか
* [ ] ユーザーは現在位置と進捗を理解できるか
* [ ] ボタンラベルは具体的な動詞になっているか
* [ ] 成功・失敗・読み込み状態が明確か
* [ ] 失敗時に次の行動が示されているか
* [ ] カードやボタンは押せる見た目になっているか
* [ ] 色だけで状態を伝えていないか
* [ ] 文言は短く、やさしく、具体的か
* [ ] 画面内の情報量は多すぎないか
* [ ] アニメーションは操作を邪魔していないか

---

## 15. Design Direction Summary

この UI は、次の印象を目指す。

* わかりやすい
* 楽しい
* 続けたくなる
* 迷わない
* 失敗しても怖くない
* 進歩が見える
* 操作が軽い
* 初心者にやさしい

最優先事項は「ユーザーが次に何をすればよいか、迷わないこと」である。
