FROM alpine:3.10
MAINTAINER Greg Sharpe <docker+me@gregsharpe.co.uk>

RUN	apk add --no-cache \
	bash \
	zip \
	curl

ARG TERRAFORM_VERSION

RUN 	curl -o terraform.zip https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
	unzip terraform.zip && \
	mv terraform /usr/bin && \
	rm terraform.zip

ENTRYPOINT [ "terraform" ]
CMD [ "--help" ]
