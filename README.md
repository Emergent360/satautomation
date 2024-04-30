![logos](https://github.com/Emergent360/satautomation/assets/18014714/13b3e5b4-0b94-4b0d-b92e-c79b183ffc89)


# Satellite Automation Workshop
Welcome to today's Satellite Automation Workshop! We are very excited to present a bit of a tour along with some exercises that will help your teams understand how Ansible Automation Platform integrates with Red Hat Satellite to manage OS patching and content deployment in a predictable, automated way. 


Before we get started, let's log into your student seat:

> Assign yourself a student number using [Student Assignments](https://aap2-april26test.lab-emergent360.com/#studentinfo)

![student assignment page](https://github.com/Emergent360/satautomation/assets/18014714/cffcfda9-2488-4fe9-b75b-8a935870d960)


> For more information on Ansible Best Practices, playbooks, inventory creation, roles, and modules; checkout this deck: [Ansible Best Practices](https://aap2.demoredhat.com/decks/ansible_best_practices.pdf) 



## **Use Cases** ##
This workshop currently focuses on 4 main customer pain points: 

- Compliance (OpenSCAP Scanning) and Vulnerability Management
- Patch/Package Management
- CentOS to RHEL conversion
- Vulnerability Management with Insights

## **Presentation** ##
The exercises are self-explanatory and are meant to guide participants through the entire lab. All concepts are explained as they are introduced. 

Today's presentation is available to support the workshop and explain Automation, the basics of Ansible and the topics of the exercises in more detail. Today's Workshop presentation can be downloaded [here](https://uploads-ssl.webflow.com/64dd02f7406bf2448a30e68f/662fdbc786abd010d11d18b8_Satellite%20Automation.pdf)

## **Time Planning and CPE Credits** ##
The time required to do the workshops strongly depends on multiple factors: the number of participants, how familiar those are with Linux in general and how much discussions are done in between.

Having said that, the presentation should take about 40 minutes, with a 10-minute break, then the exercises themselves should take roughly 3 hours. We will break every 40 minutes or so to complete three polling questions, allowing the group to qualify for CPEs. This workshop is accredited by NASBA, which requires one CPE credit to be awarded for every 50 minutes of teaching. The polling questions ensure participants are present and working on presented content. You will be awarded credits as long as you respond to the polling questions. 

Certificates with the awarded amount of CPEs should be sent out to the attendees within 5 business days, post-event. 

## **Welcome to Your Ansible Automation Platform Workshop Tour!**
Get ready to unlock the power of automation! This workshop will guide you through the exciting world of Ansible Automation Platform (AAP), equipping you to automate IT tasks and streamline your processes.

Here's what you can expect today:

An Introduction to Ansible Automation Platform (AAP).

We'll kick things off with an overview of AAP, its key components, and its numerous benefits for automating infrastructure, applications, and IT workflows.
Learn how AAP builds upon the foundation of Ansible Tower and introduces features like centralized management, role-based access control, and enhanced security.

A chart of today's workshop environment looks like this:

![ansible_smart_mgmt_diagram](https://github.com/Emergent360/satautomation/assets/18014714/51aea489-b1f3-4d17-9696-3bc6802a18e2)

## **Environment** ##

![Environment](https://github.com/Emergent360/satautomation/assets/18014714/5f2170d8-4a2f-4a63-b08e-8d1db6f1dde8)


Then, we will dive into the AAP User Interface:

Get comfortable navigating the intuitive AAP user interface. We'll explore dashboards, inventories, projects, and credentials – the building blocks for your automation adventures.
Learn how to manage your infrastructure within AAP, including adding machines, groups, and cloud resources.

Next up, we will build our First Playbook:

Now comes the fun part! We'll delve into the world of Ansible playbooks, the heart of automation. You'll learn how to write playbooks using YAML syntax to automate tasks.
We'll walk you through the structure of a playbook, covering modules, tasks, variables, and conditionals.

Get hands-on experience by building your first basic playbook to automate a simple task on your managed machines.

After building our first playbook, we will use some more advanced Playbook techniques:

Don't stop there! We'll explore advanced playbook features like loops, conditionals, error handling, and templating. These powerful tools will enable you to create sophisticated automations that adapt to various conditions.

Learn how to manage complex workflows by breaking them down into smaller, reusable playbooks.

We will of course take a look at Inventory management as well:

Efficient inventory management is crucial for scaling your automation. We'll explore how to manage inventories in AAP, including adding machines by IP address, hostname, or cloud provider.
Learn how to leverage dynamic inventories to automatically discover and manage your infrastructure.

Finally, we'll take a look at Security and Access Control:

Security is paramount. We'll discuss the robust security features within AAP, including role-based access control (RBAC) and credential management.
Learn how to assign different levels of access to users and teams within your organization.

Putting it All Together:

We'll wrap up by showcasing some real-world examples of how AAP can be used to automate various tasks across IT operations, including provisioning servers, configuring software, and deploying applications.

Gain inspiration for how to leverage AAP to streamline your own processes and boost your team's efficiency.
Throughout the workshop, there will be ample opportunities for hands-on practice, Q&A sessions, and interaction with your fellow participants and trainers.

Get ready to embark on your automation journey with Ansible Automation Platform!

## **Objective** ##

The objective of this exercise is to setup the lab environemnt following an Infrastructure as Code process. This exercise will require you to launch a series of playbooks. The playbooks accomplish the following:

Populate Ansible Controller with an inventory source, add templates, as well as an additional project.
Publish RHEL7 dev content view in Satellite
Register servers to the Satellite installation - RHEL7
Register servers to the Satellite installation - CentOS7
Populate dynamic inventories - RHEL7
Populate dynamic inventories - CentOS7

## **Exercise One** ##
 Log into your Ansible Automation Platform (AAP2) Controller

 Use the link found [here](https://aap2-april26test.lab-emergent360.com/#studentinfo)
 ![Student View](https://github.com/Emergent360/satautomation/assets/18014714/a68794ef-27a2-4e47-a651-5cb90863cc31)


 Select the link noted for "Automation controller"
![AAP2](https://github.com/Emergent360/satautomation/assets/18014714/f8933677-a55e-4284-958e-411620b0e7b5)

Once logged in, you should be able to see the Ansible Automation Platform dashboard:

![Dashboard](https://github.com/Emergent360/satautomation/assets/18014714/84c26793-30d0-4e0b-89dd-424a087f19cd)

Use the side pane menu on the left to select Projects and review the two projects named Automated Management and Fact Scan. These projects, along with the Workshop Inventory under Resources, and Inventories, have been set up for you during the provisioning of the lab environment. 

<img width="1423" alt="Projects" src="https://github.com/Emergent360/satautomation/assets/18014714/aaa8bf2a-b366-4302-944a-cfb04bc1ada2">

## **Exercise Two** ##

Next, we will execute our first job template. We'll be working with several templates during today's workshop, and this step uses a couple of them to initialize the lab environment. 

<img width="1423" alt="Templates" src="https://github.com/Emergent360/satautomation/assets/18014714/c05f3c6c-4264-4e80-8a00-a2eaa4172183">

You should initially see three Templates, named Demo Job Template, Z / CaC / Controller, and Z / CaC / Satellite 

Notice that the Z / CaC / Satellite template has already been run for you.

We will have to run the Z / CaC / Controller job template. To do this, click either into the job template and click Launch, or click the Rocketship icon. 

<img width="1422" alt="controller" src="https://github.com/Emergent360/satautomation/assets/18014714/a2cd2502-1d65-4146-8d00-0ef265de1b04">

You will be taken under the Views, Jobs output window, where you can view the output from the job run. This will display all the tasks executed as part of the playbook. This should take about two minutes to complete and you should see a green "Successful" tag after the name of the playbook in this view once the last task has completed. 

<img width="1425" alt="Controller Play" src="https://github.com/Emergent360/satautomation/assets/18014714/ec278bcb-43f4-4623-aeaa-5811166088f9">

Remember to wait until you see the green "Successful" tag before moving on to the next exercise. 

Then, navigate back to Templates on the left side pane. 

You will notice many more Job Templates have been provisioned in your Controller. We will use some of these in today's workshop. 

<img width="1436" alt="Templates" src="https://github.com/Emergent360/satautomation/assets/18014714/a807edef-6232-44a8-b132-f6966490294f">

Next, let's run SATELLITE / RHEL - Publish Content View job template by clicking the rocketship icon or by pressing the Launch button. When prompted by the survey for the content view to publish, from the drop down menu, select RHEL 7. 

<img width="1432" alt="Publish Content View" src="https://github.com/Emergent360/satautomation/assets/18014714/df91cd75-218b-4b8f-9501-e6ac0aa9b8a6">

<img width="1118" alt="Survey" src="https://github.com/Emergent360/satautomation/assets/18014714/7cdd8bf6-c7ad-4b52-9bdb-6fa190c05ef2">

> Hit Next, then Launch.

You will be taken to the Jobs view, showing the output window for the template SATELLITE / RHEL - Publish Content View. This job will take about a minute to run. 

<img width="1434" alt="Publish Content View" src="https://github.com/Emergent360/satautomation/assets/18014714/35fc21d8-bb3c-455f-a11a-34d722e9f85a">

Next, click on Templates and search for CONVERT2RHEL / 01 - Take node snapshot job template. Click on the rocketship icon or the template, and click Launch. This job template will take longer, about seven minutes to complete. 

<img width="1431" alt="Convert2RHEL Take Snapshot" src="https://github.com/Emergent360/satautomation/assets/18014714/3f8b53bc-9b27-4ad7-a633-c1c723ee4779">

<img width="1436" alt="Node Snapshot Output" src="https://github.com/Emergent360/satautomation/assets/18014714/8b7f0ce8-1374-4e7a-a475-ab6f356fd761">

Next up, click on Templates, search for, and run the SERVER / RHEL7 - Register job template by click the rocketship icon or by clicking into the template and selecting Launch. When the survey appears, complete it as follows:

<img width="1438" alt="RHEL 7 Register" src="https://github.com/Emergent360/satautomation/assets/18014714/28e99a80-9c29-4685-a6ac-f44b9e08bb72">

<img width="1116" alt="Register" src="https://github.com/Emergent360/satautomation/assets/18014714/e19a32bb-9464-42d0-ac3d-636cb3f28939">



## **Satellite Tour**

During this portion of today's workshop, we will give you a comprehensive overview of Red Hat Satellite, a powerful management tool for Red Hat Enterprise Linux (RHEL) deployments. We'll delve into its features, explore its functionalities, and discover how it can streamline your infrastructure management.  By the end of this workshop, you'll be equipped to leverage Satellite's capabilities to automate tasks, improve security, and achieve greater efficiency in managing your RHEL environment.

A centralized management platform for Red Hat Enterprise Linux (RHEL) systems.
Simplifies and automates tasks like provisioning, configuration management, patch management, and subscription management.
Provides a single point of control for managing your entire RHEL infrastructure.

Reduced Costs: Saves time and resources by automating tasks.
Increased Efficiency: Streamlines workflows and simplifies management.
Improved Security: Enhances security posture by automating patch deployment and vulnerability management.
Enhanced Compliance: Simplifies compliance audits with centralized reporting and audit trails.

System Provisioning: Automate the deployment of new RHEL systems with pre-configured settings.
Configuration Management: Apply and enforce consistent configurations across your entire RHEL environment.
Patch Management: Automate the deployment of security patches and software updates to ensure your systems stay up-to-date.
Subscription Management: Manage and track RHEL subscriptions for all your systems from a central location.
Content Delivery: Efficiently distribute content like patches, software updates, and configuration files to your RHEL systems.
Reporting and Auditing: Generate comprehensive reports for compliance audits and track system activity.

Satellite Server: The central management hub that controls and coordinates all Satellite operations.
Capsule Servers (Optional): Optional servers deployed closer to remote systems for faster content delivery and reduced network traffic.
Client Systems: RHEL systems managed by Satellite.
Content Repositories: Repositories containing software packages, patches, and configuration files.
External Systems: External systems like identity management and subscription management services.



## **Convert2RHEL** ##

Next up, let's use Convert2RHEL to upgrade a CentOS 7 node to RHEL. To do this, we will first SSH into a node. We can use Node4 for this exercise. 

1. SSH into Node4

```
   ssh centos@node4
``` 

3. Login and sudo to root
    - sudo su –

4. Update CentOS box and reboot
 
```
  yum update -y
```

   - reboot

6. Login again, sudo to root

   - sudo su –

7. Download RH GPG key and install convert2rhel repo

```
   curl -o /etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release https://www.redhat.com/security/data/fd431d51.txt
```

```
    curl -o /etc/yum.repos.d/convert2rhel.repo https://ftp.redhat.com/redhat/convert2rhel/7/convert2rhel.repo
```

8. Install convert2rhel utility

```
   yum -y install convert2rhel
```


10. Add activation key. INI file should look like below after opening file using VI. Update the "activation_key" value to convert2rhel_demo. 

```
vi /etc/convert2rhel.ini
```
        
	# -*- coding: utf-8 -*-
        # This file should be in mode 0600
        # Example of configuration file convert2rhel.ini for secrets.
        # Possible locations of this file:
        # 1) user specified and passed by -c, --config-file option; highest priority
        # 2) ~/.convert2rhel.ini; lower priority
        # 3) /etc/convert2rhel.ini; the lowest priority

        [subscription_manager]
        # password = <insert_password>
        activation_key = convert2rhel_demo
        org            = 13156267


11. Run convert2rhel command

   ```
   convert2rhel --debug
```


11. IF the conversion fails, the kernel module may cause convert2rhel to fail, so we must ignore that step by setting following environment variable. Run the command below and try again. 

   ```
   export CONVERT2RHEL_ALLOW_UNAVAILABLE_KMODS=1
```


11. Reboot the system


12. Login again, sudo to root, and verify system has been upgraded to RHEL:

```
    uname –r
```

```
    cat /etc/redhat-release
```

```
    subscription-manager list
```

