# DB 設計

## users table

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| nickname           |                     | null: false             |
| email              |                     | null: false             |
| password           | string              | null: false             |
| profile            | text                | null: false             |
| name               | text                | null: false             |
| Birthday           | text                | null: false             |


#ここにパスワードの確認
#本人確認の名前の全角とカタカナの表示の仕方
#生年月日合っているか


### Association

* has_many :items
* has_many :comments
* belongs_to :Purchase record table
* belongs_to :Shipping information





##  items table(商品情報）
)
＃商品情報

| Column                              | Type       | Options           |
|-------------------------------------|------------|-------------------|
| image                               | string     | null: false       |
| title                               | string     | null: false       |
| description                         | text       | null: false       |
| Category                            | text       | null: false       |
| Status                              | references | foreign_key: true |
| Shipping charges                    | string     | null: false       |
| Shipping area                       | text       | null: false       |
| Days to ship                        | text       | null: false       |
| Selling price                       | text       | null: false       |
| Status                              | references | foreign_key: true |


#和訳
#description 説明
#Status 状態
#Shipping charges　配送料の負担　
#Shipping area 発送元の地域
#Days to ship 発送までの日数
#Selling price 販売価格
#Sales commission 販売手数料
#Sales profit　販売利益

### Association

- belongs_to :user
- has_one :Purchase record



## Purchase record table　（購入記録）

| Column      | Type       | Options           |
|-------------|------------|-------------------|
| text        | text       | null: false       |
| ◎prototype  | references | foreign_key: true |
| user        | references | foreign_key: true |

### Association

- belongs_to :user
- belongs_to :items



## Shipping information table （発送先情報）

| Column            | Type       | Options           |
|-------------------|------------|-------------------|
| Card information  | text       | null: false       |
| expiration date   | references | foreign_key: true |
| security code     | references | foreign_key: true |
| Postal code       | text       | null: false       |
| Prefectures       | references | foreign_key: true |
| Municipality      | references | foreign_key: true |
| address           | text       | null: false       |
| Building name     | references | foreign_key: true |
| phone number      | references | foreign_key: true |


### Association

- belongs_to :item
- belongs_to :user

#Card information カード情報
#expiration date　有効期限
#security code セキュリティコード
#Postal code　郵便番号
#Prefectures 都道府県
#Municipality 市町村区
#address　番地
#Building name 建物名

