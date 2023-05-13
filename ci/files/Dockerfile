FROM golang:1.20.3-alpine

ARG version

RUN apk add curl unzip docker docker-compose
RUN release=`curl -s https://api.github.com/repos/hashicorp/terraform/releases/latest |  grep tag_name | cut -d: -f2 | tr -d \"\,\v | awk '{$1=$1};1'` \
  && wget https://releases.hashicorp.com/terraform/${release}/terraform_${release}_linux_amd64.zip \
  && unzip terraform_${release}_linux_amd64.zip \
  && mv terraform /usr/bin/terraform

ADD https://github.com/gruntwork-io/terragrunt/releases/download/v${version}/terragrunt_linux_amd64 /usr/local/bin/terragrunt
RUN chmod +x /usr/local/bin/terragrunt
