Lab Information
===============

Access into the lab environment and all work are through the **Windows Server 2016** jump host provided. 

.. Warning:: You need to have outbound access from your system allowing Microsoft Remote Desktop Protocol.

Lab Topology
------------

- 1 x Windows Jumphost
- 1 x Ubuntu Server
    - LAMP
    - Radius
    - RDP
    - Docker
        - Ansible Tower
        - Hack-a-Zon
        - f5 http demo
- 2 x BIG-IP
- 1 x BIG-IQ Centralized Manager
- 1 x BIG-IQ Data Collection Device
- 1 x VMware ESXi
    - vCenter

Network Addressing
------------------

The following table lists VLANS, IP Addresses and Credentials for all
components:

.. list-table:: Lab Components
   :widths: 15 30 30 30
   :header-rows: 1
   :stub-columns: 1

   * - **Component**
     - **Management IP**
     - **VLAN/IP Address(es)**
     - **Credentials**

   * - Windows 2016 Server
     - DHCP
     - **Internal:** NA
     - Administrator/F5d3mo

   * - Ubuntu 18.04 Server
     - 10.1.1.5
     - **Internal:** 10.1.10.5
       **External:** 10.1.20.5
     - f5student/purple123

   * - ESXi 6.5.0 + vCenter
     - 10.1.1.9
     - **Internal:** 10.1.10.9
       **External:** 10.1.20.9
     - Administrator@vsphere.local/Purpl3$lab
       root/Purpl3$lab

   * - BIGIQ v6.1 CM
     - 10.1.1.4
     - **Internal:** 10.1.10.4
       **External:** 10.1.20.4
     - admin/purple123

   * - BIGIQ v6.1 DCD
     - 10.1.1.6
     - **Internal:** 10.1.10.6
       **External:** 10.1.20.6
     - admin/purple123

   * - BIGIP01 v13.1
     - 10.1.1.8
     - **Internal:** 10.1.10.8
       **External:** 10.1.20.8
       **External Float** 10.1.20.11
     - admin/admin
       root/default

   * - BIGIP02 v13.1
     - 10.1.1.10
     - **Internal:** 10.1.10.10
       **External:** 10.1.20.10
       **External Float** 10.1.20.11
     - admin/admin
       root/default

.. toctree::
   :maxdepth: 2
   :glob:

.. |image1| image:: images/image1.png