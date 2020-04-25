# README

# ChatSpace DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null:false|
|email|string|null: false|
|password|string|null: false|
|gender|string|
|avator|text|

### Association
- has_many :posts
- has_many :comments
- has_many :likes
- has_many :has_many :liked_posts, through: :likes, source: :post
- has_many :relationships
- has_many :followings, through: :relationships, source: :follow
- has_many :reverse_of_relationships, class_name: 'Relationhip',foreign_key: 'follow_id'
- has_many :followers, through: :reverse_of_relationships, source: :user


## postsテーブル
|Column|Type|Options|
|------|----|-------|
|title|text|null: false| 
|youtube_url|string|null: false|
|message|text| |
|user_id|integer|null:false|
### Association
- has_many :comments
- has_many :likes
- has_many :liked_posts, through: :likes, source: :user
- has_many :post_genres
- has_many :genres,through::post_genres
- belong_to :user
## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text| |
|image|string| |
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group
