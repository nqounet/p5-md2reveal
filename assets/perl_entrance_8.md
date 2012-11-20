# ![Perl入学式](/images/perl-entrance_t.png)
<!-- data-scale="0.5" -->

# Perl入学式 #8

<http://www.perl-entrance.org>

* 日時
    * 2012年9月23日（日） 14:00 - 17:00
* 会場
    * Joe'sクラウドコンピューティング
    * <http://www.joeswebhosting.net>

## Perl入学式について

* Perl入学式(<http://www.perl-entrance.org>)は, プログラミング未経験者からPerl初心者を対象としたワークショップです
* 公式Twitter
    * [@Perl_Entrance](http://twitter.com/perl_entrance)
* 公式ハッシュタグ
    * \#Perl入学式
* 公式Facebookページ
    * <https://www.facebook.com/PerlEntrance>

## 会場について

* 今回のPerl入学式は「Joe'sオープンソースJelly」の一環ということで、株式会社Joe'sクラウドコンピューティング（<http://www.joeswebhosting.net>）様より特別に会場をお借りしています
* この場をお借りしてお礼申し上げます

## ロゴについて

![Perl入学式](/images/perl-entrance_t_300.png)

* 横山陽平さん(<http://yokoyamayohei.com/>)にデザインしていただきました
* この場をお借りしてお礼申し上げます

## IT勉強会スタンプラリー

![IT勉強会スタンプラリー](/images/it-stamp.png)

* Perl入学式は, IT勉強会スタンプラリー(<http://it-stamp.jp/>)に参加しています
* 今回のPerl入学式は, スタンプラリーの対象となる勉強会です
* 台紙は勉強会終了後にお渡しします

## 喋ってる人

* 名前 ： papix (ぱぴっくす)
* Twitter ： [@__papix__](http://twitter.com/__papix__)
* 仕事 ： 大学院生
* ブログ ： [Masteries](http://papix.hateblo.jp)

## [YAPC::Asia](<http://yapcasia.org/2012/>)に行こう!

* Yet Another Perl Conference
    * 日本最大級のPerlの祭典！
    * 2012年9月27日から29日！！
    * 会場：東京大学！！！

## Perl入学式も出ます！

* [Perl入学式をやってみた!](http://yapcasia.org/2012/talk/show/2c8dfc82-bd2b-11e1-a568-b39f6aeab6a4)
* 開始時間：2012-09-29（土） 15:20:00
* 是非お越しください！
* [papix](https://twitter.com/__papix__)が喋ります！！

## 本日の内容

* Perlでのテスト - Test::More
* 復習問題
* Mojoliciousを使ってみよう
* Mojoliciousでhello, world!
* スタイルを整えてみよう
* 複数のページを作ってみよう

## Perlでのテスト - Test::More

## テスト

* プログラミング言語を使ってプロダクトを作る上で, テストは非常に重要です.
	* まずテストから書き始める, というTDD(test-driven development)という開発手法があったりもします.
* もちろんPerlには, テストを助けるモジュールがいくつかあります.
* 今回は, その中の1つ, Test::Moreをご紹介します.

## sample.pl

	use strict;
	use warnings;
	
	# &pow($x, $y) = $x ** $y を計算する関数
	sub pow {
		my ($left, $right) = @_;
		return $left ** $right;
	}
	
	1;

* このスクリプトをテストします.

## sample.t

	use Test::More;
	
	require 'sample.pl'; # テストするスクリプト
	
	# &pow(2, 3) = 2 ** 3 = 8になるか確かめるテスト
	ok( &pow(2, 3) == 8, '&pow(2, 3) = 8');
	
	# テストの終わりを示すお約束
	done_testing;

* ok関数は, 1つ目の引数の式が真ならok, 偽ならngとなります.
* 2つ目の引数はコメント(テストの説明)です.

## テスト実行

	$ perl sample.t
	ok 1 - &pow(2, 3) = 8
	1..1

* 問題がないなら, このように'ok'が出力されます.

## 失敗した場合

	$ perl sample.t
	not ok 1 - &pow(2, 3) = 8
	#   Failed test '&pow(2, 3) = 8'
	#   at sample.t line 5.
	1..1
	# Looks like you failed 1 test of 1.

* 実装した関数に問題があり, 条件式が偽になる場合, このようなエラーが出力されます.

## テスト用関数(代表的なもの)

	# 引数の$gotと$expectedが等しいかテスト.
	is( $got, $expected, $test_name );

	# 引数の$gotが正規表現のqr/expected/にマッチするかテスト.
	like( $got, qr/expected/, $test_name );
	
	# リファレンスである$gotと$expectedが同じ構造(内容)かテスト.
	is_deeply( $got, $expected, $test_name );

* `$test_name`はテストの説明です.

## Test::Moreの詳細

* perldocに詳しい説明があります.
	* [Test::More - テストを書くためのもう一つのフレームワーク](http://perldoc.jp/docs/modules/Test-Simple-0.96/lib/Test/More.pod)
* 大抵のモジュールにはテストがあるので, それを参考にしてみるのもいいかもしれません.

## Let's challenge!

* Test::Moreを使いつつ, ここまで学んできたことを復習してみましょう.
	* [Perl入学式のgithubアカウント](https://github.com/perl-entrance-org/)に, 第8回用の復習問題リポジトリがあります.
	* まず最初に, `$ git clone git://github.com/perl-entrance-org/perl-entrance-2012-08.git`でclone(ダウンロード)しましょう.
* gitがインストールされていない場合インストールしましょう.
	* Ubuntuの場合, `$ sudo apt-get install git-core`でOKです.

## お約束
    #!/usr/bin/env perl
    use utf8;
    use strict;
    use warnings;
    
    binmode STDIN,  ":encoding(UTF-8)";
    binmode STDOUT, ":utf8";
    binmode STDERR, ":utf8";

* スクリプトを書く前に, このお約束のコードを書くようにしましょう.
* これ以下, お約束は省略します.

## 復習問題

## 復習問題(時間: 20分)

* `perl-entrance-08.t`がテストスクリプト, `perl-entrance-08.pl`が練習問題を回答するスクリプトです.
* 中に問題が書いてありますので, 問題に従ってスクリプトを記述すれば, `perl-entrance-08.t`が全てOKになるはずです.
* わからない点, こまった所は遠慮せず聞いて下さいね.
	* ちなみに, `sample.t`, `sample.pl`は, 先程Test::Moreの説明で使ったスクリプトです.

## Mojoliciousを使ってみよう

## これからの目標
* Perl入学式 \#8以降は, Mojoliciousを利用した簡単なウェブアプリケーション開発を経験しつつ, ここまでに学んだ知識や, ここまで紹介できなかったテクニックを披露していきたいと考えています.
* \#8から\#12までの全4回で構成する... 予定です.

## What's is Mojolicious?

* Mojolicious(もじょりしゃす)は, PerlのWebアプリケーションフレームワークです.
* cpanでMojoliciousをインストールすれば, 試験用サーバ'morbo'などの環境も用意できます.
* [日本語マニュアル](https://github.com/yuki-kimoto/mojolicious-guides-japanese/wiki)もあります.

## Mojoliciousの環境構築

* [#8に向けた宿題](http://www.perl-entrance.org/2012/09/8.html)でも解説しましたが, 念の為もう一度...
* Perlbrewなどでcpanmがインストールされている場合, `$ cpanm Mojolicious`でOKです.
* cpanmがインストールされていない場合, `$ sudo cpan Mojolicious`でインストールできます.

## Mojoliciousの動作を確認

* ワンライナーでMojoliciousがインストールできたか確認します.
    * `mojo version`を実行してPerlのバージョンやMojoliciousのバージョンが表示されればOKです.
	* `$ perl -Mojo -E 'a( { "text" => "Neko" } )->start;' daemon`を実行した後, ブラウザで`127.0.0.1:3000`を開いて, `Neco`と表示されればOKです.

## Mojoliciousでhello, world!

	use Mojolicious::Lite;
	use utf8;

	get '/' => sub {
		my $self = shift;

		$self->render(text => 'Hello, world!');
	};

	app->start;

* 早速, Mojoliciousでhello, world!を動かしてみましょう.
* このスクリプトを`hello.pl`という名前で保存して, `$ morbo hello.pl`で実行してみましょう.
* ブラウザで`127.0.0.1:3000`を開けば, `Hello, world!`と表示されるはずです.

## コードの解説(1) 

	use Mojolicious::Lite;
	use utf8;

* `Mojolicious::Lite`は`Mojolicious`のLite版... って, そのまんまですね.
* `Mojolicious::Lite`は1つのスクリプトで複数のページを作成できます. 一方`Mojolicious`は, 1ページ=1スクリプトで構成されます.
* もちろん, `Mojolicious::Lite`で作成した複数のページを, `Mojolicious`の為に分割することも可能です.
* ｢まずはMojolicious::Liteで作って, 大規模になったらMojoliciousに｣という事も可能です.

## コードの説明(1)

	use Mojolicious::Lite;
	use utf8;

* `Mojolicious::Lite`は`Mojolicious`をインストールすれば同時にインストールされますので, 別にインストールする必要はありません.
* `use Mojolicious::Lite;`をすれば, 自動的に`use warnings;`と`use strict;`が有効になります. わざわざ書く必要はありません.
* 以下, この2行は省略します.

## コードの説明(2)

	get '/' => sub {
		my $self = shift;

		$self->render(text => 'Hello, world!');
	};

* `get '/' => sub { ... };`は, getメソッドで'/'にアクセスした場合, subの中の`...`の処理を行う, という意味です.
* `my $self = shift;`は｢お約束｣と思っておいて下さい.

## コードの説明(2)
	get '/' => sub {
		my $self = shift;

		$self->render(text => 'Hello, world!');
	};

* `$self->render(text => 'Hello, world!');`で, ｢textの形式で, 'hello, world!'と出力せよ!｣という命令をしています.
* renderの引数が`json => { x => 3 }`なら, json形式で`{"x":3}`が出力されますし, `text => 'Oops!', status => '410'`とすれば, ステータスコードを指定することもできます.

## コードの説明(3)

	app->start;

* アプリケーションとして実行します, というような意味があります.
* これも｢お約束｣と思っておいて下さい.

## 練習問題A(10分)

* `Mojolicious::Lite`を使って, `hello, mojolicious! my name is (あなたの名前)`と出力するスクリプトを書いて, 実行してみましょう.

## スタイルを整えてみよう

* とりあえずテキストは出力されましたが, シンプルです.
* もう少し, ｢スタイリッシュに｣キメたいところです.
* HTMLを使って整形してみましょう.

## テンプレート

	__DATA__
	@@ index.html.ep
	<html>
	<head><title><%= $title %></title></head>
	<body style='padding: 30px;'>
	<%= $string %>
	</body>
	</html>

* `hello.pl`の末尾に(`app->start;`の後に), このようなテンプレートを用意します.
* テンプレートを用意することで, 複数のページで同じようなHTMLを使うことができます.
* （？）同じテンプレートは, `template/index.html.ep`にあります.
* テンプレートを別のファイルにする場合は`template/index.html.ep`として保存することで適用されます.

## テンプレートとデータ

	get '/' => sub {
		my $self = shift;

		$self->stash(string => 'Hello, world!', title => 'hello');
		$self->render();
	} => 'index';

* `/`にアクセスした際の動作を記載する関数を, このように書き換えましょう.
* `$self->stash`で, 先程記述したテンプレートにデータを渡すことができます.
* 最後に`=> 'index';`と記載することで, 使用するテンプレートを指定できます.

## テンプレートと変数

	__DATA__
	@@ index.html.ep
	<html>
	<head><title><%= $title %></title></head>
	<body style='padding: 30px;'>
	<%= $string %>
	</body>
	</html>

* stashでデータが渡されているので, テンプレートの中の`<%= $title %>`は`hello`に, `<%= $string %>`は, `Hello, world!`に置き換わります.
* `<%= $xxx %>`は, テンプレートの中で使える変数だと思って下さい.

## 練習問題B(10分)

	@@ profile.html.ep
	<html>
	<head><title><%= $name %>のプロフィール</title></head>
	<body style='padding: 30px;'>
	私の名前は<%= $name %>です.<br>
	趣味は<%= $hobby %>で, 好きなプログラミング言語は<%= $language %>です.
	</body>
	</html>

* このようなテンプレートに対し, stashで`name`, `hobby`, `language`を与え, あなたの自己紹介(プロフィール)ページを作ってみよう.
* （？）同じテンプレートは, `template/profile.html.ep`にあります.

## 複数のページを作ってみよう

* さきほどのプロフィールを独立したページにして, トップページからリンクを踏めば, プロフィールページを閲覧できるようにしてみましょう.

## インデックスページの用意

	get '/' => sub {
		my $self = shift;

		$self->stash(name => '');
		$self->render();
	};
	$app->start;

* （？）`template/app.pl`を編集していきます.
* `name`が空になっているので, あなたの名前を入力してください.
* morboで実行し, ブラウザでアクセスするとリンクが出てきますが, クリックするとエラーが出力されます.

## プロフィールページの用意

	get '/profile' => sub {
		...
	};

* リンク先の, プロフィールページを作りましょう.
* テンプレートは既に用意してあるので, `$app->start;`よりも上に, 次のようなコードを書きましょう.
* 関数の中身は, 練習問題Bで関数の中に書いたコードと同じです.

## 動作確認

* morboで実行し, ブラウザでアクセスしてみましょう.
* リンクを踏めば, 練習問題Bで作ったプロフィールページが表示されるはずです.

## 最終問題C(30分)

* インデックスページ, プロフィールページの他, もう1つページを作ってみてください.

## 質問タイム
<!-- data-scale="0.5" -->

## お疲れさまでした
<!-- data-scale="0.2" -->
