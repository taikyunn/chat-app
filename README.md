#テーブル設計

## users テーブル

|column   |Type   |Options    |
|------   |-----  |-----------|
|name     |string |null: false|
|email    |string |null: false|
|password |string |null: false|

### Association

- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages

## rooms テーブル

|column   |Type   |Options    |
|------   |-----  |-----------|
|name     |string |null: false|

### Association

- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages

## room_users テーブル

|column   |Type       |Options                      |
|---------|-----------|-----------------------------|
|user     |references |null: false foreign_key: true|
|room     |references |null: false foreign_key: true|

### Association

- belongs_to :room
- belongs_to :user

## messages テーブル

|column   |Type       |Options                      |
|---------|-----------|-----------------------------|
|content  |string     |                             |
|user     |references |null: false foreign_key: true|
|room     |references |null: false foreign_key: true|

### Association

- belongs_to :room
- belongs_to :user