# 初回起動ログイン画面 下書き

| 項目 | 内容 |
| --- | --- |
| updated | 2026-05-26 |
| related | `docs/features.md#初回起動` |

## 目的

ユーザーが迷わずゲスト開始できる入口を作り、Apple / Google / class code は将来の認証導線としてブランド上表示する。

## 対象ユーザー

- 対象レベル: JLPT N2
- 利用前提: 未ログイン、初回起動、またはオンボーディング未完了

## ユーザーフロー

1. 初回起動時にログイン画面を表示する。
2. `Get Started` を押すとゲストセッションを作り、オンボーディングへ進む。
3. `Login with class code` を押すとコード入力画面を表示する。
4. class code 送信時は「無効なコードです」と表示し、`Get Started` へ戻れるようにする。
5. Apple / Google は押下時に準備中の短い説明を表示する。

## 画面/状態

| 画面または状態 | 主アクション | 表示内容 | 遷移先 |
| --- | --- | --- | --- |
| 初回起動画面 | `Get Started` | ロゴ、アプリ名、メッセージ、4つの導線 | オンボーディング |
| class code入力 | `CONTINUE` | コード入力、説明、戻る導線 | 無効コード表示 |
| 無効コード | `Get Started` | 「無効なコードです」、補足文 | オンボーディング |
| Apple / Google準備中 | `Get Started` | 準備中メッセージ | オンボーディング |

含める状態:

- ローディング: ゲストセッション作成中。
- 空状態: class code 未入力では送信不可。
- 成功: `Get Started` でオンボーディングへ進む。
- エラー: class code は常に無効コード表示。
- オフライン: ゲスト開始は可能。Apple / Google / class code は準備中または無効表示。
- 権限不足: なし。

## データ要件

| データ | 型/形式 | 必須 | 説明 |
| --- | --- | --- | --- |
| guestId | string | yes | ローカル生成するゲスト識別子 |
| hasSeenEntry | boolean | yes | 初回起動画面を表示済みか |
| classCodeAttempt | string | no | 入力されたコード。保存は任意で、認証には使わない |

Zod では `guestId` の空文字禁止、`classCodeAttempt` の最大長を検証する。

## API/Firebase 要件

初回リリースでは Apple / Google / class code の本番認証 API を呼ばない。将来接続のため、UIイベント名は `entry_get_started`, `entry_class_code_invalid`, `entry_apple_pending`, `entry_google_pending` として分析可能にする。

## コンテンツ要件

問題コンテンツは扱わない。

## エッジケース

- 未ログイン: `Get Started` で進行可能。
- データ未作成: 新しい `guestId` を作る。
- 通信失敗: ゲスト開始はローカルで継続する。
- 途中離脱: 次回起動時もオンボーディング未完了として扱う。
- 重複送信: `Get Started` は処理中に無効化する。
- 端末変更: ゲスト状態は移行しない。

## 実装対象外

- Apple / Google の実認証。
- class code のクラス参加。
- ゲストからログインアカウントへの移行。

## 受け入れ条件

- [ ] `Get Started` が最も強い主アクションとして表示される。
- [ ] class code 入力後に「無効なコードです」と表示される。
- [ ] Apple / Google は本番認証を必須にしない。
- [ ] ゲスト開始後にオンボーディングへ進む。

## 確認すべき質問

- 未定。
