# テーブル設計

## users テーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| nickname           | string | null: false               |
| email              | string | null: false  unique: true |
| encrypted_password | string | null: false               |
| last_name          | string | null: false               |
| first_name         | string | null: false               |
| last_name_kana     | string | null: false               |
| first_name_kana    | string | null: false               |
| birth_date         | date   | null: false               |

### Association

- has_many :items
- has_many :purchases

## items テーブル

| Column       | Type         | Options                        |
| ------------ | ------------ | ------------------------------ |
| item_name    | string       | null: false                    |
| text         | text         | null: false                    |
| category_id  | integer      | null: false                    |
| condition_id | integer      | null: false                    |
| cost_id      | integer      | null: false                    |
| area_id      | integer      | null: false                    |
| datee_id      | integer      | null: false                    |
| price        | integer      | null: false                    |
| user         | references   | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_one :purchases

## addresses テーブル

| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| postal_code   | string     | null: false                    |
| area_id       | integer    | null: false                    |
| municipality  | string     | null: false                    |
| house_number  | string     | null: false                    |
| phone_number  | string     | null: false                    |
| building_name | string     |                                |
| purchase      | references | null: false, foreign_key: true |

### Association

- belongs_to :purchase

## purchases テーブル

| Column       | Type       | Options                        |
| ------------ | ---------- | ------------------------------ |
| user         | references | null: false, foreign_key: true |
| item         | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one :address