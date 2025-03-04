# Variables
IMAGE_NAME = your_dockerhub_username/container1
TAG = latest

# Build the Docker image
build:
	docker build -t $(IMAGE_NAME):$(TAG) .

# Push the Docker image to Docker Hub
push: build
	docker push $(IMAGE_NAME):$(TAG)

# Clean up local Docker images
clean:
	docker rmi $(IMAGE_NAME):$(TAG)

.PHONY: build push clean