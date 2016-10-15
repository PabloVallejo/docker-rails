# Rails 5 Docker boilerplate

Boilerplate for Rails projects using Docker.


## Building the project

Run the following command to create a new Rails project scaffold with a postgres database.

```bash
docker-compose run web rails new . --force --database=postgresql --skip-bundle
```

In order to have a JavaScript runtime you have to uncomment this line in your Gemfile.
```
gem 'therubyracer', platforms: :ruby
```

After that build the project in order to install new Gems.

```bash
docker-compose build
```

## Database

Use the following configuration for your **development** and **test** databases.

```yaml
development: &default
  adapter: postgresql
  encoding: unicode
  database: postgres
  pool: 5
  username: postgres
  password:
  host: db

test:
  <<: *default
  database: myapp_test
```

After this you can run the project and get ready to create the database.

```bash
$ docker-compose up
```

Run this command to create the database.

```bash
$ docker-compose run web rake db:create
```

## Running

At this point your application must be running on localhost on port 3000, so head over to it and take a look!

[http://localhost:3000](http://localhost:3000)
