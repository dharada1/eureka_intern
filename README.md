# eureka_intern

## 概要

エウレカのサマーインターン 2日間でTwitterクローンをつくる (2017/9/7〜2017/9/8)

原田 @dharada1 & 入江 @marky080120 チーム

Python 3.4.2 / django 1.11.5 / sqlite

アプリ名はPAKUTTER

## 進めかた

・Twitterの機能を実際に触りながら洗い出し、コアとなる機能を確認した。(ログイン・フォロー・ツイート)

・言語はチーム2人とも使った経験のあるPythonを選択

・フレームワークはDjango (Djangoを触るのは2人とも初)
選定基準 ①Pythonの中で一番情報が多いもの ②実際Webアプリケーションとしての公開に耐えうる(拡張性の観点で)もの

## できたこと

### コア機能完成

・登録ログインログアウト

・ツイートを投稿できる

・フォローした人のツイート+自分のツイートがタイムラインで見られる。

・タイムラインでは、最新のツイートが、上に表示されていく。

・自分のフォロイー・フォロワーが一覧で見られる。

・自分のツイート削除機能

・ツイート削除権限の判別(他の人が削除はできない。フロント側/サーバー側両方対応した。)

・フォローボタン/リムーブボタンの表示(自分のプロフィールには表示しない。フォロー状態によってボタン表示が変わる。)

・User（djangoデフォルトのユーザーを継承）/ Tweet / Follow(リレーションテーブル)

・全体的にクエリに無駄がないか joinとかしてSQLの発行回数を意識

・XSS対策
(<script>alert();</script>でアラート出ない)
(テンプレートで変数展開時に変数をエスケープしてくれる)

・CSRF対策

・パスワードのハッシュ化(SHA-256)

## できなかったこと

・インデックスの設定(とりあえずアプリケーションを動く状態に完成させてから貼ろうと思ったが、時間が足りなかった。)

・timezone日本時間にするとこ
(DBに標準時で保存されてることが重要と考えた。表示を日本時間にするのはちょっとややこしく、時間が足りなかった。)

・詳細なバリデーション(ブランクを許容しない、140文字以下切り捨てとかしかできてない、エラーメッセージ表示できないなど)

・SQLインジェクション対策(確認できてない)

・ページネーション(苦し紛れに select時 limit 20 とかで対応してる...)

・実際に飛んでるクエリの確認 (django側から呼び出しっぱなし...)
