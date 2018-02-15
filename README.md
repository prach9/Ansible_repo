***Tools used:***

1)Vagrant	  
2)Ansible  
3)Virtualbox  
4)Python  
5)Flask

OS : ubuntu

***Info:***

The script starts with VagrantFile which is used to build VM with Docker.

Ansible is used to build three containers one for flask,one for mysql db and one for sql data volume.

Once vagrant creates VM we should be able to access the VM via browser and we should be able to see conection estalished between flask container and mysql container.

***Script workflow:***

  The script is divided into several parts as described:

  **data:**
	  Contains a Dockerfile which is reponsible for building a data volume container.

  **database:**
	  Handles roles required for sql and sql configuration

  **web:**
	  Install all dependencies for flask and, copies the template which would be displayed in the browser.

  **VagrantFile:**
	  Creates a VM on virtualbox with name docker.dev and calls the ansible playbook

  **dockerfile.yml:**
    This creates 3 containers for flask,data and SQL.

  **setup.yml:**
	   Installation of docker python library along with vagrant user creation.  
	**requirements.yml:**
	   Enables us to install the docker ubuntu role,Which can be achieved in two ways:  
		 1)After the repo is cloned locally run:   
         
       'ansible-galaxy install -r requirements.yml'
     
     2)Sometimes we may face issues while doing the above step, in that case we Can manually get the role as follows:
                    
        'apt-get update
         apt-get install git python-yaml python-jinja2 python-pycurl
         git clone https://github.com/ansible/ansible.git
         cd ansible
         source ./hacking/env-setup
         ansible-galaxy install angstwad.docker_ubuntu'

Once the setup is up simply run the command:

'vagrant up'

This would create our env then we can connect to host at port 80 and our template is loaded.
