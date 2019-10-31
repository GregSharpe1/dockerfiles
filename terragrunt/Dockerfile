FROM alpine:3.10
MAINTAINER Greg Sharpe <docker+me@gregsharpe.co.uk>

RUN	apk add --no-cache \
	bash \
	zip \
	curl

ARG TERRAFORM_VERSION
ARG TERRAGRUNT_VERSION

RUN 	curl -o terraform.zip https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
	unzip terraform.zip && \
	mv terraform /usr/bin && \
	rm terraform.zip

RUN	curl -sS -L https://github.com/gruntwork-io/terragrunt/releases/download/v${TERRAGRUNT_VERSION}/terragrunt_linux_amd64 -o /usr/bin/terragrunt && \
	chmod +x /usr/bin/terragrunt

ENTRYPOINT [ "terragrunt" ]
CMD [ "--help" ]
