# DB 設計

## users table

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| nickname           | string              | null: false             |
| email              | string              | null: false             |
| password           | integer             | null: false             |
| profile            | text                | null: false             |
| name               | string              | null: false             |
| Birthday           | datetime            | null: false             |


#ここにパスワードの確認
#本人確認の名前の全角とカタカナの表示の仕方
#生年月日合っているか

### Association

* has_many :items
* belongs_to :Purchase record table



##  items table(商品出品機能）

＃商品情報

| Column                              | Type       | Options           |
|-------------------------------------|------------|-------------------|
| image                               | binary     | null: false       |
| title                               | string     | null: false       |
| description                         | text       | null: false       |
| Category                            | boolean    | null: false       |
| Status                              | boolean    | null: false       |
| Shipping charges                    | boolean    | null: false       |
| Shipping area                       | boolean    | null: false       |
| Days to ship                        | boolean    | null: false       |
| Selling price                       | bigint     | null: false       |
| user                                | references | foreign_key: true |


#和訳
#description 説明
#Status 状態
#Shipping charges 配送料の負担
#Shipping area 発送元の地域
#Days to ship 発送までの日数
#Selling price 販売価格


### Association

- belongs_to :user
- has_one :Purchase record



## Purchase record table （商品購入機能）

| Column            | Type       | Options           |
|-------------------|------------|-------------------|
| Card information  | text       | null: false       |
| expiration date   | integer    | null: false       |
| security code     | integer    | null: false       |
| Postal code       | integer    | null: false       |
| Prefectures       | text       | null: false       |
| Municipality      | text       | null: false       |
| address           | text       | null: false       |
| Building name     | text       | null: false       |
| phone number      | integer    | null: false       |
| user              | references | foreign_key: true |
| items             | references | foreign_key: true |



### Association

- belongs_to :item
- belongs_to :user

#Card information カード情報
#expiration date 有効期限
#security code セキュリティコード
#Postal code 郵便番号
#Prefectures 都道府県
#Municipality 市町村区
#address 番地
#Building name 建物名

