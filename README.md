# README


## ChatSpaceの機能
- ①. 新規登録機能 ②.グループチャット機能 ③.チャット相手の検索機能 ④.チャットグループへのユーザー招待機能


## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|integer|null: false,unique: true|

### Association
- has_many: members
- has_many: groups,through: :members
- has_many: messages

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many: members
- has_many: users,through: :members
- has_many: messages

## membersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to: group
- belongs_to: user

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|-------|
|image|string |-------|
|user_id|integer|index: true,null: false, foreign_key: true
|group_id|integer|index: true,null: false, foreign_key: true

### Association
- belongs_to: group
- belongs_to: user
