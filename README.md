# ansible-networking
Networking Demos and Tests with Arista vEOS

Testing Ansible etc on a virtual vEOS instance of an Arista swtich. This is done on kvm.

Use the Arista-VEOS.xml and define it on kvm (virsh define Arista-VEOS.xml). You will need to download the Aboot iso and vEOS image from Arista as I cannot distribute that.

Place those images into your /var/lib/libvirt/images folder and correct the file versions in Arista-VEOS if needed. You will need to also change each virtual interface on the vm to point to your network config on kvm. Otherwise your interface/bridge name wont match mine and you will get an error. 

Once the Arista switch is up on kvm - you can login with just using admin as a username. I would recommend you set ip addresses for the management interface:


arista-core1-veos>en

arista-core1-veos#conf t

arista-core1-veos(config)#int management 1

arista-core1-veos(config-if-Ma1)#ip address 192.168.0.200 255.255.255.0

arista-core1-veos(config-if-Ma1)#wr mem

Copy completed successfully.



arista-core1-veos(config-if-Ma1)#sh run int management 1

interface Management1

   ip address 192.168.0.200/24
   
arista-core1-veos(config-if-Ma1)#



Setup a password for login:


arista-core1-veos(config-if-Ma1)#username admin secret password

arista-core1-veos(config)#wr mem

Copy completed successfully.


