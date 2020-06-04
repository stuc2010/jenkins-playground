# Jenkins Playground
This repository is to demonstrate skills in Vagrant, Ansible, and Jenkins. It simulates a very simple (and not very secure) build server using Vagrant to supply a Linux Virtual Machine and Ansible to install and configure an HTTP instance of Jenkins and expose it on port 58080 of the host machine.

Whilst it will automatically install Jenkins you will need to follow the post installation steps defined [here](https://www.jenkins.io/doc/book/installing/#setup-wizard) to make use of the server. 

The repository also contains example Jenkins pipelines for:
* C++ (Relies on CMake plugin for Jenkins to be installed)
* NodeJS [TODO]
* Python [TODO]
