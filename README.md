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

# Chat-spaceの DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false,add_index:true|
|mail|string|null: false,unique:true|
|password|string|null: false|
|password_confirmation|string|null: false|
### Association
-has_many :messages
-has_many :groups,through: groups_users
-has_many :groups_users


## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|text|string|null: false|
|img|text|null: false|
|users_id|integer|null: false,foreign_key: true|
|group_id|integer|null: false,foreign_key: true|
### Association
-belongs_to :groups
-belongs_to :groupusers


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false,unique:true|
### Association
-has_many :messages
-has_many :users,through: groups_users
-has_many :groups_users


## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|users_id|integer|null: false,foreign_key: true|
|group_id|integer|null: false,foreign_key: true|
### Association
-belongs_to :groups
-belongs_to :users

