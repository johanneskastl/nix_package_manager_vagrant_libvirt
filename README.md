# nix_package_manager_vagrant_libvirt

This Vagrant setup creates a VM and installs the Nix package manager using the
[installer from determinate.systems](https://zero-to-nix.com/start/install).

Default OS is openSUSE Leap 15.5. Although that can be changed in the
Vagrantfile, please beware that this will break the Ansible provisioning.

## Vagrant

1. You need vagrant obviously. And ansible. And git...
1. Fetch the box, per default this is `opensuse/Leap-15.5.x86_64`, using
   `vagrant box add opensuse/Leap-15.5.x86_64`.
1. Make sure the git submodules are fully working by issuing `git submodule init
   && git submodule update`
1. Run `vagrant up`
1. Connect to the VM using SSH via `vagrant ssh`.
1. Run `nix --version`
   ```bash
   $ nix --version
   nix (Nix) 2.18.1
   $
   ```
1. Party!

## Disabling the Ansible provisioning

In case you do not want Ansible to install teleport (because you want to install
it yourself), just comment out the following lines in the `Vagrantfile`:

```hcl
    node.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook-vagrant.yml"
    end # node.vm.provision
```

You also find all of the playbooks in the `ansible` folder.

## License

BSD-3-Clause

## Author Information

I am Johannes Kastl, reachable via git@johannes-kastl.de.
