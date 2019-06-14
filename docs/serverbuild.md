# はじめに
この記事は自分がビルドした際のやり方です。忘れないように書いたメモ程度のものなので内容や手順が必ずしも適当とは限りませんので予めご了承ください。

# バージョン1.14が公開
2019年の4/23日、平成のラストにMinecraftの最新バージョンである1.14が正式にリリースされ遊ぶことができるようになりました。（ランチャー画面も1.14仕様に）
![SnapCrab_Minecraft Launcher_2019-4-26_15-0-28_No-00.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/371392/2d742bfb-fa41-3404-cdec-92f1907a6c9f.png)

詳しいアップデート内容はたくさんの方がまとめてくださっているのでそちらを調べると良いでしょう。
そして、Spigotフォーラムでも開発ビルドが発表された報告されています。[こちら](https://www.spigotmc.org/threads/bukkit-craftbukkit-spigot-bungeecord-1-14-development-builds.369724/)は英語ですが翻訳すれば普通に読めるので詳細が気になる場合は読んでみるといいでしょう。
すぐにでも1.14にサーバーをアップデートしたいところですが、Spigot管理者、md_5が言っているように、これらの最新のビルドは開発専用なので、大規模な公開サーバーで使用するべきではないでしょう。

> “The software released today is the product of several months work. Although the API changes are small compared to 1.13, this is not a small release. In fact it is almost as large as 1.13. Accordingly the software has no doubt inherited many bugs from Vanilla and a few of its own, meaning it is not ready for use on a production server.” -md_5


# ビルドの下準備
1.14の最新バージョンっといってもビルドする作業自体は今までのバージョンと殆ど変わりません。
今回はWindowsの環境でビルドするので[Git for Windows](https://gitforwindows.org/)をインストールしておく必要があります。Linuxでやりたい！という場合はUbuntuであれば``sudo apt-get install git``ですぐにインストールすることができます。

# BuildTools.jarをダウンロード
[こちら](https://hub.spigotmc.org/jenkins/job/BuildTools/)からビルドツールダウンロードページに飛び、「最新成功ビルドの成果物」の下にあるBuildTools.jarをクリックするとダウンロードすることができます。
![SnapCrab_NoName_2019-4-26_15-29-51_No-00.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/371392/9e54e62d-7283-b080-53e2-6c037ddfb7cb.png)

# BuildTools.jarを移動

ダウンロードしたビルドツールは専用のフォルダを作り、そこに置きます。
フォルダの名前はなんでもいいですが、場所は、Cドライブ直下に置くと次の作業でパスが指定しやすくて良いでしょう。（そんなのは気にしない！という場合は他のところでも大丈夫です。）
![SnapCrab_NoName_2019-4-26_15-33-31_No-00.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/371392/ed9bbbc9-5ef5-6fc7-dbc8-5f1ec715d302.png)

# Git Bashを起動
Gitをインストールが出来ている場合は、スタートメニューから「Git」と検索することでGit Bashが候補に出てくるかと思いますので、それをクリックして起動させます。
![SnapCrab_NoName_2019-4-26_15-41-42_No-00.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/371392/2b0ee480-6294-16f4-c2bb-59e273ea257d.png)

すると、なんだか黒い画面のウィンドウが出ますが、こちらからSpigotをビルドすることになります。

# ビルドする
先程起動したGit Bashにて、まずはカレントディレクトリを指定するため``cd C:/<フォルダの名前>``と入力します。今回はフォルダの名前を「Build」にし、Cドライブ直下に置いたので``cd C:/Build``と入力します。
そして、ビルドのコマンドを入力しますが、こちらは**ビルドするSpigotのバージョンごとに異なるので**、[こちら](https://www.spigotmc.org/wiki/buildtools/#latest)のページから自分のビルドするバージョンあったコマンドを選んで入力しましょう。
今回インストールするバージョンは最新なので「Latest」を選択したいところですが、これは1.13.2用なので、その下の``java -jar BuildTools.jar --rev 1.14``をGit Bashに入力します。
![SnapCrab_NoName_2019-4-26_15-51-6_No-00.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/371392/454c1b58-d447-7ae0-75af-858be8b839b6.png)

すると、勝手にビルドが進行していくので終わるまでしばし待ちます。（私の環境では数分で終わりました）
こんな表示が出たらビルド成功ということになります。
![SnapCrab_NoName_2019-4-26_16-14-12_No-00.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/371392/5c06e6ad-a766-6fbc-6653-7ede4cb72d59.png)

ビルドが終了したら、先程ビルドツールを入れていたフォルダにたくさんのファイルが生成されていますが、使うのは**spigot-1.14.jar**だけなので、それをサーバー用のフォルダに移動して起動させます。（ここでは起動の仕方などは紹介しません）
Git Bashは``exit``で終了することが出来ます。

# さいごに
無事起動してログインすることが出来ました。
Spigotのビルド方法は日本人でもまとめてくださっているかたがたくさんいらっしゃるのでこの方法でよくわからない人はそちらを調べてみると良いでしょう。
![2019-04-26_16.23.33.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/371392/c82e297d-03b8-d803-ab71-be7c16632db6.png)

蛇足ですが、私は普段はマインクラフトサーバーを運営しているので、遊びに来てくれると嬉しいです。
Twitter: [@dedetyan968](https://twitter.com/dedetyan968)
運営しているサーバー: [lucknetwork.jp](https://lucknetwork.jp)
