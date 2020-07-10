# Image Factory

Mantoso Image Factory is a project to build OS Images that are used with different hypervisor providers. It is the foundation for all images used in development and with cloud providers.

## At a Glance

### Operating Systems

- CentOS 8

### Builders

- proxmox
- virtualbox-iso

### Provisoners

- Ansible
- Shell-local

### Post Processors

- vagrant
- vagrant-cloud
- proxmox
- aws

## Requirements


### Vagrant Cloud

To upload images to [Vagrant Cloud](https://app.vagrantup.com), you will need to create a personal account. Once you do that, you will need to [create a new Organization](https://app.vagrantup.com/mantoso/boxes/centos-8).

#### Create New Box

- Once logged in, navigate to your [Dashboard](https://app.vagrantup.com) and click on [New Vagrant Box](https://app.vagrantup.com/boxes/new).
- Choose the org to put it under, a name and description. This will be the URL that your images will be hosted under. For example https://app.vagrantup.com/mantoso/boxes/centos-8 will host all CentOS 8 images, with versions being hosted under it.

## Cleaning Images

```shell script
virt-sysprep -d centos
```

## Extract /proc/cmdine variables

TO make variables available via kickstart and preseed, we need to extract variables with a prefix from `/proc/cmdline`.

```shell script
%pre%
cat /proc/cmdline | grep -o '\bIMAGE_BUILDER__[^ ]*' | sed -e 's/^/export /g > /tmp/image_builder.sh
source /tmp/image_builder.sh
%end%
```
