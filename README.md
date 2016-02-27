# Dual Deployment example

Disclaimer : No actual services will be deployed in this example.

The Packer template [aws.json](aws.json) is used to build and provision an Amazon Machine Image.  There is no bootstrap.sh or deploy_container.sh scripts provided with this example.

The bootstrap.sh can be as simple or complex as you need it to be.  We use it to install some helper tools and install Docker.

The deploy_container.sh pulls the service container code from github and builds the container images as part of the AMI build.  

The aws.json template supports 6 arguments :

```
    base_image : The AMI ID of the base image you want to build from.
    new_image  : The name of the new AMI you are building.
    access_key : AWS access key 
    secret_key : AWS secret key
    script     : The name of the script you want to run to bootstrap the base image.
    script_args: Pass in additional arguments to the script.
```

Create a Primed Centos 7 AMI which includes container build provisioner :

```
packer build -var 'base_image=ami-c7d092f7' -var 'new_image=CentOS-7-x86_64 (Demo)' -var 'script=bootstrap.sh' -var 'access_key=12345674345456454' -var 'secret_key=erewrwrw2424esfsfdfwrwerwe2423wer' -var 'script_args=' aws.centos.json
```
