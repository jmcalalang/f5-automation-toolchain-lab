Module |labmodule|\, Lab \ |labnum|\: Ansible Galaxy Role to install the Automation Toolchain
=============================================================================================

Lab scenario:
~~~~~~~~~~~~~

|image2| Ansible Galaxy

In Modules 2-4 we installed our F5 Automation Toolchain objects through a Postman upload and initiation sequence. In Module 5 we run the `full_build.yml` playbook, which executes the roles needed to send our declarations for all three of the Automation Toolchains (AS3, DO, and TS), it however does not import and install the packages.

F5 has created an Ansible Galaxy Role to download, install, and if needed remove the packages, making the system ready to accept configuration declarations.

Task |labmodule|\.\ |labnum|\.1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



.. |labmodule| replace:: 6
.. |labnum| replace:: 1
.. |labdot| replace:: |labmodule|\ .\ |labnum|
.. |labund| replace:: |labmodule|\ _\ |labnum|
.. |labname| replace:: Lab\ |labdot|
.. |labnameund| replace:: Lab\ |labund|

.. |image2| image:: images/image2.png
   :width: 200px