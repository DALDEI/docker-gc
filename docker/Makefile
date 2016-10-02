# Only evaluate shell once
DOCKER_TAG ?=$(shell cat version.txt)
DOCKER_TAG :=${DOCKER_TAG}
DOCKER_REPOSITORY ?=spotify/docker-gc
DOCKER_VERSION ?=$(shell docker version --format="{{.Server.Version}}")
DOCKER_VERSION :=${DOCKER_VERSION}
DOCKER ?= docker 
export DOCKER
export DOCKER_VERSION

	 
.PHONY: all image push

image:
	echo Creating image with docker version: $(DOCKER_VERSION) and tag: $(DOCKER_TAG)
	cp ../docker-gc .
	$(DOCKER) build --build-arg=DOCKER_VERSION=$(DOCKER_VERSION) -t docker-gc:latest \
	-t $(DOCKER_REPOSITORY)-$(DOCKER_VERSION):$(DOCKER_TAG) .

push: image
	echo Pushing image with docker version: $(DOCKER_VERSION) and tag: $(DOCKER_TAG)
	$(DOCKER) push $(DOCKER_REPOSITORY)-$(DOCKER_VERSION):$(DOCKER_TAG)

clean:
	rm -f docker-gc *~
