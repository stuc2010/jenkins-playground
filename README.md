# Jenkins Playground
This repository is to demonstrate skills in Vagrant, Ansible, and Jenkins. It simulates a very simple (and not very secure) build server using Vagrant or Docker Compose to supply a Linux Virtual Machine and Ansible to install and configure an HTTP instance of [Jenkins](http://localhost:58080) and [Artifactory](http://localhost:58082/ui/) and expose them on port 58080 and 58082 of the host machine.

**The Ansible play makes use of Ansible Vault to protect secrets but in the interests of this being a demo which you don't have to contact me about I have included the Vault password file in repository. *Obviously you would never, ever, ever, do this in a real world scenario*.**

To run using Docker Compose (requires Docker to be installed on the host machine) run `docker compose up` from the project root directory.

To run using Vagrant (requires Vagrant and a VM provider to be installed) run `vagrant up` from the project root directory.

## Jenkins
The Vagrant or Docker Compose environments will automatically install Jenkins but you will need to follow the post installation steps defined [here](https://www.jenkins.io/doc/book/installing/#setup-wizard) to make use of the server.

All required plugins are automatically installed although they must be manually configured.

**A future update to this repository will, where possible, automatically configure these plugins.**

## Artifactory
In order to demonstrate the ability to push build files to an artifact repository the OSS version of Artifactory is also deployed alongside Jenkins. It is exposed on port 58082 of the host machine and will need to be configured as per JFrog's [documentation](https://www.jfrog.com/confluence/display/JFROG/Installing+Artifactory#InstallingArtifactory-Post-InstallSteps). The Jenkins Artifactory plugin should also be installed and configured with the server id set to 'ArtifactoryPlayground'.

You will need to configure a generic local repository and a user with rw permissions to that repository in order for the Jenkins pipelines referenced below to work correctly. This username and password should be provided to Jenkins when configuring the Artifactory plugin as per the plugin [documentation](https://www.jfrog.com/confluence/display/RTF/Jenkins+Artifactory+Plug-in).

## Example pipelines
There are companion code repositories which contain example Jenkins pipelines which can be used with this playground. **All examples rely on the relevant pipeline plugins being installed on the Jenkins server.** 

### C++ 
* https://github.com/stuc2010/hellocplusplus

#### Requirements
* CMake Jenkins plugin
* xUnit Jenkins plugin
* Artifactory Jenkins plugin

### NodeJS
* TBC

#### Requirements
N/A

### Python
* TBC

#### Requirements
N/A

## Configuring example pipelines
Each of the projects can be added to Jenkins as a 'Pipeline' item. To test these examples create a 'Pipeline' item in Jenkins as per the instructions below.

1. From the Jenkins 'Dashboard' select 'New Item' from the left hand nav menu

![](images/jenkins-new-item.png)

2. Enter a name for your 'Pipeline', select 'Pipeline' from the list of item types, and then click 'Ok'

![](images/new-item-setup.png)

3. Enter a description for your 'Pipeline', select the 'Discard old builds' checkbox, and set the maximum number of builds to keep to 3. *This will keep the disk usage low, even though the projects are quite small*.

![](images/pipeline-setup-general.png)

4. Under 'Build triggers' select the 'Build periodically' check box and leave blank. *This will mean your build is never triggered but it will still work on demand.*

![](images/pipeline-setup-build-triggers.png)

5. Under 'Pipeline' set your 'Definition' to be 'Pipeline script from SCM'. Then set your 'SCM' to be 'Git', copy the HTTPS clone link for the repo you wish to test, leave all other options as per the default, and save your pipeline

![](images/pipeline-setup-git.png)

6. You can now test your 'Pipeline' by selecting it from the Jenkins 'Dashboard' and clicking 'Build Now' from the left hand nav menu.

![](images/build-now.png)