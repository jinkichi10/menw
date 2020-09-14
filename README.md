# README


# オリジナルアプリ名
麺stagram


# 概要(このアプリでできることを書いて下さい)
ユーザー作成
ユーザー編集
画像投稿
投稿削除
コメント機能
コメント削除
いいね機能
いいね削除


# 本番環境(デプロイ先　テストアカウント＆ID)
https://menw.herokuapp.com/

メールアドレス:　test@com
パスワード:　testtest
ユーザー名:　testuser


# 制作背景(意図)
ラーメン　×　instagram

シンプルにラーメンが好きだから！
・好きなラーメンを投稿して、共有できるアプリを作りたいと思いました。
・カリキュラム以外の教材で、アプリを作成する事でrailsの理解が深まると考えました。

# DEMO(gifで動画や写真を貼って、ビューのイメージを掴んでもらいます)
![Uploading 2020-09-14 17.07のイメージ.jpeg…]()
￼



# 工夫したポイント
・実際のinstagramのようなビューに近付けました。

・ラーメンの写真は正方形で撮るとバランスが良いので、
「MiniMagick」を使って自動的に正方形に加工、投稿できるようにしました。


# 使用技術(開発環境)
・Ruby on Rails
・JavaScript
・HTML
・CSS
・SCSS


# 課題や今後実装したい機能
・投稿ページからの遷移が
・マイページに自分の写真投稿一覧
・プロフィール画像の表示
・1投稿で複数枚の写真投稿機能
・地図機能（お店やスポットの位置情報）
・拡張子「heic」を投稿可能にする。

# DB設計

# menstagram DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|default: "", null: false
|email|string|default: "", null: false, unique: true, index: true 
|profile_photo|string||

### Association
- has_many :posts
- has_many :comments
- has_many :likes


## postsテーブル
|Column|Type|Options|
|------|----|-------|
|caption|string||
|user_id|integer|null:false, foreign_key: true|

### Association
- belongs_to :user
- has_many :photos


## photosテーブル
|Column|Type|Options|
|------|----|-------|
|image|string|null: false|
|post_id|integer|null:false, foreign_key: true|

### Association
- belongs_to :post


## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|comment|text|null:true|
|post_id|integer|null:false, foreign_key: true|
|use_id|integer|null:false, foreign_key: true|

### Association
- belongs_to :post
- belongs_to :user


## likesテーブル
|Column|Type|Options|
|------|----|-------|
|post_id|integer|null:false, foreign_key: true|
|use_id|integer|null:false, foreign_key: true|

### Association
- belongs_to :post
- belongs_to :user
