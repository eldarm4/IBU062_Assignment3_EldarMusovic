# IBU062_Assignment3_EldarMusovic
Router0:
    Device Model: 1941
    Hostname: Router


FirstSwitch:
    Device Model: 2960 IOS15
    Hostname: Switch
SecondSwitch:
    Device Model: 2960 IOS15
    Hostname: Switch


Server0:
    Device Model: Server-PT
    IP Address: 168.90.0.3
Server1:
    Device Model: Server-PT
    IP Address: 210.3.14.4
Server2:
    Device Model: Server-PT
    IP Address: 210.3.14.3


PC0:
    Device Model: PC-PT
    IP Address: 168.90.0.2
PC1:
    Device Model: PC-PT
    IP Address: 168.90.0.4
PC2:
    Device Model: PC-PT
    IP Address: 210.3.14.2
PC3:
    Device Model: PC-PT
    IP Address: 168.90.0.6
PC4:
    Device Model: PC-PT
    IP Address: 210.3.14.5
Laptop:
    Device Model: Laptop-PT
    IP Address: 168.90.0.5


DHCP details:

configure terminal                          # Enter global configuration mode.
ip dhcp pool FirstSwitch                    # Create a DHCP pool named "FirstSwitch."
network 168.90.0.0 255.255.0.0             # Specify the network range for the DHCP pool.
default-router 168.90.0.1                  # Set the default gateway for the DHCP pool.
exit                                       # Exit DHCP configuration mode.
configure terminal                          # Enter global configuration mode again.
ip dhcp pool SecondSwitch                   # Create another DHCP pool named "SecondSwitch."
network 210.3.14.0 255.255.255.0           # Specify the network range for this DHCP pool.
default-router 210.3.14.1                  # Set the default gateway for the second DHCP pool.
exit                                       # Exit DHCP configuration mode.
configure terminal                          # Re-enter global configuration mode.
ip dhcp excluded-address 168.90.0.1        # Exclude the default gateway of "FirstSwitch" from the DHCP pool.
ip dhcp excluded-address 210.3.14.1        # Exclude the default gateway of "SecondSwitch" from the DHCP pool.
exit                                       # Exit configuration mode.
configure terminal                          # Enter global configuration mode again.
interface GigabitEthernet0/0                # Select the first interface (GigabitEthernet0/0).
ip address 168.90.0.1 255.255.0.0          # Assign an IP address and subnet mask to the interface.
no shutdown                                # Activate the interface.
interface GigabitEthernet0/1                # Select the second interface (GigabitEthernet0/1).
ip address 210.3.14.1 255.255.255.0        # Assign an IP address and subnet mask to the interface.
no shutdown                                # Activate the interface.
exit                                       # Exit interface configuration mode.