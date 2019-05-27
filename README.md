# chat-space
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|index: true, unique: true null: false|

### Association
- has_many :groups, through: :users_groups
- has_many :messages
- has_many :users_groups

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|mediumblog||
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|messages_id|integer|null: false, foreign_key: true|
|users_id|integer|null: false, foreign_key: true|

### Association
- has_many :messages
- has_many :users, through: :user_group
- belongs_to :user_group

## users_groupsテーブル
|Column|Type|Options|
|------|----|-------|
|users_id|integer|null: false, foreign_key: true|
|groups_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
