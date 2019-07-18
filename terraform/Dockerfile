FROM golang:alpine
MAINTAINER Greg Sharpe <docker+me@gregsharpe.co.uk>

RUN	apk add --no-cache \
	bash \
	zip \
	curl

ENV 	TERRAFORM_VERSION 0.11.12

RUN 	curl -o terraform.zip https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
	unzip terraform.zip && \
	mv terraform /usr/bin && \
	rm terraform.zip

ENTRYPOINT [ "terraform" ]
CMD [ "--help" ]
