# api-setup-practice

## 概要
COACHTECH 教材 Tutorial 11-1「API開発環境の構築と疎通確認」で作成した成果物です。
API開発専用プロジェクトをセットアップ（Githubからクローン）し、「Hello World」を出力させる疎通確認を実施

## 使用技術
- PHP 8.x
- Laravel 10.x
- REST API（JSONレスポンス）
- Postman（動作確認）

## ディレクトリ構成（抜粋）
```text
~/laravel-practice/
└── 10-1-6_hands-on/
    └── app-setup-practice/
        ├── routes/                            #APIとのルーティングを実施
             └── api.php
```

## 学んだこと
- POSTMANを用いたAPIの実行確認の方法
    - URL部分に**URLパス**し、リクエストを設定することで容易にAPI実行を確認することができる。
- route/api.phpにAPIを作成する。
    - ルーティングの設定自体はコントローラーとほぼ同義
    ```
    Route::get('/api/hello', function () {
    ```
    ではなく、
    ```
    Route::get('/hello', function () {
    ```でOK
## 動作確認
1. GithubからAPI開発専用のスターターキットをクローン（私のGithubからクローン）
```
git clone git@github.com:aridome-sashizume/api-setup-practice.git
```
2. sailの起動
```
./vendor/bin/sail up -d
```
3. POSTMANを起動し、HTMLでGETメソッドを設定し以下のURLを入力し、送信をクリック
```
http://localhost/api/hello
```
返却されたステータスが**200 OK**と表示され、メッセージに以下が表示されれば成功
```
{
    "message": "Hello, World!"
}
```
※予め、**routes/api.php**に以下の内容でルーティングを設定している。
```
Route::get('/hello',function(){
    return response()->json(['message' => 'Hello, World!']);
});
```