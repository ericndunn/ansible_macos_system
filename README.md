Jenkins
=========

This role will query Jenkins file system for files by date and size

Assumptions
------------
- ssh key copied to servername as jenkins user
	- ssh-copy-id jenkins@servername

Requirements
------------
- See Assumptions
- Install homebrew
	- https://docs.brew.sh/Installation
- Install ansible
	- brew install ansible
- (OPTIONAL) - Install jenkins-lts
	- brew install jenkins-lts
- Create the following inventory file and place in your local ~/macos_inventory
	
	[JENKINS]
	servername1
	servername2	

Role Variables
--------------
NOTE: All vars can be overdden on commandline or Jenkins

files_path: /Users/jenkins/.jenkins/jobs #Jenkins var {{ lookup('env','FILES_PATH') }}
files_age: 4w  #Jenkins var {{ lookup('env','FILES_AGE') }}
files_size: 100m #Jenkins var {{ lookup('env','FILES_SIZE') }}

Dependencies
------------

- ssh key generated and copied to server as jenkins user
- JDK 1.8 installed as dependency for Jenkins-lts)
  	https://java.com/en/download/help/mac_install.xml

Example Playbook
----------------
- TERMINAL METHOD: cd to dir where ansible_macos.yml is located on local
- ansible-playbook -i macos_inventory --ask-pass ansible_macos.yml 
	NOTE: When prompted, enter ssh keygen password

License
-------

FOSS

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
