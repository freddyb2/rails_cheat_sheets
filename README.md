## Rails useful commands

### Solve gem issues

Check brew:
```
brew cleanup
brew update-reset
brew doctor
```

With gemset:
```
rm -rf /Users/<user>/.gem
rm -rf /usr/local/Homebrew/Library/Homebrew/vendor/bundle/ruby/2.6.0/gems/*

rvm gemset empty
gem install bundler
bundle install
```

### Create a model

```sh
rails generate model some_model
```

It creates: 
- The migration script: `db/migrate/20201123095448_create_some_models.rb`
- The model `SomeModel`: `model/some_model.rb`
- The test of the model
- The factory of the model

### Generate a migration

```sh
rails generate migration FixSomething
```

## ActiveRecord migrations tips

### Create a column with 'now' as default value

```ruby
class CreatePosts < ActiveRecord::Migration[5.0]
  def change
    create_table :posts do |t|
      t.datetime :modified_at, default: -> { 'CURRENT_TIMESTAMP' }
      t.timestamps
    end
  end 
end
```

### Resolve conflits on `db/structure.sql`

```sh
git checkout $(git merge-base origin/master HEAD) -- db/structure.sql
bundle exec rails db:drop db:create db:structure:load db:migrate db:seed
git add db/structure.sql
git commit -m "resolve conflicts with db/structure.sql"
git push
```
