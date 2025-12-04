

Every command below except `build` and `run` is executed in a docker container.

### Set Environment Variables

```bash
# Copy service env file
$ cp .env.example .env
# Copy db env file
$ cp .db.env.example .db.env
```

### Build and run the app with Docker Compose

```bash
# Build docker image
$ docker compose build

# Run the app in the background
$ docker compose up -d

# Watch logs
$ docker compose logs -f

# Execute a command in a running container
$ docker compose exec app <command>
```

### Migrate database

**before test or use the app, you need to migrate the database.**

```bash
# init User table
$ docker compose exec app poetry run alembic upgrade head
```

### Test

```bash
# Run unit tests using pytest
$ docker compose exec app poetry run pytest
```

### Lint and format

The Ruff is an extremely fast Python linter and code formatter written in Rust.
It can replace flake8, isort, and black at once.

```bash
# Run Ruff

## Code linting
$ docker compose exec app poetry run ruff check .

## Code formatting
$ docker compose exec app poetry run ruff format .
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE.md) file for details.
