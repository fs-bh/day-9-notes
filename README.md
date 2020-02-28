# day-9-notes

```ruby
class CreateMovies < ActiveRecord::Migration[5.2]
	def change
		create_table :movies do |t|
			t.string		:name
			t.integer		:year
			t.integer		:genre_id, foreign_key: true
			t.timestamps
		end
	end
end
```

```ruby
class CreateWatchListItems < ActiveRecord::Migration[5.2]
	def change
		create_table :watch_list_items do |t|
			t.integer		:movie_id
			t.integer		:user_id
			t.timestamps
		end
	end
end
```

```ruby
class Movie < 
end
```
