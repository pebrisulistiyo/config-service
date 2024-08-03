![Commit Stage](https://github.com/pebrisulistiyo/config-service/actions/workflows/commit-stage.yml/badge.svg)
# config-service

### Run apps with Docker
Build Image Project
```shell
docker build -t config-service .
```

Run Docker Service for Config Project
```shell
docker run -d \
  --name config-service \
  --net catalog-network \
  -p 8888:8888 \
  config-service
```


Build Image with buildpack and automatic push it to registry
```shell
./mvnw spring-boot:build-image \
  -Ddocker.publishRegistry.username=<username> \
  -Ddocker.publishRegistry.password=<token> \
  -Ddocker.publishRegistry.url=ghcr.io \
  -Dspring-boot.build-image.publish=true \
  -Dspring-boot.build-image.imageName=ghcr.io/<username>/config-service:0.0.1
```
Build Image Local
```shell
./mvnw spring-boot:build-image -DskipTests -Dspring-boot.build-image.imageName=config-service
```
Load Image to Minikube◊
```shell
minikube image load config-service --profile books
```
### Run Project
Run project with specific profile
```shell
./mvnw spring-boot:run -Dspring-boot.run.arguments="--spring.profiles.active=dev"
```

### List port
```shell 
lsof -i :9001
```