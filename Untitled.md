```
name: Deploy to Docker Swarm

on:
  push:
    branches:
      - main

jobs:
  ci:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Install dependencies
        run: |
          npm install

      - name: Lint
        run: |
          npm run lint

      - name: Test
        run: |
          npm run test

      - name: E2E Test
        run: |
          npm run e2e

  deploy:
    runs-on: ubuntu-latest
    needs: ci
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Login to Docker Hub
        uses: docker/login-action@v1
        with:
          username: ${{ secrets.DOCKER_USERNAME }}
          password: ${{ secrets.DOCKER_PASSWORD }}

      - name: Build and push image
        run: |
          docker build -t myapp:latest .
          docker tag myapp:latest ${{ secrets.DOCKER_USERNAME }}/myapp:latest
          docker push ${{ secrets.DOCKER_USERNAME }}/myapp:latest

      - name: Deploy to Docker Swarm
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.SWARM_HOST }}
          username: ${{ secrets.SWARM_USERNAME }}
          password: ${{ secrets.SWARM_PASSWORD }}
          script: |
            docker stack deploy -c docker-compose.yml myapp
```
Для чего здесь используется Deploy to Docker Swarm

Автоматизация обновления образа в Swarm можно осуществить несколькими способами:

1.  **Использование Docker Hub Webhooks:** Docker Hub предоставляет веб-хуки, которые можно использовать для автоматического обновления образа в Swarm при изменении версии образа в Docker Hub.
2.  **Использование CI/CD-пайплайна:** Можно использовать CI/CD-пайплайн для автоматического обновления образа в Swarm при изменении кода. Например, можно использовать Jenkins или GitLab CI/CD для автоматического обновления образа.
3.  **Использование Docker Registry Webhooks:** Docker Registry также предоставляет веб-хуки, которые можно использовать для автоматического обновления образа в Swarm при изменении версии образа в Docker Registry.
4.  **Использование скриптов:** Можно написать скрипт, который будет периодически проверять версию образа в Docker Registry и обновлять образ в Swarm, если версия изменилась.
5.  **Использование Docker Swarm API:** Docker Swarm предоставляет API, который можно использовать для автоматического обновления образа в Swarm. Например, можно использовать команду `docker service update` с опцией `--image` для обновления образа.

Ниже приведен пример скрипта, который можно использовать для автоматического обновления образа в Swarm:

```bash
#!/bin/bash

# Установка адреса Docker Registry
REGISTRY_URL="https://registry.hub.docker.com"

# Установка имени образа
IMAGE_NAME="my-image"

# Установка версии образа
IMAGE_VERSION="latest"

# Проверка версии образа в Docker Registry
LATEST_VERSION=$(curl -s -X GET \
  https://registry.hub.docker.com/v2/repositories/${IMAGE_NAME}/tags/${IMAGE_VERSION} \
  | jq -r '.results[0].name')

# Обновление образа в Swarm, если версия изменилась
if [ "${LATEST_VERSION}" != "${IMAGE_VERSION}" ]; then
  docker service update --image ${REGISTRY_URL}/${IMAGE_NAME}:${LATEST_VERSION} my-service
fi
```

Этот скрипт периодически проверяет версию образа в Docker Registry