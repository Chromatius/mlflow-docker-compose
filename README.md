# Configuration Example

You can quickly setup your MLflow environment with this example.

## Quickstart

The MLFlow Tracking server does not out of the box support artifact storage on the remote server itself, and using S3 as the backend is not in scope here.
The solution then is to store the artifacts locally where the ``mlflow`` client is run, and mount those to the Tracking Server with Docker.
From there, the Tracking server can pick up the artifacts.

One tricky thing to keep in mind is that the ``mlflow.create_experiment()`` methods set the artifact storage location, and this applies
both to the client and the tracking server. Therefore the path to the artifacts have to be the same on both client and server side.

1. Get your mlflow server up and running. This takes time.

    ```sh
    docker-compose up --build -d
    ```

2. Confirm your server is running properly.

    Open server URI. By default it's `http://localhost:5000/`.

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
