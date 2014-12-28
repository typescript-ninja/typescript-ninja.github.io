---
layout: post
title: TypeScript in Definitelyland 発行
---

## 公開しましたよ

どうも、[vvakame](https://twitter.com/vvakame)です。

去る12月30日、[コミックマーケット87](http://www.comiket.co.jp/)にてTypeScript in Definitelylandという冊子を[頒布](http://techbooster.github.io/c87/#typescript)しました。

頒布前から宣言していた通り、その[全文を公開](http://typescript.ninja/typescript-in-definitelyland/)します。
GitHubリポジトリは[こちら](https://github.com/typescript-ninja/typescript-in-definitelyland/)。
本書はTypeScriptリファレンス（[Amazon](http://www.amazon.co.jp/gp/product/484433588X?tag=damenako-22)、[達人出版会](http://tatsu-zine.com/books/typescript-reference)）の既読、未読に関わらず読めるようになっています。
本書ではJavaScriptの細かい仕様については解説していません。もし、JavaScript自体の仕様について、TypeScriptと共に学びたい場合はTypeScriptリファレンスの購入をお勧めします。
TypeScriptリファレンスはTypeScript 1.0対応の書籍です。
1.0から今までの差分は、[TypeScript 1.1.0 変更点](http://qiita.com/vvakame/items/5e53c392867ebc604267)と[TypeScript 1.3.0 変更点](http://qiita.com/vvakame/items/0b5060de5566f210479b)を参照してください。

## 本書を支える技術

折角なので、本書を支える技術について言及しておきます。
技術書をこれから執筆したい、興味がある、という人に役立つかもしれません。
なお、TechBoosterの中でプロジェクト構成改善ガチ勢は多分僕だけなので僕のプロジェクトが一番研究が進んでいると思います。

最近だと[Promise本](http://azu.github.io/promises-book/)や[Fuzoku実践入門 環境サンプルファイル](https://github.com/akinomurasame/learning-fuzoku-sample)あたりが技術的に頑張ってる技術書だと思うので、そちらと見比べてみても楽しいかもしれません。

### ツールの選定

* [Re:VIEW](https://github.com/kmuto/review)
  * 日本の出版業界を支えるプロが利用・メンテナンスしている
    * [kmuto](https://github.com/kmuto)さんは[トップスタジオ](http://www.topstudio.co.jp/)の人なので商業（紙を含む）に持ってきたい時相談しやすそう（たぶん）
    * [達人出版会](http://tatsu-zine.com/)の[takahashim](https://github.com/takahashim)さん
  * WordなどのGitHub上でdiffが取れなかったり手で変更をmergeできない書式を使うのは嫌だ
    * よーするにテキストファイルがいい
  * 和文組版についてのdomain specificな事情も考慮されている
    * エッジケースが色々なところにあって、何も考えずに小賢しいパッチを当てると後で「それにはこういう悲しい事情があってね…」という話を伺って涙腺が緩んだりする
  * 書籍固有の拡張を行うのが比較的容易
    * 競合に[Sphinx](http://sphinx-users.jp/)、[Pandoc](http://sky-y.github.io/site-pandoc-jp/users-guide/)、[asciidoc](http://www.methods.co.nz/asciidoc/)などがある。
      * asciidocは米O'Reillyが[atlas](https://atlas.oreilly.com/)という書籍執筆プラットフォームに採用
    * 拡張の容易さという意味では、Markupな言語が強い。Markdown類似のものは新規文法導入のコストが高い(記法から追加しないといけない)
    * 記述の容易さで張り合うには、テキストエディタによる気持ちのよいバックアップが必要
  * セットアップがダルいのが玉に瑕
    * Ruby処理系とlatex(PDF出力する場合)など。
    * [はじめのRe:VIEW](https://github.com/TechBooster/FirstStepReVIEW)あたりを参考にするとよい
    * latexで出したいわけじゃなくてPDFが得られればそれでいいので、[AH Formatter](http://www.antenna.co.jp/AHF/)（有料）または[vivliostyle](http://vivliostyle.co.jp/)さんのプロダクトに期待するのも手
  * [review.js](https://vvakame.github.io/review.js/)作ってるけどやりたい事が多すぎてリソースが回ってない状態…
* [GitHub](https://github.com/)
  * 言わずと知れた… これを使わないとかありえない
    * Issue管理とpull requestがあればまぁなんでも良い
    * [gh-pages](https://help.github.com/articles/creating-project-pages-manually/)が大変便利
  * gitが使えない人と組んではいけない（共著者、編集者、などなど）
    * 組む場合はパッと想像した負担の5倍の苦労(または諦め)を背負う覚悟が必要
    * GitHub自体については能力の高い技術者でも仕事環境や興味の方向次第ではびっくりするくらい慣れていない場合も結構あるので随時色々教えてあげよう
* [Atom](https://atom.io/)
  * JavaScriptで拡張可能なエディタ ということで使っている
  * Re:VIEWに限ればSublime Text 2と[yanzm製プラグイン](http://y-anz-m.blogspot.jp/2013/08/sublime-text-2-review.html)が一番いいと思う
  * [language-review](https://atom.io/packages/language-review)を作っているがこれまた時間が足りない
* [prh](https://github.com/vvakame/prh)
  * 今回の原稿後に作り始めたので実戦投入はまだ
  * 校正を簡単な単語の置き換えレベルで自動化する
    * [てくぶ用設定](https://github.com/vvakame/prh/blob/master/misc/techbooster.yml)
    * 誤検出を抑える代わりに検出漏れが発生しやすいかも
* [bundler](http://bundler.io/) [例](https://github.com/typescript-ninja/typescript-in-definitelyland/blob/master/Gemfile)
  * Re:VIEWのどのバージョンを使ってコンパイルするか表すため
  * 最新のリリースを使いたい場合やmaster/HEADが使いたい場合などがあるため
* [grunt](http://gruntjs.com/) [例](https://github.com/typescript-ninja/typescript-in-definitelyland/blob/dd6b0f18655397782e61ec1e8faff13844e83199/Gruntfile.js#L200)
  * 使い慣れているタスクランナーならなんでもよいと思う
  * わかめはRuby慣れてないのとTypeScriptバトラーなのでgrunt
    * gulpは使ったことない
  * pdf, epub, html の生成用タスクを準備しておく
  * 本書の場合、サンプルコードのビルドチェックと原稿への埋め込み（review-preproc）なども行う
* [Circle CI](https://circleci.com/)
  * CIサービスの中で最近一番流行ってる奴
  * Travis CIよりUIがこなれていて使いやすい
  * テスト実行時にインスタンスが割り当てられるのが早い
  * 本当を言うと、好きなDockerimageをベースにビルドできるCIサービスがあればそれを使いたい
    * [Re:VIEW用イメージ](https://registry.hub.docker.com/u/vvakame/review/)を作ってある(使ってないけど)
    * drone.ioを自分のサーバで運用すればそれが出来るんだけど自前サーバはめんどくさい
    * Circle CIはビルドフェーズを細かく管理している(のでわかりやすいUIが提供できる)ので、すぐにはbaseのDocker image指定対応とかは入らなさそうな気がする
* [griflet](https://tcb.mowa-net.jp/griflet/)
  * [amedama](https://twitter.com/amedama)さんがやってるRe:VIEW専用謎CIサービスっぽいもの
    * 本人による[スライド](http://www.slideshare.net/mowamowa3/201412-42460693)
  * 多分、誰でも使えるわけではないクローズドなサービス（まだ）
  * 本書のPDF, epub入手先はgrifletを使っています
  * GitHubへのpushを検知して自動ビルドしておいてくれます 良い子
* [mhidaka](https://twitter.com/mhidaka)
  * 非常にハイエンドかつ多機能なマネージメントが行なわれる
  * 自動で稼働するためこちらの要望を伝えておくだけでいい感じになる
  * 編集・構成、入稿、表紙の絵・デザインの依頼、コミケ当日の搬入の手配までやっておいてくれる
  * 非売品
* [muo_jp](https://twitter.com/muo_jp)
  * 高性能レビュワー
  * 非常に有用なアドバイスをくれる
  * 〆切なんてなんのその
  * 非売品

### ワークフロー

書籍執筆時のワークフローをまとめておきます。
書籍執筆自体についての手引は[こちら](http://qiita.com/vvakame/items/d657baf26cf83ac98bd0)。

#### 企画

* 本を書きたいなーという気持ちにする
* 対象読者をざっくり決める
* 目次をざっくり書く
  * 今回は深さ2で設計
  * これから書く予定の所はTODOとかTBDとか書いてしまい、目次が出力できるところまでさくさく作業する
* 目標ページ数をざっくり決め（られ）てしまう
  * mhidakaが96Pを1ヶ月で書いてね☆ とか言ってきた時はこいつ頭おかしいな！？と思った（104P書いた）

#### 書く

* プロジェクト構成はどっかからコピーしてくる
  * 大抵一個前の著書から
  * review-init とかでもいいと思う
* とりあえずまずは分量をたくさん書く
  * 調査過程で役に立ったURLなどはコメントとしてしっかり残す
  * 案外、後から再調査する必要が生じる事があるもの
  * 自分の文章のソースがどれか追跡できるようにしておくのは重要
* 構造の変更、文章の練り上げなどは後からでも出来る！
  * 特に慣れないうちはレビュアーに依るところが大きいのでまずレビューしてもらえる所まで頑張って持ってく
  * 節A, B, Cの間の依存関係は最初に整理しておく
    * 変数と関数、どちらを先に教えるか で文章の内容がガラっと変わる
    * この依存関係を変える場合、大幅な書き直しが発生するので気をつける

#### レビュー取り込み

* レビュワーからの修正はpull request経由で受け取る [例](https://github.com/typescript-ninja/typescript-in-definitelyland/pull/7/files)
  * typoの修正は直接、構成変更についてはコメントとして書く
  * コメントの書式はある程度決めておく
    * `#@# REVIEW 名前` など あとから検索しやすく
    * 対応したものは `#@# OK REVIEW 名前` などに改変する 定期的に消す
    * 修正後のレビュワーによる再確認は基本行わない
      * そんな時間があるならもう一回通しで読んで貰ったほうがよい
* 個人毎にレビューの能力に大幅な違いがあるので気をつける
  * 誤字の発見が上手い人
    * わかめは誤字は脳内で自動補正がかかるらしくてあまり気がつかない…
  * わかりやすい言い回しに変更するのが上手い人
  * わかりやすい構成に組み替えるのが上手い人
  * 特定のパターンの検知・修正が得意な人
* レビュワーには対象読者に近い人を必ず入れる
  * 常識だと思っていた範囲が実は常識じゃなかった！みたいなことが結構多い
  * その人に教える過程でどういう書き方をするのが良いか整理される場合も多い
    * 人によって理解の方法は違うのでその人に特化しないように留意する

#### 校正

* このフェーズに入ったら基本的には文章を直接触らない
  * 著者がpull requestを出す側に回る
* 編集者の修正は直接masterにpushする場合が多い [例](https://github.com/typescript-ninja/typescript-in-definitelyland/commit/9335e77a8c3f6214b97a61702a2ea0e5c44194a0)
  * 変更点が気になる場合はコミットログを追って確認する
    * 作業速度的に問題がないのであればpull request運用でも良いだろう
* 商業の場合、編集者の言うことは基本的に鵜呑みにする
  * 相手は文章のプロなので
  * こっちは技術のプロなので内容の正確さの担保が最低限の責務

### プロジェクト構成

* articles/
  * 原稿を置く
  * 昔はプロジェクトルートに置いてたけど、プロジェクトルートにあるファイルが多くなりすぎたのと、1段掘っても何も困らなかったので
* articles/images/
  * 章単位でフォルダを切る Re:VIEW 1.3.0か1.4.0くらいからこれが可能 [このへん](https://github.com/kmuto/review/wiki/ImagePath)
* code/
  * サンプルコードは全部ここに置く
  * 章・節 程度のレベルでフォルダ分けする
  * 原稿中のソースコードは全部[#@#mapfile](https://github.com/typescript-ninja/typescript-in-definitelyland/blob/dd6b0f18655397782e61ec1e8faff13844e83199/articles/types-basic.re#L32)でサンプルコードから展開する
    * ビルドが通るコードが原稿に載っていることを保証しやすくなる
    * コンパイラやライブラリのアップデート後の自動チェックが行い易くなる
    * Javaのような重要ではないコードが多く入る言語の時どうするかはまだ知見がない
      * maprangeを使えるようにするべき # でコメントが始まる言語じゃないといけないのが問題
      * dedentも適当に処理してほしい
    * TypeScriptリファレンスではmapfileの他にtslistという独自記法を導入していた
      * 独自記法による飾り枠の自動判別とかも考慮していたが諸般の事情で使われなかった
      * 独自記法によるTypeScriptコンパイラの制御が慣れないとわかりにくい
        * 今回はサンプルコードのファイル名のルールで制御 [このへん](https://github.com/typescript-ninja/typescript-in-definitelyland/blob/dd6b0f18655397782e61ec1e8faff13844e83199/Gruntfile.js#L5)

### 未解決の問題

* 金銭に変換する方法
  * KDP, 達人出版会, booth, gumroadなど？
  * 個人的には 雑誌記事 > 紙の本 > 電子書籍 で儲かるかな？という気持ち
  * 自分が頑張らなくても人様が既にレールを引いてくれてる金銭変換システムに乗るのほんと楽
  * ユーザの時の便利さとはわりと両立しない
    * Googleがインデックスしてくれる形式＝金にならない
* Webサイトで公開するためのノウハウ
  * Re:VIEWは出版物の生成に主眼を置いているのでWebサイトで公開する形式への変換が弱い
  * epubとWebサイト用HTML生成が微妙に切り離しにくい
    * epubが内部的にHTMLビルダに依存しているため
    * 今回はgruntタスク中でcssとlayout.html.erbの使用ON/OFFをファイルコピーで切り抜けている
  * 文章間のリンク生成がめんどくさそう
* epub内でのソースコードのリフローの制御
  * 今回全然調整してないです
  * 検証環境、そもそも何にすればいいかわからんな？
