# Docker Hub kullanıcı adınızı buraya girin.
DOCKER_USER := your_dockerhub_username

# Geçerli dizinde Dockerfile içeren tüm dizinleri bulur.
CONTAINERS := $(shell find . -mindepth=1 -maxdepth=1 -type d -exec test -f '{}/Dockerfile' \; -print)

.PHONY: all build push

# Tüm imajları oluştur ve Docker Hub'a gönder.
all: build push

# Her dizindeki Dockerfile'dan imaj oluşturur ve dizin adıyla etiketler.
build:
	@for d in $(CONTAINERS); do \
		image_name=$$(basename $$d); \
		echo "Building image: $(DOCKER_USER)/$$image_name:latest from directory $$d"; \
		# docker build -t $(DOCKER_USER)/$$image_name:latest $$d; \
	done

# Oluşturulan tüm imajları Docker Hub'a gönderir.
push:
	@for d in $(CONTAINERS); do \
		image_name=$$(basename $$d); \
		echo "Pushing image: $(DOCKER_USER)/$$image_name:latest"; \
		docker push $(DOCKER_USER)/$$image_name:latest; \
	done
