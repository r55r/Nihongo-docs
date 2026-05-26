# N2オンボーディング 下書き

| 項目 | 内容 |
| --- | --- |
| updated | 2026-05-26 |
| related | `docs/features.md#1-オンボーディング` |

## 目的

N2 合格に必要な初期プロフィールを集め、10問診断と学習計画へつなげる。

## 対象ユーザー

- 対象レベル: JLPT N2
- 利用前提: ゲスト開始済み、オンボーディング未完了

## ユーザーフロー

1. 固定ヘッダーに説明と質問進捗を表示する。
2. 1画面1質問を基本に、約12問へ回答する。
3. 未回答の必須質問では `CONTINUE` を無効化する。
4. 完了後に10問診断へ進む。

## 画面/状態

| 画面または状態 | 主アクション | 表示内容 | 遷移先 |
| --- | --- | --- | --- |
| 質問 | `CONTINUE` | 質問、選択肢、進捗 | 次の質問 |
| 日付入力 | `CONTINUE` | 試験予定日、入力例 | 次の質問 |
| 完了 | `診断へ` | 10問診断の案内 | 診断 |

含める状態:

- ローディング: 保存中。
- 空状態: 必須未回答時は次へ進めない。
- 成功: プロフィールを保存する。
- エラー: 保存できない場合は画面内で再試行。
- オフライン: ローカル保存で継続。
- 権限不足: なし。

## データ要件

| データ | 型/形式 | 必須 | 説明 |
| --- | --- | --- | --- |
| displayName | string | yes | 呼び名 |
| uiLanguage | `ja` / `en` | yes | UI言語 |
| nativeLanguage | `ja` / `en` | yes | 母語 |
| studyPurpose | string[] | yes | 学習目的 |
| targetLevel | `N2` | yes | v1では固定 |
| selfLevel | string | yes | 自己申告レベル |
| examDate | ISO date | yes | 試験予定日 |
| studyDaysPerWeek | number | yes | 週の学習日数 |
| dailyStudyMinutes | number | yes | 1日の学習時間 |
| weakAreas | string[] | yes | 苦手分野 |
| studyStyle | string | no | 学習スタイル |
| notificationPreference | boolean | no | 通知希望 |

Zod では `targetLevel` を `N2` 固定、`dailyStudyMinutes` を 5〜120、`studyDaysPerWeek` を 1〜7 で検証する。

## API/Firebase 要件

初回リリースはローカル保存。後続同期先は Firestore `users/{userId}/profile`。React Query key は `["profile", guestId]`。

## コンテンツ要件

問題コンテンツは扱わない。

## エッジケース

- 未ログイン: ゲストIDで保存する。
- データ未作成: デフォルト値は保存するが、選択済み表示にはしない。
- 通信失敗: ローカル保存で進む。
- 途中離脱: 最後の回答済み質問から再開する。
- 重複送信: 保存中はボタンを無効化する。
- 端末変更: 初回リリースでは引き継がない。

## 実装対象外

- N2以外の目標選択。
- 多言語UIの本格対応。
- 学校クラス設定。

## 受け入れ条件

- [ ] 固定ヘッダーと固定フッターで進行できる。
- [ ] 初期値が選択済みの見た目にならない。
- [ ] 完了後に10問診断へ進む。

## 確認すべき質問

- 未定。
