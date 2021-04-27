# Running on Elastic

This project showcase how to use [Elastic APM](https://www.elastic.co/apm).

## Requirements

- Docker >= 19.x.x
- Docker Compose >= 1.25.0

## Build

```bash
$ make docker-build
```

## Run

```bash
$ make docker-start
```

After executing the above commands you can reach the Jenkins coordinator in the following URL:

```
http://localhost:8080
```
