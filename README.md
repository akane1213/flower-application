# README

## アプリケーション名
flower-application

## アプリケーション概要
花言葉を調べることができる・登録ユーザーと写真を共有しコメントし合える(コミュニケーション)

## URL
# デプロイ後のURL

## テスト用アカウント
# ログイン機能等を実装した場合は、ログインに必要な情報を記述。

## 利用方法	
花の画像を投稿できる。花言葉を調べることができる。

## 目指した課題解決
お花や花言葉が好きな人が、素敵だと思った花を色んな人と共有できるように目指しました。
更に花言葉をすぐに分かるようにしました。

## 洗い出した要件
### 機能
①ログイン・新規登録機能
②タイムライン(みんなの声)
③花の検索
④花の名前の表示(五十音順)

### 目的
①自分のアカウントを作成し、利用しやすくする
②花の名前がわからない場合、みんなの意見を聞くことができるようにする・コミュニケーション
③ユーザーが簡単にデータ検索出来るようにする
④ユーザーが簡単にデータを見つけやすいようにする

### 詳細
①ログイン・新規登録機能
②自分で撮った花の写真を投稿し、わかる人がコメントできるようにする
③自分の知りたい花言葉の花の名前を検索可能にする
④なんとなくしかわからない花の名前を探しやすいように五十音順で表示しておく

### ストーリー(ユースケース)
①ログイン・新規登録機能を手打ちで入力

②タイムラインタブを儲ける
投稿した写真に「名前教えて！」のタグor説明にハッシュタグを儲ける
コメントができる機能を儲ける
写真投稿(花の特徴などのコメントも)ができる機能を儲ける

③何種類かの有名な花の花言葉が記載されているのが前提
花言葉調べのタブを儲ける
条件に該当する花の検索結果のページで表示する

④何種類かの有名な花の花言葉が記載されているのが前提
五十音順で表示する


## 実装した機能についての画像やGIFおよびその説明
実装した機能について、それぞれどのような特徴があるのかを列挙する形で記述。画像はGyazoで、GIFはGyazoGIFで撮影すること。

## 実装予定の機能
洗い出した要件の中から、今後実装予定の機能がある場合は、その機能を記述

## データベース設計
flower.png

## ローカルでの動作方法
git cloneしてから、ローカルで動作をさせるまでに必要なコマンドを記述。この時、アプリケーション開発に使用した環境を併記することを忘れないこと（パッケージやRubyのバージョンなど）


## テーブル設計

### users テーブル

| Column          | Type   | Options     |
| --------        | ------ | ----------- |
| nickname        | string | null: false |
| email           | string | null: false |
| password        | string | null: false |
| profile         | text   | null: false |
| favorite_flower | text   | null: false |

#### Association

- has_many :timelines
- has_many :comments

### timelines テーブル

| Column         | Type         | Options           |
| ------         | ------       | -----------       |
| title          | string       | null: false       |
| comment        | text         | null: false       |
| user           | references   | foreign_key: true |

#### Association

- belongs_to :users
- has_many   :comments

### comments テーブル

| Column       | Type       | Options          |
| -------      | ---------- | ----------------- |
| text         | text       | null: false       |
| user         | references | foreign_key: true |
| timeline     | references | foreign_key: true |

#### Association

- belongs_to :users
- belongs_to :timelines