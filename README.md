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
# models/user.rb

class User < ActiveRecord::Base
	
	def watch_list_items
		WatchListItem.where(user_id: self.id)
	end

	def watch_list_movies
		watch_list_items.map do |wli|
			Movie.find(wli.movie_id)
		end
	end

end
```

```ruby
# models/watch_list_item.rb

class WatchListItem < ActiveRecord::Base

	belongs_to :movie
	belongs_to :user

	# those macros above replace the methods below
	# and it probably creates more methods!?

	# def movie
	# 	Movie.find_by(id: self.movie_id)
	# end

	# def user
	# 	User.find_by(id: self.user_id)
	# end

end
```
