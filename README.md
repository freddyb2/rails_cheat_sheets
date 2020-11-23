# Rails useful commands

## Create a model

```sh
Rails generate model some_model
```

It creates: 
- The migration script: `db/migrate/20201123095448_create_some_models.rb`
- The model `SomeModel`: `model/some_model.rb`
- The test of the model
- The factory of the model
