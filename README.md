## Kitura Cloud 

Configuration files for creating a Kitura playground on a Digital Ocean
droplet.

Following great instructions on [CocoaDev Central](http://cocoadevcentral.com/d/swift_kitura/), this file is suitable for pasting as 'User Data' while creating a new droplet.

## Pre-requisites
- Digital Ocean account
- Generated SSH key pair for a user you intend to use

## Installation
- Create a new Droplet ([link](https://cloud.digitalocean.com/droplets/new))
- Select 'Ubuntu 15.10 x64'
- Under 'Additional Options', select 'User Data'...
- ...paste the contents of the cloud init file
- ...modify the SSH key for the user you intend to use
- Create the droplet!

## Post-setup
- Once it's created, you can ssh to your instance as kitura@<IP ADDRESS>
- Head to the log directory and tail the installation as it happens
    cd /tmp/log
    tail -f cloud-init-output.log
- You should see things progress normally...
- Once it's successful, follow the instructions on CocoaDev Central:
    cd ~/Kitura
    make
    .build/debug/XCTest.a
- Head to http://IP_ADDRESS:8090 and see your site!


## TODO
- Front the app with nginx
