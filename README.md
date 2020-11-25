# Configuration Example

You can quickly setup your MLflow environment with this example.

## Quickstart


2. Make a folder to store artifacts.

    Edit `.env` if you want to change folder, it's `/tmp/artifacts` by default.

    ```sh
    mkdir /tmp/artifacts
    ```

3. Get your mlflow server up and running. This takes time.

    ```sh
    docker-compose up --build -d
    ```

4. Confirm your server is running properly.

    Open server URI. By default it's `http://localhost:5000/`.

## Basic design

- User ID/password are basically fixed, these are used only for postgresql.
- Port is set to 5000 by default.
- Artifact folder is a little tricky, it has to be the same pathname in the local environment and in the server running on docker. So it's set to `/tmp/artifacts` by default.

## Troubleshooting

Stop containers first.

```sh
docker-compose down
```

See what's happening by running without as detached `-d`.

```sh
docker-compose up
```

## Cleaning docker-created-files

Followings will clean up both containers/images.

```sh
docker ps -aq |xargs docker rm
docker images -aq |xargs docker rmi
```

Following will clean up cache.

```sh
docker system prune -a
```
