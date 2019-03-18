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

Ansible Tower User: ``admin``
Ansible Tower Password: ``admin``

  |image3|

Task |labmodule|\.\ |labnum|\.2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Making sure Ansible Tower has the current source code.

.. note: Ansible Tower version is `Tower 3.4.2` Ansible Version is `Ansible 2.7.9`.

Navigate to `Projects`.

  |image4|

Navigate to the `f5_automation_toolchain_project`.

  |image5|

The project will pull in its configuration from GitHub, the `SCM URL` is the repository containing all our lab. The other Update settings that are in use are because we use template created objects (jinja2 files) which we want cleared out on an update to not cause any overlapping issues.

  |image6|

The repository for this lab is public, ansible.cfg instructs Ansible Tower where it need to lookup Ansible specific object (Roles and Playbooks)

  |image7|

Return to the `Projects` Tab. We need to update our Ansible Tower from Source Control, as our source goes through changes we want to make sure whatever we are working with is the most current.

``Update`` from source by clicking on the loop icon. 

  |image8|

This will trigger an Ansible Tower `Job` to go get the current configuration. This is viewed in `Jobs` and tagged as an `SCM Update`.

  |image9|

Navigating into the Job exposes the tasks and console of how the job preformed.

  |image10|

Task |labmodule|\.\ |labnum|\.3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Executing a pipeline for BIG-IP configuration as code.

Navigate to `Templates`.

  |image11|

Navigate to the `f5_automation_toolchain_template`.

The Template is wrapped around our Project created previously, within the Template is where we organize and set the resources we want executes.

In this Template we are going to use:
- Our Project imported from SCM `f5_automation_toolchain_project`
- Our Inventory (localhost) as our Ansible target
- A playbook located at `docs/module5/ansible/playbooks/full_build.yml`
  - Extra Variables for the Roles

  |image11|

.. codeblock:: yaml
    ---
    BIGIPadminUsername: "admin"
    BIGIPadminPassword: "admin"

    deviceName1: "10.1.1.8"
    deviceName2: "10.1.1.10"
    serviceName: "as3demo"
    servicePort: "80"
    forwarderName: "tsdemo"

.. Note:: There are other Playbooks in this SCM repository, specifically there is one for each of our Automation Toolchain objects, and the full_build. The full_build will run all the roles for each of the Automation Toolchain objects together.

.. Note:: Our Ansible Role contains our AS3 declaration that is used in this documentation, which was also used in Postman. Its a perfect example of source control.

Return to the `Projects` Tab. We are going to deploy our Template which will stitch together all its objects and run against our BIG-IPs.

``Deploy`` the Template by clicking the deploy icon.

  |image11|

Our Template will deploy all the code we've used previously in our Postman module, but because everything is idempotent, no change will be inacted on the BIG-IPs. The Automation Toolchain objects look through all 4 declarations that are coming for deltas, finding none, no action will need to be taken.

.. Note:: At this point we've progressed into a solution that could be Continiously Delvered. 

Task |labmodule|\.\ |labnum|\.3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Mutation of objects and reusable items.






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
.. |image3| image:: images/image3.png
.. |image4| image:: images/image4.png
.. |image5| image:: images/image5.png
.. |image6| image:: images/image6.png
.. |image7| image:: images/image7.png
.. |image8| image:: images/image8.png
.. |image9| image:: images/image9.png
.. |image10| image:: images/image10.png
.. |image11| image:: images/image11.png
.. |image12| image:: images/image12.png
.. |image13| image:: images/image13.png

.. _CloudDocs: https://clouddocs.f5.com