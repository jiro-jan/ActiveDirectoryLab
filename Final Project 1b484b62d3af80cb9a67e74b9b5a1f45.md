# Final Project

**Objective:** Set up a virtual environment and  create three virtual machine:

- One for the Domain Controller with Windows Sever 2022 and hostname DC01
- One for the File Server and hostname FS01
- One for the Client workstation with Windows 10 Pro and hostname PC01

### Create Virtual Machines

1. Create the Domain Controller VM named DC01
    
    ![remmina_myPC_192.168.1.245_20250312-004739.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/71043ce6-f0b5-4fa1-89e8-73915f717e2c.png)
    
2. Create the File Server VM named FS01
    
    ![remmina_myPC_192.168.1.245_20250312-005043.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/e26ae493-6527-46d7-bb98-24e85f523e84.png)
    

1. Create a client workstaion VM wiith Windows 10 Pro named PC01
    
    ![remmina_myPC_192.168.1.245_20250312-005202.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/5c95d563-1b55-49ac-b302-f779678df0e2.png)
    

### Install and Configure Windows Server 2022

**Objective:** Install Windows Server 2022 in the Virtual Machine and perform configurations.

1. Change the server hostname to DC01
    
    ![remmina_myPC_192.168.1.245_20250312-010135.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/80e08808-dfbf-46b5-b361-5b2ac6ca8796.png)
    
2. Connect the Virtual Switch in the Network Adapter settings of Hyper-V Manager.
    
    ![remmina_myPC_192.168.1.245_20250312-010300.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/d0bfd67a-8ce3-443b-8e1f-70418ff279cb.png)
    
3. Check if the DC01 successfully established a connection with the DHCP server and received Network information to use such as the IP address, Subnet Mask, and Default Gateway.
    
    ![remmina_myPC_192.168.1.245_20250312-010337.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/fa5bbe7d-4ef0-408e-8e32-72a6cd496ca7.png)
    
4. Setup a static IPv4 address and test the connectivity again.
    
    ![remmina_myPC_192.168.1.245_20250312-010637.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/108c7734-821f-4282-bc6d-049e2cb0a90e.png)
    
5. Check network connectivity: ensure connectivity between the client and server
    - Login to PC01 and ping DC01
    
    ![remmina_myPC_192.168.1.245_20250312-013154.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/189b4510-e425-4963-b04f-3ca81a817b01.png)
    
6. Enable ICMPv4 in **‘Windows Defender Firewall with Advanced Security’**
    
    ![remmina_myPC_192.168.1.245_20250312-010749.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/07fc7d72-d635-4bde-b6ff-9c721322ef8e.png)
    
7. From PC01 check if the ping is successfull
    
    ![remmina_myPC_192.168.1.245_20250312-013231.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/b2b310b3-5a86-40b8-8b50-475dac3ca0cd.png)
    
8. Turn off **Internet Explore Enhance Security Configuration** and change **Time Zone** to the correct region.
    
    ![remmina_myPC_192.168.1.245_20250312-013724.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/b9fc9d59-90ab-489e-b0a9-6d9cb9fd9eb9.png)
    

## Active Directory Installation and Domain Controller Promotion

**Objective**: Install Active Directory Tools and promote it to Domain Controller.

1. Install Active Directory Domain Services
    
    ![remmina_myPC_192.168.1.245_20250312-014017.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/0bf65cc5-822b-4156-943f-c946e32d93e2.png)
    
2. Promote the server as a Domain Controller
    
    ![remmina_myPC_192.168.1.245_20250312-014726.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/0bfeab30-5fba-458e-bbfc-b45ff9cb53ec.png)
    
3. Setup a new forest as adproject.local
    
    ![remmina_myPC_192.168.1.245_20250312-015001.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/920b12cd-d76d-4dd4-8410-1f2716597801.png)
    
4. Check that there is a green checkmark with a message stating “All prerequisite check passed successfully”.
    
    ![remmina_myPC_192.168.1.245_20250312-015045.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/8e94474f-27fb-4830-bde5-3b807f81d6c0.png)
    
5. After Reboot, login and change the DNS server address of the DC01 to its own IPv4 address.
    
    ![remmina_myPC_192.168.1.245_20250312-015905.png](Final%20Project%201b484b62d3af80cb9a67e74b9b5a1f45/3b5cce4f-f59e-4202-8d0b-986ac5f530c6.png)
    

## Joining File Server and Client to the Domain

Objective: Join FS01 nad DC01 to the domain.

1.