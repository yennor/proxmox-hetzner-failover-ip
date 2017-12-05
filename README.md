# proxmox-hetzner-failover-ip
Simple scripts to handle a Proxmox VM Migration and Hetzner ip failover

The files dispatch, failover and monitor are supposed to be in
/etc/failover
.
The failover script is just a copy from the script in the hetzner wiki


The file rc.local in
/etc/

and the host.conf file should be in
/etc/pve/failover

They should have the same name as the Proxmox Vm-Id they represent.
see the example 200.conf


For the whole thing to work you should have a routed network config.
vmbr0 should have the same ip address on all proxmox machines,
otherwise the default gateway out of the VM will not work after migrate.
See example config in wiki: TODO: put wiki url here.