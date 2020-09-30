Establishing an HA Cluster
=========================

Now that the servers have been provisioned and properly subscribed to Satellite to receive software and updates, you are
ready to configure the HA Cluster environment.

Overview
========

In this lab exercise, you will identify vulnerable systems and automatically apply live kernel patches on your lab instances.

SAP Host preparation is a complex and long task that traditionaly involves multiple teams and expertise to accomplish. There is not a unique document we can follow in order to get the system configured in the way SAP installers are expecting. SAP uses ‘SAP Notes’ to capture all these prerequisites and specific configurations that need to be done prior HANA and NetWeaver software could be installed.

Red Hat and SAP teams provides a set of Ansible roles that greatly simplifies this workflow in a reliable and repeatable way. ‘Red Hat Enterprise Linux System Roles for SAP’ is a collection of Ansible Roles developed by SAP and Ansible experts and supported by Red Hat.

For the purposes of this workshop, we broke the deployment into three stages:

1. Preconfigure SAP HANA servers for deployment
2. Deploy HANA servers in HA configuration
3. Deploy S4HANA application server

In a real world scenario, these job templates can be tested by different users and put in a workflow template to run with one-click. You will see examples of how this is accomplished in subsequent lab exercises.

Preconfigure SAP HANA servers
======================

In this exercise, you will run the a job template that includes 3 roles:

##### - sap-preconfigure (runs on all nodes):
This Ansible role will ensure that prerequsite steps are applied on all nodes such as adjusting selinux, memory and
other OS parameters

##### - sap-netweaver-preconfigure (on S4 node):
This Ansible role will ensure that netweaver specific pre-configuration steps are performed on S4 node.

##### - sap-hana-preconfigure (on hana nodes):
This Ansible role will ensure that HANA specific pre-configuration steps are performed on HANA nodes.

Run **Lab 2 - SAP Prepare** job template to prepare the SAP environment by performing the pre-configuration steps
on all nodes.

Step 1:
-------

Select **TEMPLATES**

Step 2:
-------

Click the rocketship icon ![Add](images/at_launch_icon.png) for the
**Lab 2 - SAP Prepare**

Step 3:
-------

When prompted, in **Other Prompts** tab, enter sap3vm* (make sure you type '*' at the end as this will match multiple VMs)

Select **NEXT**.

Step 4:
-------

When prompted, in **Survey** tab, enter sap3vm this time.

Select **NEXT** and preview the inputs.

Step 5:
-------

Select LAUNCH.

Step 6:
-------

When the job has successfully completed, you should have all SAP nodes pre-configured.


Deploy SAP servers
======================

In this exercise, you will run a job template that will deploy HANA in HA clustered configuration as well as
 S4/HANA application server. The job template includes the following roles:

##### - redhat_sap.sap_rhsm (runs on all nodes):
This Ansible role will ensure that Red Hat Enterprise Linux Server nodes are properly registered with the Satellite server.
It will also ensure that required repositories for 'RHEL for SAP Solutions' are attached to the RHEL hosts. Additionally,
it will ensure the hosts are registered with Red Hat Insights.

##### - redhat_sap.sap_hostagent (runs all nodes):
This Ansible role will ensure the SAP Host Agent is installed and running on all hosts.

##### - redhat_sap.sap_hana_deployment (on hana nodes):
This Ansible role will ensure that SAP HANA is installed on both HANA nodes which will later be configured with HA.
This role will utilize ansible variables and performs an unattended installation, variables are defined along with the
Ansible playbook and stored in a source control repository. You can provide credentials and user provided variables from
Ansible Tower.

##### - redhat_sap.sap_hana_hsr (on hana nodes):
This Ansible role will ensure clustering is configured and enabled on HANA nodes.

##### - redhat_sap.sap_hana_ha_pacemaker (on hana nodes):
This Ansible role will ensure PCS is installed and configured to support underlying clustering at the OS level between
the HANA nodes. This role requires a Virtual IP(VIP) as an input parameter. In your lab environment this will provided
as part of the job template as a survey question.

Run **Lab 2 - SAP Deploy** job template to deploy HANA servers in HA clustered configuration and S4/HANA application
server.

Step 1:
-------

Select **TEMPLATES**

Step 2:
-------

Click the rocketship icon ![Add](images/at_launch_icon.png) for the
**Lab 2 - SAP Deploy**

Step 3:
-------

When prompted, in **Other Prompts** tab, enter sap3vm* (make sure you type '*' at the end as this will match multiple VMs)

Select **NEXT**.

Step 4:
-------

When prompted, in **Survey** tab, enter sap3vm this time and select a VIP from the list.

Select **NEXT** and preview the inputs.

Step 5:
-------

Select LAUNCH.

Step 6:
-------

When the job has successfully completed, you should have SAP deployed in your environment.


