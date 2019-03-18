Module |labmodule|\, Lab \ |labnum|\: CI/CD with Ansible Tower
==============================================================

Lab scenario:
~~~~~~~~~~~~~

F5 Declarative Onboarding, Application Services 3, and Telemetry Streaming are solutions that function well in within templated environments. The use of single declarative configuration files and idempotent solutions create scenarios where a system can progress from Continious Delivery, to Continious Deployment.

Ansible Tower has been installed into this lab to show the possibility of an orchestration engine with the capabilities for large scale deployments. Tower has many features which will not be covered in this lab, however, two concepts that **are** covered are Projects and Templates.

A Project is a collection of Ansible objects in relation to each other. 

A Template is a subset of project, and Ansible Playbook, which run Role(s) including modules.

The entirety of this lab is created in Source Control, with different tools using different parts; Postman we imported our collection directly from the lab SCM, the documention and configuration examples are all pulled from the same source, giving the purpose as a Source-of-Truth. We are now going to integrate Module5 of this lab into Ansible Tower.

Ansible Tower will read this labs GitHub repository looking for an `ansible.cfg` file, this file will present logical pathings for objects to be used in an Ansible Project.

Task |labmodule|\.\ |labnum|\.1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ansible Tower has been installed and configured ready to be executed.

.. seealso:: Within the Postman Collection for this lab is the Ansible Tower configuration that was used. `Module 5 - CI/CD with Ansible Tower` was used to License and configure Tower objects.

  |image2|

Using `Chrome` open a tab to Ansible Tower.



Directives:

.. Note:: Note
.. Warning:: Warning
.. SeeAlso:: See Also

Image:

  |image1|

URL:

CloudDocs_

.. |labmodule| replace:: 5
.. |labnum| replace:: 1
.. |labdot| replace:: |labmodule|\ .\ |labnum|
.. |labund| replace:: |labmodule|\ _\ |labnum|
.. |labname| replace:: Lab\ |labdot|
.. |labnameund| replace:: Lab\ |labund|

.. |image2| image:: images/image2.png

.. _CloudDocs: https://clouddocs.f5.com