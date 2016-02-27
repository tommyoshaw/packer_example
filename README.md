# Dual Deployment example

Disclaimer : No actual services will be deployed in this example.

The Packer template [aws.json](aws.json) is used to build and provision an Amazon Machine Image.  There is no bootstrap.sh provided with this example.  

The aws.json template supports 4 arguments :

```
    base_image : The AMI ID of the base image you want to build from.
    new_image : The name of the new AMI you are building.
    script : The name of the script you want to run to bootstrap the base image.
    script_args : Pass in additional arguments to the script.
```

Create a Primed Centos 7 AMI which includes container build provisioner :

```
packer build -var 'base_image=ami-c7d092f7' -var 'new_image=CentOS-7-x86_64 (Demo)' -var 'script=bootstrap.sh' -var 'script_args=' aws.centos.json
```
