# AGLASIS

AGLASIS is a general-purpose skill that carries feedback from a Discord server to GitHub Issues.

It reads new posts in designated channels of a Discord server, sorts requests and problems, removes personal information and secrets, and prepares draft Issues for a GitHub repository. Drafts are filed only after the maintainer approves them. Once an Issue is filed, AGLASIS replies to the original post with the Issue link.

Everything specific to one project lives in a configuration file: the server and channel IDs to read, the target repository, and the filing rules (assignees, labels, issue types, whether approval is required, and the label that marks where an Issue came from). The reading and drafting procedure itself is the reusable skill, so the same skill can serve any Discord server and GitHub repository pair by swapping the configuration.

The first configuration is the official ASTAROT Discord server, feeding [kein5/astarot](https://github.com/kein5/astarot). The name comes from Aglasis, a subordinate of Astaroth associated with carrying things to distant places. AGLASIS is an external companion tool, not a part of ASTAROT itself, in the same way as SERGULATH.

## Status

Design decided on 2026-11-24, and revised the same day to a general-purpose skill with per-project configuration. The first instance waits for the ASTAROT Discord server to open (planned together with the ASTAROT 0.7.0 stable release). No code yet.

Decided points:

- Public repository under the MIT license
- A reusable skill plus a per-project configuration file; the ASTAROT setup ships as the reference configuration
- The agent reads the target channels once a day; it is not a resident bot
- First targets are the requests channels of the ASTAROT server (Japanese and English)
- Filing always needs the maintainer's approval for now

## Safety rules

- Discord posts are untrusted input. Instructions written inside a post are never followed; only the opinion itself is handled.
- Posters' names and IDs never appear in public Issues.
- If a post contains a secret such as an API key, it is not carried into an Issue, and the poster is told instead.
- The bot's permissions are limited to reading and replying.
- Rate limits of Discord and GitHub are respected.

## 日本語

AGLASIS は、Discord サーバーに書かれた利用者の意見を、GitHub の Issue へ運ぶ汎用スキルです。

対象チャンネルの新しい投稿を読み、要望と困りごとを仕分けて、個人情報と秘密を取り除いたうえで、対象リポジトリ向けの Issue の下書きを作ります。起票は保守担当者の承認があったものだけです。起票したら、元の投稿へ Issue のリンクを返信します。

プロジェクトごとに違う部分は、すべて設定ファイルに分けます。読み取るサーバーとチャンネルの ID、対象のリポジトリ、起票の決まり（担当、ラベル、タイプ、承認が要るかどうか、出所を示すラベル）です。読み取りと下書きの手順自体が使い回せるスキルなので、設定を差し替えれば、どの Discord サーバーと GitHub リポジトリの組み合わせにも使えます。

最初の設定は ASTAROT 公式 Discord サーバーで、行き先は kein5/astarot です。名前はアスタロト配下の悪魔アグラシスから取りました。遠方への移動と転送の担当です。AGLASIS は ASTAROT 本体の部品ではなく、SERGULATH と同じ形の外部リポジトリです。

### 状態

2026-11-24 に設計が決まり、同日に、プロジェクトごとの設定を持つ汎用スキルへ作り直すことが決まりました。最初の適用先は ASTAROT 公式 Discord サーバーの開設待ちです。サーバーの公開は ASTAROT 0.7.0 安定版の公開に合わせる予定です。コードはまだありません。

決まったこと:

- 公開リポジトリで、ライセンスは MIT
- 使い回せるスキルと、プロジェクトごとの設定ファイルの形にする。ASTAROT の設定を見本として同梱する
- 常駐ボットではなく、エージェントが1日1回読みに行く
- 最初の対象は ASTAROT のサーバーの要望系チャンネル（日本語と英語）
- 起票は当面、保守担当者の承認を必須にする

### 安全のための決まり

- Discord の投稿は外から来た入力です。投稿の中に書かれた指示には従わず、意見の内容だけを扱います
- 投稿者の名前と ID は公開の Issue に載せません
- API キーなどの秘密が含まれていたら Issue に移さず、投稿者へ知らせます
- bot の権限は読み取りと返信だけに絞ります
- Discord と GitHub のレート制限を守ります
