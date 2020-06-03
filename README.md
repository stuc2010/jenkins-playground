# C++ Builder
This repository is to demonstrate skills in Vagrant, Ansible, and Jenkins. It simulates a very simple (and not very secure) C++ build server using Vagrant to supply a Linux Virtual Machine and Ansible to install and configure an HTTP instance of Jenkins and expose it on port 58080 of the host machine.

Whilst it will automatically install Jenkins you will need to follow the post installation steps defined [here](https://www.jenkins.io/doc/book/installing/#setup-wizard) to make use of the server. 

The repository also contains a simple example Jenkins job which can:
1. Pull a C++ code repository on GitHub
2. Run the required unit tests
3. Compile and package the code
4. Publish (or simulate a publish) to an artefact repository

## TODO
- [x] Add Vagrant file for relevant base OS image
- [x] Add Ansible play for configuring server and [installing Docker-CE](https://docs.docker.com/engine/install/centos/)
- [x] Install Jenkins as a container per instructions [here](https://www.jenkins.io/doc/book/installing/#docker)
- [ ] Research C++ build requirements
- [ ] Update Ansible play to allow for C++ build requirements
- [ ] Write simple C++ code and unit tests
- [ ] Update Ansible play to include dependencies to build C++ code and run unit tests
- [ ] Write Jenkins job to pull code, execute unit tests, and compile code
- [ ] Research if Artifactory has a free version or there is an equivalent tool I could run
- [ ] Update Jenkins job to publish code to artefact repository