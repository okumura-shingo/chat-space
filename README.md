# DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many :messages
- has_many :groups_users
- has_many :groups,  through:  :groups_users

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :groups_users
- has_many :messages
- has_many :users,  through:  :groups_users

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
|photo|text||
|message|string||
### Association
- belong_to :user
- belong_to :group

## groups_userテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|groups_id|references|null: false, foreign_key: true|
### Association
- belong_to :user
- belong_to :group