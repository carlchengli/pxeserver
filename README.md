## Deploy a pxe server via ansible

### How to use it

This works with virtualbox/vagrant.

1. Clone the project code.
   ```
   git clone     https://github.com/carlchengli/pxeserver.git
   ```
1. Set the pxeserver ip by editing Vagrantfile. For example, to make pxeserver ip 192.168.50.3
   ```
     config.vm.network "private_network", ip:  "192.168.50.3", virtualbox__intnet: "pxenet"
   ```
1. Set the pxeserver ip and dhcp ip range for ansible deployment. To edit `roles/pxeserver/defaults/main.yaml`
   **NOTE**: the pxe_server_ip shold be the same with the ip set in previous step.
1. Run `vagrant up` in the project root directory.
1. After vagrant running, the pxe server will be up. We can boot a virtualbox vm via pxe. To boot a vm via pxe in virtualbox:
   1. Create a vm with a nic of `internal network` mode. And select the network name `pxenet`
   1. Boot the vm and press F12, then press `L` to boot from network.
