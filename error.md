# Vagrant errors

## change host name

On `vagrant up`, got the following error. However, `vagrant status` says both
servers are up, and I can `vagrant ssh` to them.

    Vagrant attempted to execute the capability 'change_host_name'
    on the detect guest OS 'linux', but the guest doesn't
    support that capability. This capability is required for your
    configuration of Vagrant. Please either reconfigure Vagrant to
    avoid this capability or fix the issue by creating the capability.


