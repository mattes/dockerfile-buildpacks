all: base build deploy

base:
	docker build -f ../Dockerfile.Base -t rails:base .

build:
	docker build -f ../Dockerfile.Build -t rails:build .

deploy:
	docker build -f ../Dockerfile.Deploy -t rails:deploy .

.PHONY: all base build deploy
