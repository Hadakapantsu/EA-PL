# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# テーブル設計

## users テーブル
| Column          | Type    | Options     |
| --------------- | ------- | ----------- |
| nickname        | string  | null: false | 
| email           | string  | null: false |
| password        | string  | null: false |

### Association

- has_many :petroom_users
- has_many :petrooms, through: petroom_users
- has_many :messages



## petrooms テーブル

| Column    | Type   | Options     |
| --------- | ------ | ----------- |
| petname   | string | null: false |

### Association

- has_many :petroom_users
- has_many :users, through: petroom_users
- has_many :messages


## petroom_users テーブル

| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| user      | references | null: false, foreign_key: true |
| petroom   | references | null: false, foreign_key: true |

### Association

- belongs_to :petroom
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| petroom | references | null: false, foreign_key: true |

### Association

- belongs_to :petroom
- belongs_to :user

