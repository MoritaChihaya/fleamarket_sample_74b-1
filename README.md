# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation
<!-- active_hashで作成するデータ郡については以下判断で処理 -->
<!-- テーブルは作成しない／Associationにも記述しない／Colum,Type,Optionは記述する -->

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|id                             |string|null: false|
|delivery_information_id        |references|null: false|
|credit_card_id                 |references|null: false|
|nickname                       |string|null: false|
|email                          |string|null: false , unique: true|
|password                       |string|null: false , unique: true|
|first_name                     |string|null: false|
|family_name                    |string|null: false|
|first_name_furigana            |string|null: false|
|family_name_furigana           |string|null: false|
|birth_date                     |date|null: false|
|created_at                     |timestanp|null: false|
|updated_at                     |timestanp||
### Association
- has_many :items
- has_many :credit_cards , dependent: :destroy
- has_many :delivery_information , dependent: :destroy
- has_many :items_purchases


## delivery_informationテーブル
|Column|Type|Options|
|------|----|-------|
|id                             |string|null: false|
|user_id                        |references|null: false , foreign_key: true|
|prefecture_id(acitve_hash)     |references|null: false|
|delivery_family_name           |string|null: false|
|delivery_first_name            |string|null: false|
|delivery_family_name_furigana  |string|null: false|
|delivery_first_name_furigana   |string|null: false|
|postal_code                    |string|null: false|
|city                           |string|null: false|
|address                        |string|null: false|
|building_room_number           |string||
|phone_number                   |string||
|created_at                     |timestanp|null: false|
|updated_at                     |timestanp||
### Association
- belongs_to :user


## credit_cardsテーブル
|Column|Type|Options|
|------|----|-------|
|id                             |string|null: false|
|user_id                        |references|null: false , foreign_key: true|
|customer_id                    |string|null: false|
|card_id                        |string|null: false|
|created_at                     |timestanp|null: false|
|updated_at                     |timestanp||
### Association
- belongs_to :user


## itemsテーブル
|Column|Type|Options|
|------|----|-------|
|id                             |string|null: false|
|user_id                        |references|null: false , foreign_key: true|
|image_id                       |references|null: false , foreign_key: true|
|categories_id                  |references|null: false , foreign_key: true|
|size_id(acitve_hash)           |references||
|prefecture_id(acitve_hash)     |references|null: false|
|condition_id(acitve_hash)      |references|null: false|
|shipping_fee_id(acitve_hash)   |references|null: false|
|delivery_days_id(acitve_hash)  |references|null: false|
|item_name                      |string|null: false|
|price                          |string|null: false|
|description                    |text|null: false|
|brand_id                       |references|foreign_key: true|
|created_at                     |timestanp|null: false|
|updated_at                     |timestanp||
### Association
- belongs_to :user
- belongs_to :items_purchases
- has_many :images
- belongs_to :categories
- has_many :brands

## items_purchasesテーブル
|Column|Type|Options|
|------|----|-------|
|id                             |string|null: false|
|item_id                        |references|null: false , foreign_key: true|
|user_id                        |references|null: false , foreign_key: true|
|purchase_status_id(active_hash)|references||
|created_at                     |timestanp|null: false|
|updated_at                     |timestanp||
### Association
- belongs_to :user
- belongs_to :item

## imagesテーブル
|Column|Type|Options|
|------|----|-------|
|id                             |string|null: false|
|item_id                        |references|null: false , foreign_key: true|
|image               　         |string|null: false|
|created_at                     |timestanp|null: false|
|updated_at                     |timestanp||
### Association
- belongs_to :item


## categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|id                             |string|null: false|
|name                  |string|null: false|
|ancestry_path                  |string||
|created_at                     |timestanp|null: false|
|updated_at                     |timestanp||
### Association
- has_many :categories

## brandsテーブル
|Column|Type|Options|
|------|----|-------|
|id                             |string|null: false|
|name                           |string|null: false|
|created_at                     |timestanp|null: false|
|updated_at                     |timestanp||
### Association
- has_many :item


* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

