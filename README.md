# 【Android問題集】<br>オンラインランキング機能を作ってみよう！<br>「連打ゲーム」

_2017/05/16作成 (2017/05/19修正)_

![RendaGame](/readme-img/RendaGame.png)

GitHub<br>
**https://goo.gl/zZY5RA**

<div style="page-break-before:always"></div>

## コンテンツ概要

* ニフティクラウドmobile backend の機能『データストア』を学習するための問題集です
 * ニフティクラウドmobile backend の利用登録（無料）が必要です。
* 問題用プロジェクトにはオンラインランキング機能が実装されていない状態の「連打ゲーム」です
 * 既に実装済みのニフティクラウドmobile backend を利用するための準備（SDK導入など）方法の詳細はこちらをご覧ください。<br>http://mb.cloud.nifty.com/doc/current/introduction/quickstart_android.html

## 問題について

* 問題は２問あります
* ２問クリアすると「連打ゲーム」にオンラインランキング機能を実装したアプリが完成します
* 問題を取り組む上で必要な開発環境は以下です
 * AndroidStudio ver.1.4 以上

 <div style="page-break-before:always"></div>

## 問題に取り組む前の準備
### プロジェクトのダウンロード

▼問題用プロジェクト▼<br>**https://github.com/natsumo/AndroidFirstApp/archive/Question.zip**

1. 上記リンクをクリックしてzipファイルをローカルに保存します
1. zipファイルを解凍して、AndroidStudioを開き,「Open an existing AndroidStudio project」を選択し、解凍したプロジェクトを開きます。
1. プロジェクトをビルドし、「連打ゲーム」で遊んでみましょう

#### 「連打ゲーム」の操作方法

1. 「START」ボタンをタップします
2. 「3」,「2」,「1」とカウントダウンし、「スタート！」からタイムアップ！の10秒間「◎」の部分がタップできるようになります
3. 10秒間に何回タップできるかを競う単純なゲームです
4. 10秒経つと名前を入力するアラートが表示されますので、入力し「OK」をタップします
5. 「SHOW RANKING」ボタンをタップすると、画面に名前とスコアが表示されます。

※ __注意__：問題に取り組む前の状態では「SHOW RANKING」ボタンをタップしてもランキングは表示されません

<div style="page-break-before:always"></div>

### アプリの新規作成とAPIキーの設定

![mBaaS](/readme-img/mBaaS.png)

*  ニフティクラウドmobile backend にログインしアプリの新規作成を行います
 * アプリ名はわかりやすいものにしましょう。例）「renda」
* アプリが作成されるとAPIキーが２種類（アプリケーションキーとクライアントキー）発行されます
 * 次で使用します。

![AndroidStudio](/readme-img/icon_androidstudio.png)

* `MainActivity.java`の`onCreate`を編集します
* 先程ニフティクラウドmobile backend のダッシュボード上で確認したAPIキーを、それぞれ`YOUR_APPLICATION_KEY`と`YOUR_CLIENT_KEY`に貼り付けます

 ![問題0-1](/readme-img/0-1.png)

* このとき、ダブルクォーテーション（`"`）を消さないように注意してください！

<div style="page-break-before:always"></div>

## 【問題１】<br>名前とスコアの保存をしてみよう！
`MainActivity.java`を開きます。下図の__`saveScore`__ メソッドを編集し、引数の__`name`__ （アラートで入力した名前）と__`score`__ （連打ゲームでタップした回数）の値をmBaaSに保存する処理をコーディングしてください

![問題1-1](/readme-img/1-1.png)

* データストアに保存先クラスを作成します
 * クラス名は「`GameScore`」としてください
* `name`を保存するフィールドを「`name`」、`score`を保存するフィールドを「`score`」として保存してください

### ヒント

* ニフティクラウドmobile backend のキュメントのドキュメントページをご活用ください<br>http://mb.cloud.nifty.com/doc/current/datastore/basic_usage_android.html

<div style="page-break-before:always"></div>

### コーディング後の作業
問題１のコーディングが完了したら、下記の作業を行います

#### 【作業1-1】
それぞれ該当する箇所に以下の処理を追記して、実行時にAndroidStudio上にログを表示できるようにします

* 保存に失敗した場合の処理を行う箇所に追記

 ![code1](/readme-img/code1.png)

* 保存に成功した場合の処理を行う箇所に追記

 ![code2](/readme-img/code2.png)

