# データベース設計

## users table
| Column             | Type   | Options                            |
|------------------------------------------------------------------|
| nickname           | string | null: false                        |
| email              | string | null: false unique: true           |
| encrypted_password | string | null: false                        |
| hospital           | string | null: false                        |
| emergency contact  | string | null: false                        |

### Association
has_many :days
has_many :medicines
has_many :life_events
has_many :posts

## medicines table
| Column             | Type       | Options                        |
|------------------------------------------------------------------|
| medicine_name      | string     | null: false                    |
| medicine_amount    | string     | null: false                    |
| medicine_timing_id | integer    | null: false                    |
| user               | references | null: false, foreign_key: true |

### Association
belongs_to :user

## life_events table
| Column             | Type       | Options                        |
|------------------------------------------------------------------|
| events             | string     | null: false                    |
| year               | integer    | null: false                    |
| month              | integer    | null: false                    |
| user               | references | null: false, foreign_key: true |

### Association
belongs_to :user

## days table
| Column             | Type       | Options                        |
|------------------------------------------------------------------|
| mood_score_id      | integer    | null: false                    |
| user               | references | null: false, foreign_key: true |

### Association
belongs_to :user
has_many :posts

## posts table
| Column             | Type       | Options                        |
|------------------------------------------------------------------|
| content            | string     | null: false                    |
| category_id        | integer    | null: false                    |
| user               | references | null: false, foreign_key: true |
| days               | references | null: false, foreign_key: true |

### Association
belongs_to :user
belongs_to :days