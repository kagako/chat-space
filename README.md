## contents テーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true, null: false|
|group_id|references|foreign_key: true, null: false|

### Association
- belongs_to :group
- belongs_to :user

## userテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false, unique: true|
|email|string|null: false, unique: true|

### Association
- has_many :groups, through: :group_users
- has_many :group_users
- has_many :chats

## groups テーブル

|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false, unique: true|

### Association
- has_many :users, through: :group_users
- has_many :group_users
- has_many :chats

## chats テーブル

|Column|Type|Options|
|------|----|-------|
|text|text|
|image|string|
|group|references|foreign_key: true, null: false|
|user|references|foreign_key: true, null: false|

### Association
- belongs_to :user
- belongs_to :group
