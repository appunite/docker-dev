## Development Environment

We use [Docker Compose] to setup a development environment. Here's a typical Phoenix configuration:

`docker-compose.yml`: services we use and link with the app
`Dockerfile.local`: a file to define local environment for our app

Before anything else, install the deps and create the database:

```sh
docker-compose run web mix deps.get
docker-compose run web npm install
docker-compose run web mix ecto.create
docker-compose run web mix ecto.migrate
docker-compose run web mix run priv/repo/seeds.exs
```

Run tests with:

```sh
docker-compose run web mix test
```

Boot the stack with:

```sh
docker-compose up
```

Whenever you make changes to `Dockerfile.local` you'll have rebuild using:

```sh
docker-compose build
```
