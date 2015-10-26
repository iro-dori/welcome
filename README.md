![](https://www.iro-d-ori.co.jp/img/og.png)

# irodori How-To-Work

この資料はirodoriでの仕事に対する考え方や作業方法をまとめています。


## 僕達が大事にしているもの

### ■ パフォーマンス
契約形態がどうであれ、自分が **一番パフォーマンスを出せるための環境** を自分で見つける/作ることを心がけてください。

必要な書籍/機材等、会社でサポートできるものについては可能な限り揃えます。

### ■ セルフジャッジ
自分で判断すべきものは自分で判断してください。

上記パフォーマンスに関する働き方やプロジェクトの進捗に対する各種判断等、あなたがジャッジして下さい。

ジャッジをするための相談やサポートが必要な場合も遠慮なく言ってください。

### ■ 結果
ソフトウェア/サービス開発には様々な不確定要素が存在しますが、 **最終的なアウトプット** しかクライアント/ユーザーは見ません。

そこに至るまでの工程や手法は各人が担当している役割等に応じて変わってくると思いますが、仕事の評価はそこに帰結されるのは必然です。

### ■ 責任
セルフジャッジをする以上、対象プロジェクトに対する責任はあなたの手に委ねられます。

おっと、そうは言っても恐れることはありません。最終的には経営陣が責任を取ります。

とにかくあなたは **クリエイターとしての能力** を発揮することに集中してください。


## 働き方について

### リモートワークの場合
朝礼に出席せず、朝からオフィス外で作業する場合には **当日の8:00** までにその旨をSlackで共有してください。


## 開発の進め方について

### ■ 開発マシン
社員は付与されたPCを利用しますが、外部パートナーの方は各自のノートPCでも構いません。

### ■ 開発言語
原則的に初期リリースまでにかかる工数が少ないRuby on Railsを利用します。

受託開発案件の場合はクライアントと協議することになりますが、Ruby on Railsを利用しない案件はほぼありません。

#### ◆ バックエンド
Ruby on Railsをそのまま利用しますが、APIのみ提供するプロジェクトの場合にはgrapeと組み合わせて利用することもあります。

#### ◆ JavaScript
![](http://justdevign.com.au/wp-content/uploads/2014/08/CoffeeScript_Logo_128.png)

JavaScriptを直接記述するのは極力避け、CoffeeScriptで記述します。

#### ◆ テンプレートエンジン
![](http://haml.info/images/haml.png)

[Haml](http://haml.info/)を利用します。

#### ◆ スタイリング
![](https://dynamicimagesfr-v2b.netdna-ssl.com/product_class_external_product/sass.png)

SASS（SCSS）で記述します。

CSSのフレームワークとしては[Bootstrap 3](http://getbootstrap.com/)や[Foundation](http://foundation.zurb.com/)を利用します。

![](http://www.w3schools.com/bootstrap/bs.png) ![](http://31.media.tumblr.com/avatar_3865d3a8accc_128.png)


### ■ ソースコードの管理について

![](http://kykamath.github.io/images/github.png)

[GitHub](https://github.com/)を利用します。

実装を行わない方もissueの登録等でレポジトリを閲覧できる必要がありますので、アカウントを持っていない場合は作成してください。

また、セキュリティレベル向上のためアカウント作成後に[二段階認証](https://help.github.com/articles/about-two-factor-authentication/)を有効にしてください。


### ■ プロジェクトの進捗管理

GitHubのIssue機能を利用して行います。

マイルストーンを週単位で作成した上で、その週に行う予定のissueを登録してください。

#### マイルストーンの命名規約

```ruby
"v#{Date.today.beginning_of_week.strftime('%Y%m%d')}-#{Date.today.end_of_week.strftime('%Y%m%d')}"
# 例). v20151026-20151101
```

また、マイルストーンの期日を必ずそのマイルストーンの終了日に指定してください。

#### ◆ issue登録時に設定する項目

##### 件名（Title）
長すぎず、完結に。
```
例). XXXにパスワードリマインダの機能を実装する
```
##### 本文（Comment）
issueを見た人間が開発に取り組めるように、情報が多すぎる位でも問題ありません。

4W1H（What / Why / Where / When / How）を明確にするように記述すると対象機能に関する簡単な議事録としても残せるのでオススメです。

```
例).
## 何を作るのか？
パスワードリマインダーです。

## 何故作るのか？
パスワードを忘れたユーザーにパスワードを再発行するフローを作りたいから。

## どこに作るのか？
同一サービス上の、ログインフォームの下にリンクをつけて誘導する。

## どうやって作るのか？
deviseの機能を使って実装します。

## 作成/変更するテーブル定義
usersテーブルにtemporary_key（string, null: false）を追加

## 参考リンク/資料
- [Google](https://www.google.com)
- [フォームデザイン.pdf](xxx)
```
##### ラベル（Labels）
ラベルについては特に制約は設けません。

```
例). カンバン方式を採用している場合

- 「TODO」
- 「DOING」
- 「DONE」

のラベルを作成して管理する。
```
##### マイルストーン（Milestones）
やることが決まっているものは必ずいつ取り組むのか分かるようにマイルストーンを設定すること。

実装時期が未定だったり、実装自体するか検討中のissueについては「Backlog」マイルストーンを設定してください（なければ作成してください）。

![](https://raw.githubusercontent.com/iro-dori/welcome/master/images/milestones.png)

##### 担当者（Assignee）
担当者が決まっている場合は指定すること。

### ■ 作業開始から終了まで

基本的にgit-flowの流れに則った形で作業を進めていきます。

- issueに作業内容を登録
- 作業用ブランチ作成
- 実装作業
- GitHubへ作業用ブランチをpush
- プルリクエストの作成
- 実装者以外のレビュー
- （レビューで修正の指定がある場合は修正後、再度レビューを依頼）
- 本ブランチ（主にmaster）へのマージ

#### ◆ 利用するブランチ
初期開発完了（受託開発であれば納品まで。サービスであれば初期ローンチまで）はmasterブランチをmerge先のブランチとします。

issueの対応を行う際にはgit-flowに則り「features/your-task」のような形で新しくmasterからブランチを作成して作業を開始してください。

1つのブランチで複数のissueを対応しても問題ありませんが、多く詰め過ぎるとmergeが面倒になるので最大3つのissueを目処にしてください。

![](http://joefleming.net/images/posts/git-flow-timeline.png)

#### ◆ ローカルでのmergeについて
作業用ブランチにmasterをmergeするタイミングなど、ローカルでmerge作業を行う際には必ず「--no-ff」を指定してください。

```shell
# masterブランチを自分の作業用ブランチにmergeする場合
git merge master --no-ff
```

#### ◆ プルリクエストの作成
作業用ブランチでの作業が完了したら、masterブランチに対してプルリクエストを作成してください。その上でSlack上のプロジェクト用チャネルで

```
@reviewer pull-request-url

レビューお願いします。
```

のような形でSlack上で声をかけてください。

（複数のプロジェクトが同時に進行しているため、GitHub上の作業が流れてしまうのを防ぐためです）

![](https://raw.githubusercontent.com/iro-dori/welcome/master/images/pr-slack.png)

#### ◆ issueの完了
gitでcommit時のメッセージとして「fixed #000」と入れておいてください。

こうしておくことで、masterにmergeされた時点でissueが自動的にcloseされます。

自動的にissueをcloseしたくない場合には、「#000」とだけ書いておけばissueに関連づけられます。

![](https://raw.githubusercontent.com/iro-dori/welcome/master/images/issue-log.png)


### ■ テストコードについて
Railsのプロジェクトであればrspecを利用します。ほとんどのプロジェクトでは原則モデルのunitテストだけで十分です。

継続して案件が進む場合には必要に応じて追加します。また、以下のものについてはリリース前までに書いておいたほうが幸せになれることが多いです。

- 決済機能
- API
