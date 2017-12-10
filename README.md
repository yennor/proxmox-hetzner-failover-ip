# proxmox-hetzner-failover-ip
Simple scripts to handle a Proxmox VM Migration and Hetzner ip failover

The files dispatch, failover and monitor are supposed to be in
/etc/failover
.
The failover script is just a copy from the script in the hetzner wiki


The file rc.local should be in /etc/

and the <vm id>.conf file should be in
/etc/pve/failover

They should have the same name as the Proxmox Vm-Id they represent.
see the example 200.conf


For the whole thing to work you should have a routed network config.
vmbr0 should have the same ip address on all proxmox machines,
otherwise the default gateway out of the VM will not work after migrate.
See example config in wiki: TODO: put wiki url here.

You maybe need to change the name of the nic in the file dispatcher.

-----------

The vm_subnet_change is used inside of VM. It is written for VM which only use ipv6 (there is a ipv4 reverse proxy in front of them).
When the vm migrates obviously also the ipv6 subnet migrates. That script gets exectued, verifies in which subnet it is, and sets the ip address and gateway correctly.
Since we don't support life migration, it is only executed after the network is started. You can easily add it to a cronjob, for live migration.
it also should be easy to extend for ipv4 if wished
