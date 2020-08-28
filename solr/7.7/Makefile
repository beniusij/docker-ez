.PHONY: build

build:
	docker build -t ez-solr:7.7-latest .

tag-and-push:
	docker tag ez-solr:7.7-latest 429776178057.dkr.ecr.eu-west-1.amazonaws.com/ez-solr:7.7-latest
	docker push 429776178057.dkr.ecr.eu-west-1.amazonaws.com/ez-solr:7.7-latest