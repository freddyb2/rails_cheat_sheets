## Rails useful commands

### Create a model

```sh
Rails generate model some_model
```

It creates: 
- The migration script: `db/migrate/20201123095448_create_some_models.rb`
- The model `SomeModel`: `model/some_model.rb`
- The test of the model
- The factory of the model

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