#### 【作業1-2】
エミュレーターで実行、「START」ボタンを押してゲームを遊びます

* 名前を入力し、「OK」がタップされると【問題１】で作成した`saveScore`メソッドが呼ばれ、データが保存されます
* このとき下記のいずれかのログが出力されます
 * 保存成功時：「`保存に成功しました。`」
 * 保存失敗時：「`保存に失敗しました。エラー :******`」

※ エラーコードが出た場合はこちらで確認できます<br>http://mb.cloud.nifty.com/doc/current/rest/common/error.html#REST_APIのエラーコードについて

<div style="page-break-before:always"></div>

### 【問題１】答え合わせ

#### ニフティクラウドmobile backend上での確認
![mBaaS](/readme-img/mBaaS.png)

* 保存されたデータを確認しましょう
 * 「データストア」をクリックすると、「`GameScore`」クラスにデータが登録されていることが確認できます。

 ![ans1-1](/readme-img/ans1-1.png)

* 上図はスコアが35連打で名前を「あいうえお」とした場合の例です。

<div style="page-break-before:always"></div>

#### コードの答え合わせ

![Android](/readme-img/icon_androidstudio.png)

* 模範解答は以下です

 ![Answer1](/readme-img/Answer1.png)

<div style="page-break-before:always"></div>

## 【問題２】<br>ランキングを表示しよう！
`RankingActivity.java`を開きます。下図の`checkRanking`メソッドを編集し、データストアの`GameScore`クラスに保存した`name`と`score`のデータを`score`の降順（スコアの高い順）で検索・取得する処理をコーディングしてください

![問題2-1](/readme-img/2-1.png)

* 検索データ件数は５件とします

### ヒント

* ニフティクラウドmobile backend のキュメントのドキュメントページをご活用ください<br>http://mb.cloud.nifty.com/doc/current/datastore/basic_usage_android.html<br>http://mb.cloud.nifty.com/doc/current/datastore/ranking_android.html

<div style="page-break-before:always"></div>

### コーディング後の作業
問題２のコーディングが完了したら、下記の作業を行います

#### 【作業2-1】
該当する箇所に以下の処理を追記して、実行時にAndroidStudio上にログを表示できるようにします

* 検索に失敗した場合の処理を行う箇所に追記

 ![code3](/readme-img/code3.png)


* 検索に成功した場合の処理を行う箇所に追記

 ![code4](/readme-img/code4.png)


#### 【作業2-2】
エミュレーターで実行し、「SHOW RANKING」ボタンをタップします

* 画面起動後、`checkRanking`メソッドが呼ばれ、【問題１】で保存されたデータが検索・取得されます
* このとき下記のいずれかのログが出力されます
 * 検索成功時：「`検索に成功しました。`」
 * 検索失敗時：「`検索に失敗しました。エラーコード：******`」


※ エラーコードが出た場合はこちらで確認できます<br>http://mb.cloud.nifty.com/doc/current/rest/common/error.html#REST_APIのエラーコードについて

* 検索の状態（成功・失敗）に関係なく、「SHOW RANKING」ボタンをタップしても、まだランキングは表示されません

<div style="page-break-before:always"></div>

#### 【作業2-3】
検索に成功したら、該当する箇所に以下の処理を追記して、取得した値から必要なデータを取り出し、ランキング画面へ反映させます

* 検索に成功した場合の処理を行う箇所に追記

 ![code5](/readme-img/code5.png)


#### 【作業2-4】
エミュレーターで実行、「SHOW RANKING」ボタンを押します

* 先ほどのスコアが表示されれば完成です！おめでとうございます★

<div style="page-break-before:always"></div>

### 【問題２】答え合わせ
#### ランキング画面の確認

* ランキング画面を確認しましょう
 * アプリで「SHOW RANKING」をタップすると以下のようにランキングが表示されます

![ans2-1](/readme-img/ans2-1.png)

* 上図は３回遊んだ場合の例です。複数回遊んで、ランキングが表示されることを確認しましょう！

<div style="page-break-before:always"></div>

#### コードの答え合わせ

![Android](/readme-img/icon_androidstudio.png)

* 模範解答は以下です
 ![Answer2](readme-img/Answer2.png)

## 参考
* 問題の解答を実装した完全なプロジェクトをご用意しています

▼完成版プロジェクト▼<br>
**https://github.com/natsumo/AndroidFirstApp/archive/AnswerProject.zip**

* APIキーを設定してご利用ください
