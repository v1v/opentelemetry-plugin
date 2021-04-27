LOG_LEVEL ?= WARNING
.DEFAULT_GOAL := help

.PHONY: docker-build
docker-build:  ## Build the jenkins image
	@env \
		docker-compose \
			--log-level ${LOG_LEVEL} \
			--file docker/docker-compose.yml \
			build --no-cache

.PHONY: docker-clean
docker-clean:  ## Reset the environment; stop Jenkins
	@env \
		docker-compose \
			--log-level ${LOG_LEVEL} \
			--file docker/docker-compose.yml \
			down --volumes

.PHONY: docker-pull
docker-pull:  ## Pull required images
	@env \
		docker-compose \
			--log-level ${LOG_LEVEL} \
			--file docker/docker-compose.yml \
			pull $${SERVICE}

# Start the local environment
.PHONY: docker-up
docker-up:
	@env \
		docker-compose \
			--log-level ${LOG_LEVEL} \
			--file docker/docker-compose.yml \
			up --detach --no-recreate

.PHONY: docker-start
docker-start:  ## Start the local Jenkins coordinator and Elastic Stack
docker-start: docker-up
	@>&2 printf '\n'
	@>&2 printf 'Jenkins coordinator now running at http://localhost:8080\n'
	@>&2 printf 'Kibana now running at http://localhost:5601\n'

.PHONY: help
help:  ## Show this help message
	@awk 'BEGIN {FS = ":.*##"; printf "Usage: make \033[36m<target>\033[0m\n\nTargets:\n"} /^[a-zA-Z_-]+:.*?##/ { printf "  \033[36m%-10s\033[0m %s\n", $$1, $$2 }' $(MAKEFILE_LIST)
