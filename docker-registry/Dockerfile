FROM registry:latest

ADD config.yml /docker-registry/config/config.yml

ENV DOCKER_REGISTRY_CONFIG /docker-registry/config/config.yml
ENV SETTINGS_FLAVOR=prod
ENV SEARCH_BACKEND=sqlalchemy
ENV CACHE_LRU_REDIS_HOST=registry-redis
ENV CACHE_LRU_REDIS_PORT=6379
