FROM node:14

WORKDIR /var/downloads

RUN apt-get update && \
	apt-get install -y \
    # fix "add-apt-repository: command not found"
    ca-certificates \
    # fix "apt-add-repository: not found"
    software-properties-common \
    # fix "[Errno 2] No such file or directory: 'less'" on lambda invoke
    less

# https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install

# https://www.terraform.io/docs/cli/install/apt.html
RUN curl -fsSL https://apt.releases.hashicorp.com/gpg | apt-key add - && \
    apt-add-repository "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com $(lsb_release -cs) main" && \
    apt update && \
    apt install terraform

WORKDIR /var/app

ENTRYPOINT ["bash"]
