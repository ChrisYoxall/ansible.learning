# A dockerfile to build an image with Ansible so that I don't need to install it on my computer

FROM ubuntu:jammy

# The zsh, curl & git packages are required for 'Oh My zsh'
RUN apt-get update && apt-get install python3 python3-pip zsh curl git \
    # Install ssh & sshpass for password ssh connection with ansible
    ssh sshpass \
    -y --no-install-recommends

# Install the AZ CLI. Refer https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-linux
RUN curl -sL https://aka.ms/InstallAzureCLIDeb | bash

# Install 'Oh My zsh'. Refer https://github.com/deluan/zsh-in-docker
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

WORKDIR /root

# Install ansible. The recommended way is to use a python virtual environment, but since we are in a 
# container there is no need
RUN pip3 install --no-cache-dir ansible

ENTRYPOINT ["/bin/zsh"]


# Run container by doing something like: docker run -it --rm my-ansible:1.0.0
#
# To run and mount a folder with playbooks: docker run -it --rm -v /home/chris/code/ansible.learning:/root/code my-ansible:1.0.0

