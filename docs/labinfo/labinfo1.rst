Lab Information
===============

Access into the lab environment and all work are through the **Windows Server 2016** jump host provided. 

.. Warning:: You need to have outbound access from your system allowing Microsoft Remote Desktop Protocol.

Lab Topology
------------

- 1 x Windows Jumphost
- 1 x Ansible Tower
- 1 x Ubuntu Server
    - LAMP
    - Radius
    - RDP
    - Docker
        - DVWA
        - Hack-a-Zon
        - f5 http demo
        - wurstmeister Kafka/zookeeper
- 2 x BIG-IP
- 1 x BIG-IQ Centralized Manager
- 1 x BIG-IQ Data Collection Device (future use)

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

   * - Win 7 Jumphost
     - DHCP
     - **External:** 10.1.10.3
     - student/automation

   * - Ubuntu 18.04 Server
     - 10.1.1.5
     - **External:** 10.1.10.5
       **Internal:** 10.1.20.5
     - f5student/purple123

   * - Ansible Tower
     - 10.1.1.12
     - **External:** NA
       **Internal:** NA
     - admin/admin

   * - BIGIQ v6.1 CM
     - 10.1.1.4
     - **External:** 10.1.10.4
       **Internal:** 10.1.20.4
     - admin/purple123

   * - BIGIQ v6.1 DCD
     - 10.1.1.6
     - **External:** 10.1.10.6
       **Internal:** 10.1.20.6
     - admin/purple123

   * - BIGIP01 v13.1
     - 10.1.1.8
     - **External:** 10.1.10.8
       **Internal:** 10.1.20.8
       **External Float** 10.1.10.11
       **Internal Float** 10.1.20.11
     - admin/admin
       root/default

   * - BIGIP02 v13.1
     - 10.1.1.10
     - **External:** 10.1.10.10
       **Internal:** 10.1.20.10
       **External Float** 10.1.10.11
       **Internal Float** 10.1.20.11
     - admin/admin
       root/default

.. Note:: In order for Postman to store objects dynamically f5-postman-workflows_ have been installed on the jumphost, this is an extension to Postman utilizing `Tests` objects.

.. Note:: The Automation Toolchain packages have been downloaded and stored in the jump host, this is done to reduce the time to deployment.

.. |labmodule| replace:: labinfo
.. |labnum| replace:: 1
.. |labdot| replace:: |labmodule|\ .\ |labnum|
.. |labund| replace:: |labmodule|\ _\ |labnum|
.. |labname| replace:: Lab\ |labdot|
.. |labnameund| replace:: Lab\ |labund|

.. |image1| image:: images/image1.png

.. _f5-postman-workflows: https://github.com/0xHiteshPatel/f5-postman-workflows