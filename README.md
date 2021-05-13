<h1 align="center">くさつ販促アプリ</h1>

![プリン投稿](https://user-images.githubusercontent.com/68247921/117586915-2d491480-b156-11eb-96b6-27e0b257ce00.jpeg)

## 概要
- 草津温泉のお土産屋さん「草津たまごファーム」の商品の販促アプリです。
- テックキャンプ 応用カリキュラムで作成。
- 作成期間 2020/8/1 ~ 2020/8/3

## 制作意図
- コロナ禍に苦しむ社会で役に立つアプリを作りたいという一心で、全国で不振に喘ぐ観光業や飲食業の手助けをするアプリを制作しました。
つまり、コロナ禍で旅行や飲食店に行けない今だからこそ、旅行に行けなくても観光気分を味わえ、飲食店が投稿した商品を見て、お取り寄せして食べた感想をコメントすることで、観光地の飲食店の手助けにもなるアプリを作りました。
尚、このアプリでは、観光地として草津温泉を、飲食店として土産店の草津たまごファームを一例として作成しました。

## このアプリで、できること（１）
- 店員は、売りたい商品の画像とコメントを投稿、編集、削除ができます。
- ログインしていなくても、店員の投稿を閲覧できます。
- ログインしていなくても、店員の投稿の詳細をクリックすると、店員の投稿に対するコメントを閲覧できます。
- 新規登録もしくはログインすれば、店員の投稿にコメントできます。
- 商品名を上部の入力欄で検索することで、その商品名を含む投稿を検索することができます。
- 例えば、店員の投稿で、お客さんと下記の画像の様に、やり取りすることによって、商品を販促できます。
<img width="909" alt="プリンこめんと改" src="https://user-images.githubusercontent.com/68247921/93275222-513a9d00-f7f7-11ea-9212-e11d16adfafc.png">


## このアプリで、できること（２）
- トップページの投稿一覧で、投稿者である店員名をクリックすると、ショップのホームページに遷移します。

![result](https://user-images.githubusercontent.com/68247921/117588235-12c66980-b15d-11eb-9682-3728fd708301.gif)


## このアプリで、できること（３）
- トップページ左上の、草津温泉virtual観光はコチラ
をクリックするとショップの前のストリートビューに遷移するので、お客さんは観光気分を味わえます。

![result](https://user-images.githubusercontent.com/68247921/117587860-e7db1600-b15a-11eb-9618-e92be2d84b9e.gif)

## 実装予定の内容
- 同じ要領で、全国の全ての飲食店で使える仕様にする予定です。

# サイトURL紹介
## URL
- https://kusatumakita2.herokuapp.com/
## テストアカウント
### スタッフ用
- メールアドレス： staff1@yahoo.co.jp
- パスワード： staff1
### お客さん用
- メールアドレス： kyaku1@yahoo.co.jp
- パスワード： kyaku1

## 使用言語
Ruby, Ruby on Rails, RSpec, HTML, CSS

# テストコード
## ユーザーの登録時に確認が必要なバリデーションのテスト
- nicknameとemail、passwordとpassword_confirmationが存在すれば登録できること
- nicknameが空では登録できないこと
- emailが空では登録できないこと
- passwordが空では登録できないこと
- passwordが存在してもpassword_confirmationが空では登録できないこと
- nicknameが7文字以上であれば登録できないこと
- nicknameが6文字以下では登録できること
- 重複したemailが存在する場合登録できないこと
- passwordが6文字以上であれば登録できること
- passwordが5文字以下であれば登録できないこと
## コントローラーのテスト
- newアクション
- editアクション
- indexアクション

# DB設計
## Usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|email|string|null: false, unique: true|
|password|string|null: false|
### Association
- has_many :tweets
- has_many :comments

## Tweetsテーブル
|Column|Type|Options|
|------|----|-------|
|tweet|text|null:false|
|image|string|null: false|
|user_id|references|null:false, foreign_key: true|
### Association
- belongs_to :user
- has_many :comments

## Commentsテーブル
|Column|Type|Options|
|------|----|-------|
|comment|text|null:false|
|tweet_id|references|null:false, foreign_key: true|
|user_id|references|null:false, foreign_key: true|
### Association
- belongs_to :tweet
- belongs_to :user

