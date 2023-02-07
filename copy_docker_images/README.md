# Copy docker images from local to a remote system

You may need to set up a remote system but don't want to use that system to explicitly login to a docker registry to pull the images down due to security concerns. This will pull images down on your local system them, export them, transfer these to the remote system and import them into the local docker registry.

There are 2 playbooks here:

- 10-install-docker.yaml
- 20-copy-images.yaml




`install-docker` can be used to install docker on the remote system.

`copy-images` will perform the pull, transfer, import of specific images.

## configuration

You need to :

1. update hosts.yaml to point to the remote system, it needs to use root to install docker. If you aren't installing docker then you can use a non-root user. If you use ssh password authentication as shown in the hosts.yaml example, then you need to install `sshpass`, eg `sudo apt install -y sshpass`

2. copy all-tpl.yaml to all.yaml and fill out the fields, but don't touch the `image_prefix_list` field.

