## Kitura Cloud 

Configuration files for creating a Kitura playground on a Digital Ocean droplet (*2016/02/23*)

Following great instructions on [CocoaDev Central](http://cocoadevcentral.com/d/swift_kitura/), this file is suitable for pasting as 'User Data' while creating a new droplet.

## Pre-requisites
- Digital Ocean account
- Generated SSH key pair for a user you intend to use

## Differences
- This recipe installs swift into the system at /usr/local
- A link to /usr/local/swift points to the installed dev kit
- Firewall rules defined as iptables
- Creates a 'kitura' unix user by default

## Setup
- Create a new Droplet ([link](https://cloud.digitalocean.com/droplets/new))
- Select 'Ubuntu 15.10 x64'
- Under 'Additional Options', select 'User Data', which opens up a text box
  - paste the contents of the cloud init file in this repo
  - be sure to add your public SSH key, replacing "`INSERT_SSH_PUBLIC_KEY`"
- Don't forget to name your droplet!

## Post-setup
- As the instance is being created, ssh to your instance as kitura@[IP ADDRESS]
- Tail the installation; eventually you should see something similar to the following:

        tail -f /tmp/log/cloud-init-output.log
        ...
        Cloning into '/home/kitura/Kitura'...
        Cloud-init v. 0.7.7 running 'modules:final' at Wed, 24 Feb 2016 05:10:52 +0000. Up 69.28 seconds.
        Cloud-init v. 0.7.7 finished at Wed, 24 Feb 2016 05:12:47 +0000. Datasource DataSourceDigitalOcean.  Up 184.00 seconds

- To build Kitura, follow the remaining instructions on [CocoaDev Central](http://cocoadevcentral.com/d/swift_kitura/#toc_11)

        cd ~/Kitura
        make
        .build/debug/XCTest.a
    
- Verify the site is up at http://IP_ADDRESS:8090


## TODO
- Front the app with nginx
- Create a better place for Kitura app to be deployed to than /home/kitura
