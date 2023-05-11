To automate the nginx setup using vagrant, follow the steps below:

1. Ensure all vagrant run Virtual Machines are off; log out of the webserver using `exit`.

2. Safely turn off the Virtual Machine with `vagrant halt`.

3. Navigate back to the original vagrant file and add `config.vm.provision "shell", path: "provision.sh"`, the vagrant script should now look like the following:

```ruby
Vagrant.configure("2") do |config|

  # configures the VM settings
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "private_network", ip:"192.168.10.100"

  # provision the VM to have nginx
  config.vm.provision "shell", path: "provision.sh"

end
```

4. Create a new file within the same repo. and name it `provision.sh`; enter the following commands to be executed after turning on the Virtual Machine.

```gitbash
#!/bin/bash

sudo apt-get update -y

sudo apt-get upgrade -y

sudo apt-get install nginx -y

sudo systemctl start nginx
```

5. Now test test the Virtual Machine can run using `vagrant up`

6. Finally connect to the Virtual Machine with `vagrant ssh`.