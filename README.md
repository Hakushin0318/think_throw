# テーブル設計

## users テーブル

| Column             | Type   | options                   |
| ------------------ | ------ | ------------------------- |
| name               | string | null: false               |
| email              | string | null: false, unipue: true |
| encrypted_password | string | null: false               |

### Association

- has_many :user_goals
- has_many :goals, through: user_goals
- has_many :user_branches
- has_many :branches, through: user_branches
- has_many :comments

## user_goals テーブル
| Column             | Type       | options                        |
| ------------------ | ---------- | ------------------------------ |
| user               | references | null: false, foreign_key: true |
| goal               | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :goal

## goals テーブル
| Column             | Type       | options                        |
| ------------------ | ---------- | ------------------------------ |
| goal               | string     | null: false                    |
| branch             | references | null: false, foreign_key: true |

### Association

- has_many :user_goals
- has_many :users, through: user_goals
- has_many :branches

## user_branches テーブル
| Column             | Type       | options                        |
| ------------------ | ---------- | ------------------------------ |
| user               | references | null: false, foreign_key: true |
| branch               | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :branch

## branches

| Column             | Type       | options                        |
| ------------------ | ---------- | ------------------------------ |
| branch             | string     | null: false                    |
| goal               | references | null: false, foreign_key: true |

### Association

- has_many :user_branches
- has_many :users, trough: user_branches
- belongs_to :goal

## comments　テーブル
| Column             | Type   | options                   |
| ------------------ | ------ | ------------------------- |
| comment            | string |                           |
| user               | references | null: false, foreign_key: true |
| branch             | references | null: false, foreign_key: true |

### Association

- belongs_to :branch
- belongs_to :user