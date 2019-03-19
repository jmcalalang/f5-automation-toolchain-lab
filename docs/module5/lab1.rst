Module |labmodule|\, Lab \ |labnum|\: CI/CD with Ansible Tower
==============================================================

Lab scenario:
~~~~~~~~~~~~~

|image1| Ansible Tower

F5 Declarative Onboarding, Application Services 3, and Telemetry Streaming are solutions that function well in within templated environments. The use of single declarative configuration files and idempotent solutions create scenarios where a system can progress from Continuous Delivery to Continuous Deployment.

Ansible Tower has been installed into this lab to show the possibility of an orchestration engine with the capabilities for large scale deployments. Tower has many features which will not be covered in this lab; however, two concepts that **are** covered are Projects and Templates.

Objects highlighted in this module.

  - A Project_ is a logical collection of Ansible playbooks, represented in Tower.
  - A job Template_ is a definition and set of parameters for running an Ansible job.

The entirety of this lab is in Source Control, with different tools using different parts; Postman we imported our collection directly from the lab SCM, the documentation and configuration examples are all pulled from the same source, giving the purpose as a Source-of-Truth. We are now going to integrate Module5 of this lab into Ansible Tower.

Ansible Tower will parse this lab GitHub repository looking for an `ansible.cfg` file, this file presents logical paths for objects used in an Ansible Project.

Task |labmodule|\.\ |labnum|\.1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ansible Tower has been installed and configured ready to be executed.

.. seealso:: The Postman Collection for this lab also contains the Ansible Tower configuration. `Module 5 - CI/CD with Ansible Tower` was used to License and configure Tower objects.

  |image2|

Using `Chrome` open a tab to Ansible Tower.

- Ansible Tower User: ``admin``
- Ansible Tower Password: ``admin``

  |image3|

Task |labmodule|\.\ |labnum|\.2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Making sure Ansible Tower has the current source code.

.. note: Ansible Tower version is `Tower 3.4.2` Ansible Version is `Ansible 2.7.9`.

Navigate to `Projects`.

  |image4|

Navigate to the `f5_automation_toolchain_project`.

  |image5|

The project pulls in its configuration from GitHub, and the `SCM URL` is the repository containing all our lab. The other Update settings used are because we use template created objects (jinja2 files) which we want to be cleared out on an update to not cause any overlapping issues.

  |image6|

The repository for this lab is public, ansible.cfg instructs Ansible Tower where it needs to lookup Ansible specific object (Roles and Playbooks)

  |image7|

Return to the `Projects` Tab. We need to update our Ansible Tower from Source Control, as our source goes through changes we want to make sure whatever we are working with is the most current.

``Update`` from source by clicking on the loop icon. 

  |image8|

This operation triggers an Ansible Tower `Job` to get the current configuration, this is viewed in `Jobs` and tagged as an `SCM Update`.

  |image9|

Navigating into the Job exposes the tasks and console of how the job performed.

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
- Extra Variables

  |image12|

Extra Variable include:
.. literalinclude :: files/f5_automation_toolchain_template_extra_variables.yml
   :language: yaml

.. Note:: There are other Playbooks in this SCM repository. Specifically, there is one for each of our Automation Toolchain objects and the full_build. The full_build runs all the roles for each of the Automation Toolchain objects together.

.. Note:: Our Ansible Role references the same AS3 declaration used in documentation, and also used in Postman. Its a perfect example of source control.

Return to the `Projects` Tab. We are going to deploy our Template which will stitches together all its objects and runs against our BIG-IPs.

``Deploy`` the Template by clicking the Deploy icon.

  |image13|

The Template deploys all the code we have used previously in our Postman module; however, because the Automation Toolchain objects are idempotent, no change is enacted on the BIG-IPs. 

  |image14|

.. Note:: At this point, we have progressed into a solution that could be Continuously Delivered. 

Task |labmodule|\.\ |labnum|\.4
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Mutation of objects and reusable items.

Template systems with single configuration files can lead to many "Snow-Flake" configuration items if not thought about early in the process. Without the use of parameters, the solution created in this lab would only be useful for one deployment. To highlight how a solution AS3 can be reused we are going to change some of the extra variables in our Template to create more deployments that use the template however are for different applications.

This lab is currently running 3 applications. Through this point of the lab we have been doing all our work against the `F5 Hello World` application, we are now going to use the same template we have crafted to deploy services to access the `Hackazon` and `DVWA` application.

This Table represents the applications and extra variables we will use to create our additional deployments.

+--------------------+-----------+-------------------+-------------------+-------------+
| **Application**    | partition | virtualAddresses1 | virtualAddresses2 | servicePort |
+--------------------+-----------+-------------------+-------------------+-------------+
| **F5 Hello World** | Module_03 | 10.1.20.110       | 10.1.20.111       | 8081        |
+--------------------+-----------+-------------------+-------------------+-------------+
| **Hackazon**       | Hackazon  | 10.1.20.112       | 10.1.20.113       | 80          |
+--------------------+-----------+-------------------+-------------------+-------------+
| **DVWA**           | DVWA      | 10.1.20.114       | 10.1.20.115       | 8082        |
+--------------------+-----------+-------------------+-------------------+-------------+

Return to the `f5_automation_toolchain_template` in Ansbile Tower.

Located at the bottom of the template are the extra variables, manipulate the variables to deploy one or both of our additional applications.

  |image15|

Save the Template with your new variables defined and rerun the template.

.. note:: You can reuse a Job after it is been run if you did not want to save the template each time you can return to a previously run Job and run with new variables.

  |image13|

This concludes Module 5 and utilizing Ansible Tower for Templates and Jobs to create reusable items.


.. |labmodule| replace:: 5
.. |labnum| replace:: 1
.. |labdot| replace:: |labmodule|\ .\ |labnum|
.. |labund| replace:: |labmodule|\ _\ |labnum|
.. |labname| replace:: Lab\ |labdot|
.. |labnameund| replace:: Lab\ |labund|

.. |image1| image:: images/image1.png
   :width: 200px
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
.. |image14| image:: images/image14.png

.. _Project: https://docs.ansible.com/ansible-tower/latest/html/userguide/projects.html
.. _Template: https://docs.ansible.com/ansible-tower/latest/html/userguide/job_templates.html