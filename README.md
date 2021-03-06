# Clearwater Heat Templates

This repository contains templates for use with [OpenStack Heat](https://wiki.openstack.org/wiki/Heat) to deploy [Project Clearwater](http://www.projectclearwater.org).

`clearwater.yaml` is the top-level template, and depends on the other templates to create a network and Clearwater servers.
local_config is written in each node's yaml file. And the shared_config is in the yaml file of ellis node.

To use them, you must

-   have an [Ubuntu 14.04 cloud image](http://cloud-images.ubuntu.com/trusty/current/) imported into your OpenStack deployment
-   identify the external network in OpenStack that Clearwater should hang off, and find its network ID
-   create a DNS private key by running `head -c 64 /dev/random | base64 -w 0`
-   create the stack by running `heat stack-create clearwater -f clearwater.yaml -P "public_mgmt_net_id=...;public_sig_net_id=...;dnssec_key=..."`.

For further options, see the definition of the `parameters` block in `clearwater.yaml`.
For example, if you want to change the url of repository, change the repo_url in the clearwater.yaml.
