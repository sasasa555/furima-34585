# DB 設計

## users table

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| nickname           | string              | null: false             |
| email              | string              | null: false             |
| encrypted_password | string              | null: false             |            |
| surname            | string              | null: false             |
| name               | string              | null: false             |
| surname_katakana   | string              | null: false             |
| name_katakana      | string              | null: false             |
| birthday           | date                | null: false             |


#Surname 姓
#Katakana
#
#



### Association

* has_many :items
* has_many :purchase_records




##  items table(商品出品機能）

＃商品情報

| Column                              | Type       | Options           |
|-------------------------------------|------------|-------------------|
| title                               | string     | null: false       |
| description                         | text       | null: false       |
| category_id                         | integer    | null: false       |
| status_id                           | integer    | null: false       |
| shipping_charges_id                 | integer    | null: false       |
| shipping_area_id                    | integer    | null: false       |
| days_to_ship_id                     | integer    | null: false       |
| selling_price                       | integer    | null: false       |
| user_id                             | references | foreign_key: true |


#和訳
#description 説明
#Status 状態
#Shipping charges 配送料の負担
#Shipping area 発送元の地域
#Days to ship 発送までの日数
#Selling price 販売価格


### Association

- belongs_to :user
* has_one    :purchase_record
- belongs_to :shipping_address




## purchase_record table （商品購入機能）

| Column            | Type       | Options           |
|-------------------|------------|-------------------|
| card_information  | text       | null: false       |
| expiration_date   | integer    | null: false       |
| security_code     | integer    | null: false       |
| user_id           | references | foreign_key: true |
| items_id          | references | foreign_key: true |


### Association

- belongs_to :item
- belongs_to :user
- has_many   :shipping_address


#Card information カード情報
#expiration date 有効期限
#security code セキュリティコード
#Postal code 郵便番号
#Prefectures 都道府県
#Municipality 市町村区
#address 番地
#Building name 建物名


## shipping_address table （配送先情報）

| Column            | Type       | Options           |
|-------------------|------------|-------------------|
| postal_code       | integer    | null: false       |
| active_hash       | integer    | null: false       |
| municipality      | string     | null: false       |
| address           | string     | null: false       |
| building_name     | string     | null: false       |
| phone_number      | string     | null: false       |


### Association

- belongs_to :purchase_record


