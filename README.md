![](https://www.iro-d-ori.co.jp/img/og.png)

# irodori How-To-Work

この資料はirodoriでの仕事に対する考え方や作業方法をまとめています。


## 僕達が大事にしているもの

### パフォーマンス
契約形態がどうであれ、自分が **一番パフォーマンスを出せるための環境** を自分で見つける/作ることを心がけてください。

必要な書籍/機材等、会社でサポートできるものについては可能な限り揃えます。

### セルフジャッジ
自分で判断すべきものは自分で判断してください。

上記パフォーマンスに関する働き方やプロジェクトの進捗に対する各種判断等、あなたがジャッジして下さい。

ジャッジをするための相談やサポートが必要な場合も遠慮なく言ってください。

### 結果
ソフトウェア/サービス開発には様々な不確定要素が存在しますが、 **最終的なアウトプット** しかクライアント/ユーザーは見ません。

そこに至るまでの工程や手法は各人が担当している役割等に応じて変わってくると思いますが、仕事の評価はそこに帰結されるのは必然です。

### 責任
セルフジャッジをする以上、対象プロジェクトに対する責任はあなたの手に委ねられます。

おっと、そうは言っても恐れることはありません。最終的には経営陣が責任を取ります。

とにかくあなたは **クリエイターとしての能力** を発揮することに集中してください。


## 開発の進め方について

### ソースコードの管理について

![](https://github.com/iro-dori/welcome/blob/master/images/GitHub_Logo.png)

[GitHub](https://github.com/)を利用します。

実装を行わない方もissueの登録等でレポジトリを閲覧できる必要がありますので、アカウントを持っていない場合は作成してください。

また、セキュリティレベル向上のためアカウント作成後に二段階認証を有効にしてください。


### 進捗管理

GithubのIssue機能を利用して行います。

マイルストーンを週単位で作成した上で、その週に行う予定のissueを登録してください。

#### マイルストーンの命名規約

```ruby
    "v#{Date.today.beginning_of_week.strftime('%Y%m%d')}-#{Date.today.end_of_week.strftime('%Y%m%d')}" # 例). v20151026-20151101
```

また、マイルストーンの期日を必ずそのマイルストーンの終了日に指定してください。

#### issue登録時に設定する項目

##### [件名]
長すぎず、完結に。
##### [本文]
issueを見た人間が開発に取り組めるように、情報が多すぎる位でも問題ありません。
##### [担当者]
担当者が決まっている場合は指定すること。
##### [マイルストーン]
やることが決まっているものは必ずいつ取り組むのか分かるようにマイルストーンを設定すること。

やるか未定のものについてはBacklogを設定してください。

### 作業開始から終了まで

基本的に以下の流れを繰り返す形で作業を進めていきます。

- issueに作業内容を登録
- 作業用ブランチ作成
- Githubへの作業用ブランチpush
- プルリクエストの作成
- 本ブランチ（主にmaster）へのマージ

#### 利用するブランチ
開発時（一次納品まで）はmasterブランチをmerge先のブランチとします。

issueの対応を行う際にはGit-flowに則り「features/your-task」のような形で新しくmasterからブランチを作成して作業を開始してください。

1つのブランチで複数のissueを対応しても問題ありませんが、多く詰め過ぎるとmergeが面倒になるので最大3つのissueを目処にしてください。

#### プルリクエストの発行
作業用ブランチでの作業が完了したら、masterブランチに対してプルリクエストを作成してください。その上でslack上のプロジェクト用チャネルで

```
@reviewer pull-request-url

レビューお願いします。
```

のような形でslack上で声をかけてください。

（複数のプロジェクトが同時に進行しているため、Github上の作業が流れてしまうのを防ぐためです）

#### issueの完了
gitでcommit時のメッセージとして「fixed #000」と入れておいてください。

こうしておくことで、masterにmergeされた時点でissueが自動的にcloseされます。


### テストコードについて
Railsのプロジェクトであればrspecを利用します。ほとんどのプロジェクトでは原則モデルのunitテストだけで十分です。

継続して案件が進む場合には必要に応じて追加します。また、以下のものについてはリリース前までに書いて頂くことが多いです。

- 決済機能
- API


### リモートワークの場合
朝礼に出席せず、朝からオフィス外で作業する場合には **当日の8:00** までにその旨をslackなりで共有してください。
