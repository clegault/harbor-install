# harbor-install 
I found this harbor install script on https://gist.github.com/kacole2/95e83ac84fec950b1a70b0853d6594dc referenced from https://goharbor.io/docs/1.10/install-config/quick-install-script/ . It was not working correctly, there were a few corrections in the comments but even those were broken, so I fixed it and uploaded it here.

## Quick Start Installation
Currently tested on Ubuntu 18.04 and 20.04  

Quick installation and running can be done like this:  
```sudo sh -c "$(curl -fsSL https://raw.githubusercontent.com/clegault/harbor-install/master/harbor.sh)"```

If you want to change from IP to FQDN for the installation, comment/uncomment appropriately in the script after downloading it. Make sure to change the permissions to executable first:  
```
curl -O https://raw.githubusercontent.com/clegault/harbor-install/master/harbor.sh  
vim harbor.sh
```
Change this section for your site:  
```
# comment out the section for #IP and uncomment out the section for FQDN to change this to FQDN

IPorFQDN=$(hostname -I|cut -d" " -f 1) #IP
#IPorFQDN=$(hostname -f) #FQDN
```
Then change the execution bit and execute as root:
```
chmod u+x harbor.sh
sudo ./harbor.sh
```

## What it does
Installs Clair and Chart repository service. It does not install Notary which requires HTTPS. The original script would ask if you wanted to set up an FQDN or IP based install, but I defaulted it to IP for a fully automated install and leave you with a way to comment/uncomment to change it to FQDN. You can change this and reconfigure to add HTTPS support and FQDN support following directions from here: https://goharbor.io/docs/1.10/install-config/reconfigure-manage-lifecycle/
