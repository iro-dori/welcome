![](https://www.iro-d-ori.co.jp/img/og.png)

# irodori How-To-Work

この資料はイロドリ社での仕事に対する考え方や作業方法をまとめています。

## はじめに

こんにちは！devkato です。

あなたがこの資料を見ているということは、何らかの関係でイロドリ社の仕事に関わっているということですね？

まずはこれからよろしくお願いします！一緒によい仕事をしましょう！

## 僕達が大事にしているもの

### ■ パフォーマンス

関わり方はどうであれ、自分が **一番パフォーマンスを出せるための環境** を自分で見つける/作ることを心がけてください。

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

### ■ 作業開始報告について

作業開始/終了時に作業予定内容（issue や PR の URL）を Slack の #daily-report チャンネルに流しておくこと。

### ■ 平日に休暇を取る場合

自分の裁量で平日に休暇を取ることに対して特に制約/制限は設けません。

ただ、あなたがお休みでも一般的な日本の会社に勤務しているクライアントは働いていますし、クライアントが国外の場合には日本が祝日でも相手は平日であることもあります。

従って、自分の担当クライアントが働いている日に休暇を取る場合には必ず事前にその旨を共有しておいてください。

仕事は自社だけで完結している訳ではありません。必ずモニターの向こうにユーザー/クライアントがいます。そのことを忘れずに。

### ■ 日報について

Slack 上の `#daily-report` にて、作業内容（作業した issue や PR の URL）を報告してください。

## 開発の進め方について

### ■ 開発マシン

社員は付与された PC を利用しますが、外部パートナーの方は各自のノート PC でも構いません。

### ■ 開発言語

原則的に初期リリースまでにかかる工数が少ない Ruby on Rails を利用します。

受託開発案件の場合はクライアントと協議することになりますが、Ruby on Rails を利用しない案件はほぼありません。

#### ◆ バックエンド

Ruby on Rails（2018 年 3 月時点では 5.1.5）をそのまま利用しますが、API のみ提供するプロジェクトの場合には grape と組み合わせて利用することもあります。

コーディング規約については最近のレポジトリであれば Rubocop を利用してチェックを行っています。

#### ◆ JavaScript

![](https://static.amido.com/wp-content/uploads/2016/10/24155219/ES6.png)

Rails 5.1 以降で導入された webpacker を利用して、ES6 で記述します。

##### ▲ スタイルガイド

クラス名/関数名は CamelCase を基本とします。

```javascript
// Good
class HelloWorld {
  sayHello() {
    alert('hi!');
  }
}

// Bad
class hello_world {
  say_hello() {
    alert('hi!');
  }
}
```

#### ◆ テンプレートエンジン

![](http://haml.info/images/haml.png)

[Haml](http://haml.info/)を利用します。

##### ▲ スタイルガイド

'='の後には必ず半角 space を 1 つ入れてください。

```haml
-# Good
%p= @variable

-# Bad
%p=@variable
```

#### ◆ スタイリング

![](https://dynamicimagesfr-v2b.netdna-ssl.com/product_class_external_product/sass.png)

SASS（SCSS）で記述します。

CSS のフレームワークとしては[Bootstrap 3](http://getbootstrap.com/)や[Foundation](http://foundation.zurb.com/)を利用します。

![](http://www.w3schools.com/bootstrap/bs.png) ![](http://31.media.tumblr.com/avatar_3865d3a8accc_128.png)

Bootstrap は 3.x 系を利用してます（4.x 系は IE9 以下がサポート対象外のため、移行まで猶予期間を設けています）

##### ▲ スタイルガイド

[Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.xml)に準拠します。

### ■ ソースコードの管理について

![](http://kykamath.github.io/images/github.png)

[GitHub](https://github.com/)を利用します。

実装を行わない方も issue の登録等でレポジトリを閲覧できる必要がありますので、アカウントを持っていない場合は作成してください。

また、セキュリティレベル向上のためアカウント作成後に[二段階認証](https://help.github.com/articles/about-two-factor-authentication/)を有効にしてください。

### ■ プロジェクトの進捗管理

GitHub の Issue 機能を利用して行います。

マイルストーンを週単位で作成した上で、その週に行う予定の issue を登録していきます。

#### マイルストーンの命名規約

```ruby
[
  'v',
  Date.today.beginning_of_week.strftime('%Y%m%d'),
  '-',
  Date.today.end_of_week.strftime('%Y%m%d')
].join ''
# => 例). v20151026-20151101
```

基本的にはスクリプト経由で当週のマイルストーンが作成されていますが、作成されていない場合は上記命名規約に従って作成をお願いします。

#### ◆ issue 登録時に設定する項目

##### 件名（Title）

長すぎず、完結に。

```
例). XXXにパスワードリマインダの機能を実装する
```

##### 本文（Comment）

issue を見た人間が開発に取り組めるように、情報が多すぎる位でも問題ありません。
.github/ISSUE_TEMPLATE.md は以下の通りです。

```markdown
## WHAT - 何を作るのか？

例. コレをアレしたらソウなるようにする

## WHY - 何故作るのか？

例). KPI の新規作成

## HOW - どうやって作るのか？

例). KPI の新規作成

## 参考 URL

* [すごく参考になるページ](https://www.google.com)
* [ちょっと参考になるページ](https://www.yahoo.com)

## 参考資料

添付ファイルを参照（ある場合は）
```

##### ラベル（Labels）

ラベルについては特に制約は設けませんが、[Waffle](https://waffle.io)を利用して管理していることが多いです。

##### マイルストーン（Milestones）

やることが決まっているものは必ずいつ取り組むのか分かるようにマイルストーンを設定すること。

実装時期が未定だったり、実装自体するか検討中の issue については「Backlog」マイルストーンを設定してください（なければ作成してください）。

![](https://raw.githubusercontent.com/iro-dori/welcome/master/images/milestones.png)

##### 担当者（Assignee）

最近は指定しないことが多いです（その代わり、Reviewer を指定する）

##### レビュー者（Reviewer）

レビューして欲しい人間のアカウントを指定してください。

### ■ 作業開始から終了まで

基本的に git-flow の流れに則った形で作業を進めていきます。

参考 : [Understanding the GitHub Flow](https://guides.github.com/introduction/flow/)

* issue に作業内容を登録
* 作業用ブランチ作成
* 実装作業
* GitHub へ作業用ブランチを push
* プルリクエストの作成
* 実装者以外のレビュー
* （レビューで修正の指定がある場合は修正後、再度レビューを依頼）
* 本ブランチ（主に master）へのマージ

プロジェクトメンバーが増えてリリース phase を踏む形にシフトする際はタイミングをみて Git-Flow へ移行していきます。

#### ◆ 利用するブランチ

初期開発完了（受託開発であれば納品まで。サービスであれば初期ローンチまで）は master ブランチを merge 先のブランチとします。

issue の対応を行う際には GitHub-Flow に則り「features/your-task」のような形で新しく master からブランチを作成して作業を開始してください。

1 つのブランチで複数の issue を対応しても問題ありませんが、多く詰め過ぎると merge が面倒になるので最大 3 つの issue を目処にしてください。

![](http://joefleming.net/images/posts/git-flow-timeline.png)

#### ◆ ローカルでの merge について

作業用ブランチに master を merge するタイミングなど、ローカルで merge 作業を行う際には必ず「--no-ff」を指定してください。

```shell
# masterブランチを自分の作業用ブランチにmergeする場合
git merge master --no-ff
```

#### ◆ プルリクエストの作成

作業用ブランチでの作業が完了したら、master ブランチに対してプルリクエストを作成してください。その上で Slack 上のプロジェクト用チャネルで

```
@reviewer pull-request-url

レビューお願いします。
```

のような形で Slack 上で声をかけてください。

（複数のプロジェクトが同時に進行しているため、GitHub 上の作業が流れてしまうのを防ぐためです）

![](https://raw.githubusercontent.com/iro-dori/welcome/master/images/pr-slack.png)

プルリクエストもテンプレートを用意しています。

```markdown
## このプルリクエストは何なのか？

## どうやってテストすればいいのか？

## どうやって実装したのか？

## スクリーンショット

## 質問事項
```

参考 : [Pull request templates make code review easier](https://quickleft.com/blog/pull-request-templates-make-code-review-easier/)

#### ◆ issue の完了

git で commit 時のメッセージとして「fixed #000」と入れておいてください。

こうしておくことで、master に merge された時点で issue が自動的に close されます。

自動的に issue を close したくない場合には、「#000」とだけ書いておけば issue に関連づけられます。

![](https://raw.githubusercontent.com/iro-dori/welcome/master/images/issue-log.png)

### ■ テストコードについて

Rails のプロジェクトであれば rspec を利用します。ほとんどのプロジェクトでは原則モデルの unit テストだけで十分です。

継続して案件が進む場合には必要に応じて追加します。また、以下のものについてはリリース前までに書いておいたほうが幸せになれることが多いです。

* 決済機能
* API

### ■ コメントについて

クラス単位でのコメントは最小限に（そもそもクラス名を見てその役割が分からないのはおかしいので）とどめる形で構いません。

関数単位でのコメントは

* その関数が行っていること
* 引数の説明
* 戻り値の説明
* その他補足事項

を記述するようにしてください（以下の例を参照）。

```ruby
#
# イロドリの業務に関する処理を記述する
#
class IrodoriCorporation

  #
  # 社員に給料を支払う
  #
  # 何の変哲もないアクションです。
  #
  # @TODO 通貨が変わった場合はどうする？
  #
  # @param [User] user 給料を支払うユーザー
  # @param [Integer] price 支払い金額
  #
  # @return [Boolean] 支払い処理に成功したらtrue、失敗したらfalse
  #
  def paySalary(user, price)
    # ...
  end
end
```

### ■ ドキュメンテーションについて

設定や備考録等、対象プロジェクトに関するドキュメントは GitHub の Wiki にまとめてください。

無理やり 1 ページに納める必要はないので、Home ページからリンクを貼る形で機能/項目単位でページを作成して問題ありません。
