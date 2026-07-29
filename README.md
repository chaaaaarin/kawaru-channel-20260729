# Google Workspace Studio紹介

📊 [スライド資料はこちら（slides.html）](https://chaaaaarin.github.io/kawaru-channel-20260729/slides.html) | 📋 [1枚まとめ資料はこちら（onepager.html）](https://chaaaaarin.github.io/kawaru-channel-20260729/onepager.html) | 🎁 [プレゼントキット（3点セット）](https://chaaaaarin.github.io/kawaru-channel-20260729/present.html)

Googleは2025年12月3日、Gmail・Drive・Chatなど**Workspaceの単純作業をGeminiに自動でつながせるノーコード機能「Google Workspace Studio」**を正式リリースした。✅ 旧称は「Google Workspace Flows」。2026年5月7日には日本語UIに対応し、2026年6月2日にはリスト・スプレッドシートを1件ずつ自動処理する「ループ処理」も追加された。✅ 本ノートは公式ドキュメント・実機レビュー・アナリスト分析を、確度表記つきで日本語に整理する。

**この資料の読み方**: 確度は文中に ✅(公式ドキュメント・公式ブログで直接確認済み)／🔶(一次情報あり・実機レビューや解説動画)／⚠️(未確認・本資料側の解釈)で表記する。本文では「Starter(スターター)」「Step(ステップ)」「Variable(変数)」という機能構造を、理解しやすいように**街の回転寿司屋**にたとえて説明する。

**🎁 この動画にはプレゼントキットがあります。** ①業務シーン別フロー設計図100選(トリガー・処理・変数を分解した設計図＋自然言語プロンプト)②導入前セキュリティ&権限チェックリスト③できること・できなくなったこと早見表、の3点セット。受け取り方は[キットの中身と受け取り方](#kit)章、キット本体は[`./present.html`](https://chaaaaarin.github.io/kawaru-channel-20260729/present.html)から。

## 目次

1. [Workspace Studioとは](#1-workspace-studioとは)
2. [得の数字と実例](#2-得の数字と実例)
3. [反論の先回り](#3-反論の先回り)
4. [なぜ今か:日本語対応とループ機能](#4-なぜ今か日本語対応とループ機能)
5. [仕組み:回転寿司でわかる3要素](#5-仕組み回転寿司でわかる3要素)
6. [セキュリティの安心感](#6-セキュリティの安心感)
7. [実践例](#7-実践例)
8. [料金・上限](#8-料金上限)
9. [公式サイトの謳い文句と実態のズレ](#9-公式サイトの謳い文句と実態のズレ)
10. [FAQ](#10-faq)
11. [今日からやること(始めるならこの順番)](#11-今日からやること始めるならこの順番)
12. [キットの中身と受け取り方](#kit)
13. [まとめ](#13-まとめ)

---

## 1. Workspace Studioとは

Google Workspace Studioは、**Google純正のノーコードAIエージェント作成ツール**。Gemini 3の推論力を使い、「メールに質問が含まれていたらChatで通知して」のような自然言語の指示から、実際に動く「フロー」を自動生成する。✅

もとは2025年4月のGoogle Cloud Next '25で「Google Workspace Flows」としてアルファ発表され、2025年12月3日に「Workspace Studio」へ改称のうえ一般提供が開始された。✅ 全ドメインへの展開は2026年3月19日に完了。✅

対象プランはBusiness(Starter/Standard/Plus)、Enterprise(Starter/Standard/Plus)、Education(Fundamentals/Standard/Plus等)で、対応エディションなら追加料金なしで使える。✅ **個人の無料Gmailアカウントでは利用できない**(独自ドメインのWorkspace有料契約が必要)。✅

出典(公式): [Introducing Google Workspace Studio](https://workspace.google.com/blog/product-announcements/introducing-google-workspace-studio-agents-for-everyday-work) ／ [Workspace Studio 製品ページ](https://workspace.google.com/studio/)

## 2. 得の数字と実例

Gemini Alphaプログラムの顧客は、正式リリース前の**過去30日間で2,000万件超のタスク**をWorkspace Studioのエージェントで処理した。✅ 清掃機器メーカーKärcher社は、新機能アイデアの評価に複数のエージェントを連鎖実行する仕組みを導入し、数時間かかっていたレビュー作業を**約2分**に短縮した。✅

出典(公式): [公式ブログ「Introducing Google Workspace Studio」](https://workspace.google.com/blog/product-announcements/introducing-google-workspace-studio-agents-for-everyday-work)

日本語で発信するこうすけ先生(Google塾)は、Workspace Studio単体をスプレッドシート・AppSheetと組み合わせ、**名刺管理システムを無料構築**した実演を公開している。フォルダに名刺画像を置く→Geminiが企業名・氏名・連絡先を抽出→スプレッドシートに自動登録、という仕組みで、市販の名刺管理ソフトと比べ共有機能等は劣るものの、無料でここまで作れるという可能性を示す一例と言える。🔶(二次情報)

⚠️ 「月間アクティブ350万人・単月1.7億タスク」という数字が一部の海外記事に見られるが、Google公式のNext'26キーノートブログでは確認できなかった。本資料では不使用とする。

## 3. 反論の先回り

**「Zapierやmakeでよくない?」**——Workspace内で完結する自動化(Gmail・Drive・Chat間の連携)ならWorkspace Studioが素直な選択肢になる。日本語UIかつ追加料金なしで使えるためだ。✅ 一方、外部システム(Webhook/CRM/決済等)からの起動や、他ツールとの深い連携が主役になる場面は、現状Zapier等の専門ツールが向く。🔶

**「結局エンジニアじゃないと無理では?」**——調査会社Forrester副社長のJ.P. Gownder氏は「エージェント作成は大多数の従業員には技術的に難しすぎる」と指摘する。🔶 同氏が引く2024年の調査では、プロンプトエンジニアリングを理解している人はわずか26%、従業員の58%が職場でのAI利用について正式な訓練を受けていないという。🔶 ただし同氏は同時に「Workspaceへのエージェント統合は賢明な設計」とも評価しており、テンプレートから始めれば自然言語での試行錯誤は最小限にできる(本資料側の補足)。

## 4. なぜ今か:日本語対応とループ機能

| | Before(〜2026年5月6日) | After(2026年5月7日〜/6月2日〜) |
|---|---|---|
| UI言語 | 英語のみ | 日本語含む8言語(英仏独伊韓葡西+日) |
| 繰り返し処理 | 手動で同じステップを複製 | 「Repeat for each」でリスト・表の最大100行を自動処理 |
| 心理的ハードル | Chrome翻訳頼み | 公式日本語対応で低い |

✅([Workspace Updates公式「Google Workspace Studio available in more languages」](https://workspaceupdates.googleblog.com/2026/05/google-workspace-studio-available-in-more-languages.html) ／ [ループ機能公式告知](https://workspaceupdates.googleblog.com/2026/06/introducing-ability-to-loop-over-list-of-items-in-Workspace-Studio.html))

日本語対応前は「日本語プロンプトが不安定」という報告も一部あったが🔶、対応後の実機レビューではその指摘は見られない。⚠️

**ここが今回最大のアップデート**: 世に出回る「Workspace Studioはループ処理ができない」という指摘(競合ベンダー記事や複数のまとめ記事)は、**2026年6月2日以降は不正確**。Geminiが生成したリストや、スプレッドシートの行(最大100件)を1件ずつ自動処理できる「Repeat for each」ステップが追加されている。✅ 会議メモのアクションアイテムを1件ずつタスク化する、営業リード表の行ごとにメール下書きを作成する、といった使い方が公式デモで示されている。✅

## 5. 仕組み:回転寿司でわかる3要素

Workspace Studioの「フロー」は、**Starter(スターター)・Step(ステップ)・Variable(変数)**の3要素で構成される。✅ これは街の**回転寿司屋**の仕組みに近い。

| 回転寿司でいうと | 公式の呼び方 | 役割 | たとえるなら |
|---|---|---|---|
| タッチパネルで注文する | Starter | 開始条件。「メールを受信したら」「毎週金曜17時」など | 「これが欲しい」を伝えるだけ |
| 大将が握る | Step | 実行アクション。「返信下書き」「Chat通知」「Geminiで判定」など(1フロー最大20ステップ) | 1皿=1ステップ、最大20皿まで |
| 皿につく伝票 | Variable | 前のステップの結果を次のステップに渡す動的プレースホルダー | 前の工程の結果を次に運ぶ |

作り方は3通り: ①自然言語でGeminiに説明して自動生成 ②Discoverページのテンプレートから選ぶ ③「+」から手動でスターター・ステップを組み立てる。✅

出典(公式): [公式ヘルプ Get started](https://support.google.com/workspace-studio/answer/16444479)

## 6. セキュリティの安心感

日本語で解説する複数のチャンネルが指摘するポイント: トリガーで動くGeminiは、Google Workspaceの**エンタープライズセキュリティの中で動くため学習対象にならない**。🔶 対して、GAS(Google Apps Script)+無償APIで自作するトリガー連携は、学習対象になりやすいと指摘されている。🔶

機密情報を扱うフローほど、この違いは実務上の判断材料になる(Claudeの補足・確度マークなし)。実践では、Geminiの返り値をJSONスキーマで受け、抽出ステップで値を取り出してから条件分岐させると扱いやすい、という実務者のテクニックも紹介されている。🔶

## 7. 実践例

- **問い合わせ自動対応**: Googleフォームに回答が来たら、Geminiが内容を要約・種類判定し、対応案を提案してChatに通知する。🔶
- **メール返信案のJSON分岐**: メール受信時にGeminiへ「返信要否・要約・返信案」をJSON形式で出力させ、抽出ステップで値を取り出し、返信が必要な時だけChat通知する条件分岐が組める。🔶
- **名刺管理システム**: 2章で紹介した実演例。フォルダ監視→Gemini抽出→スプレッドシート登録、という一連の流れをノーコードで構築。🔶

## 8. 料金・上限

公式ヘルプが明記する数値上限。✅

- 作成できるフロー数: 最大**25個**
- 1フローあたりのステップ数: 最大**20**
- Gmailイベントで起動できるアクティブなフロー: 最大**25個**
- 1日あたりの実行回数にも上限あり(24時間でリセット。具体的な数字は非公開)

出典(公式): [公式ヘルプ Learn about Google Workspace Studio limits](https://support.google.com/workspace-studio/answer/16765942)

| プラン | 月額(税別・1ユーザー) |
|---|---|
| Business Starter | 800円 |
| Business Standard | 1,600円 |
| Business Plus | 2,500円 |

✅ 対応エディションなら追加料金なしで利用可能。[出典(公式)](https://workspace.google.com/intl/ja/pricing.html)

月間フロー実行回数は、公式のAIアドオン比較表で「プロモーションアクセス。上限の適用は2026年9月1日に開始」と明記されている。🔶 **動画公開時点であと約1ヶ月**という点が、今回の"今なぜ"のもう一つの軸になる。[出典(公式)](https://knowledge.workspace.google.com/admin/getting-started/editions/compare-google-ai-expansion-add-ons)

## 9. 公式サイトの謳い文句と実態のズレ

公式サイトの製品ページは、Asana・Jira・Mailchimp・Salesforce等の「事前構築コネクタ」との連携を謳っている。✅(公式ブログ記載)

一方、実測ベースの複数のレポートによれば、**2025年12月3日の正式リリースでWebhookステップとChatスペース投稿ステップが削除された**。🔶 2026年5月に一部復活したが、GASによるカスタムステップ作成はまだ復活していないとされる。🔶 日本語で発信するこうすけ先生も、2026年6月5日時点で「外部連携・GAS連携は現状すべて消えている」と証言している。🔶

⚠️ 本資料側の注意喚起: 公式サイトのマーケティング表示と、複数の実測レポートに食い違いがある。導入前に自社環境で実際に使えるか確認することを推奨する。

専門家の懸念として、Forrester副社長J.P. Gownder氏は「エージェント統制(ガバナンス)」がIT部門の頭痛の種になりうるとも指摘している。🔶(3章参照)

## 10. FAQ

**Q. 個人のGmailアカウントでも使えますか?**
A. いいえ。独自ドメインのWorkspace有料契約が必要です。✅

**Q. 追加料金はかかりますか?**
A. 対応プラン(Business Starter以上等)なら追加料金なしで使えます。✅

**Q. プログラミングの知識は必要ですか?**
A. 基本は不要です。ただしJSON出力+条件分岐など一歩進んだ使い方には多少のコツがいります。

## 11. 今日からやること(始めるならこの順番)

1. 会社のWorkspaceプランを確認する(Business Starter以上等、管理コンソールでWorkspace Studioがオンになっているか)
2. Discoverページでテンプレートを1つ試す
3. 慣れたら自然言語で自分のフローを1つ作る
4. スプレッドシートの行が多い作業は「Repeat for each」を試す

<a id="kit"></a>
## 12. キットの中身と受け取り方

| # | キット名 | 種類 | 中身 | 受け取り方 |
|---|---|---|---|---|
| 1 | 業務シーン別フロー設計図100選 | インパクト型(100個) | トリガー・処理・変数を分解した設計図＋自然言語プロンプト。10カテゴリ×各10本 | [`kit-flow-designs100.html`](https://chaaaaarin.github.io/kawaru-channel-20260729/kit-flow-designs100.html)(個別・全件DL) ／ [`kit/flow-designs100.md`](./kit/flow-designs100.md) |
| 2 | 導入前セキュリティ&権限チェックリスト | 補助型 | 利用条件・情報ソース設定・出力安定化・上限把握・外部連携確認の5ステップ | [`present.html`](https://chaaaaarin.github.io/kawaru-channel-20260729/present.html)に直置き ／ [`kit/security-checklist.md`](./kit/security-checklist.md) |
| 3 | できること・できなくなったこと早見表 | 補助型 | 公式の上限／消えた機能／2026年の新機能／これから変わることの4カテゴリ | [`present.html`](https://chaaaaarin.github.io/kawaru-channel-20260729/present.html)に直置き ／ [`kit/capability-cheatsheet.md`](./kit/capability-cheatsheet.md) |

受け取り方は、[`./present.html`](https://chaaaaarin.github.io/kawaru-channel-20260729/present.html)のハブページから各キットへ。コピーボタンでのコピペと、ファイルダウンロードの両方に対応している。

## 13. まとめ

Workspace Studioは、Google純正・追加料金なし・日本語対応済みのノーコードAIエージェントツールとして、確実に使いやすくなっている。2026年5月の日本語UI対応、6月のループ処理追加という2つのアップデートで、「日本語が不安・繰り返し処理ができない」という以前の弱点は着実に減っている。✅

一方で、外部連携やGAS連携の実態は公式サイトの説明とズレがあり、大規模なバッチ処理にはまだ工夫が要る。🔶 まずは無料の範囲でテンプレートを1つ試してみるのが、一番リスクの低い始め方だ。

🎁 業務シーン別フロー設計図100選など、3つのプレゼントを用意した。詳しくは[12章](#kit)、または[`./present.html`](https://chaaaaarin.github.io/kawaru-channel-20260729/present.html)から。

---

本資料は非公式のまとめです。仕様・料金は変わることがあるため、最終確認は必ず公式サイトで行ってください。
