# **Nginx deployment steps**

## Run vagrant destroy to get rid of the current virtual machine

Delete any existing vagrant run Virtual Machines using:
    
    vagrant destroy

## Run vagrant up to make a new one (note, it will use the new i.p line we added so no need to add that later).

Create the vagrant script with command:
    
    vagrant init

A new file will appear in the repo. with the following script:

    Vagrant.configure("2") do |config|

        config.vm.box = "base"
 
    end

Amend the operating system configuration:

    Vagrant.configure("2") do |config|

        config.vm.box = "ubuntu/xenial64"

    end

Run the Virtual Machine with:

    vagrant up

## Vagrant ssh to go into the VM in the terminal

Connecting to the Virtual Machine through ssh:

    vagrant ssh

## Update and upgrade packages

Update the packages manager:

    sudo apt-get update


Upgrade the packages manager:

    sudo apt-get upgrade -y

Note:
- **sudo**: Super User DO, grants temporary privileged access.
- **apt-get**: Command-line tool for handling packages.
- **-y**: Defaults as yes when permission is required.
- **update**: Updates available packages and their versions, but it does not install or upgrade any packages.
- **upgrade**: Installs newer versions of the packages you have. 

_After updating the lists, the package manager knows about available updates for the software you have installed. This is why you first want to update._

## Install nginx

Install nginx package:

    sudo apt-get install nginx -y

## Start nginx

Start the nginx web server using:

    sudo systemctl start nginx

Additionally, check the status of the web server using:

    sudo systemctl status nginx

## Access the nginx web server at 192.168.10.100 in a web browser

Amend the original vagrant file to include the network configuration.

Add the network configuration to allow access to the VM:

    Vagrant.configure("2") do |config|

        config.vm.box = "ubuntu/xenial64"
        config.vm.network "private_network", ip:"192.168.10.100"

    end

Restart the VM through firstly logging out with:

    exit

Followed by a restart command:

    vagrant reload

Finally, access the web server through a browser with URL:

    192.168.10.100

## Stop vagrant

Stop vagrant safely using:

    vagrant halt
