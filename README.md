# vlan
Bash script to create and manage vlan network devices in Linux

~~~
Usage: vlan [show|add|del|mod] --vlan n interface.vlan [ip address|dhcp]
        show    show the current state of the interface (similar to ip addr, but more succinct)
                if interface is omitted, will list all
        add     add a new vlan interface called interface.vlan
        del     delete the vlan called interface.vlan

        options
                -v              show more information
                -e              show commands to run, don't run them
                --help          show this help
                --base iface    use iface as the base interface (rather than beginning of interface.vlan)
                --vlan n        use n as the vlan number (rathern than the end of interface.vlan)

        This script uses the following commands (replace BASE IFACE VLAN A.B.C.D/MASK):
                ip link add link BASE.IFACE name IFACE type vlan id VLAN        # create new link
                ip link delete IFACE                                            # delete interface
                ip addr add A.B.C.D/MASK dev IFACE                              # assign ip address
                ip addr del A.B.C.D/MASK dev IFACE                              # delete ip address
                ip link set dev IFACE [up|down]                                 # bring iface up/down
                ip route add A.B.C.D/MASK [via A.B.C.D|dev IFACE]               # add a route
                dhclient IFACE                                                  # initiate dhcp discovery
~~~
