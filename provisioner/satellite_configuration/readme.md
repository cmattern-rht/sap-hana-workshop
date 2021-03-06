# Satellite configuration for SAP AWS training provisioner

This workshop requires access to RHEL content which can come from either the Red Hat CDN or a Satellite. This document describes the configuration of the Satellite used in our development process. Satellite will provide an easy interface to view and remediate Insights findings by creating temproary student accounts on your Satellite. Demonstrating Insight throught the cloud.redhat.com portal today requires driect login to the subscrition holders account and, while technically possible, is strondlgy discouraged. If you plan to demostrate Insights remediation via cloud.redhat.com be sure to read the documentation on Cloud connector carefully to avoid being struck down by the demo gods.

## Table of Contents
* [Satellite Configuration](#satellite-configuration)
  * [Version](#version)
  * [Enabled Repos](#enabled-repos)
* [Content Host Specifics](#content-host-specifics)
  * [Host Group](#host-Group)
  * [Lifecycle](#lifecycle)
  * [Activation Keys](#activation-keys)
  * [Content Views](#content-views)

## Satellite Configuration
### Version
Tested on version >=6.8 but probably fine on anything >6.7
### Enabled Repos
Name | Repo
-----|-----
Red Hat Enterprise Linux 8 for x86_64 - AppStream RPMs 8.1 | rhel-8-for-x86_64-appstream-rpms
Red Hat Enterprise Linux 8 for x86_64 - AppStream - Update Services for SAP Solutions RPMs 8.1 | rhel-8-for-x86_64-appstream-e4s-rpms
Red Hat Enterprise Linux 8 for x86_64 - BaseOS RPMs 8.1 | rhel-8-for-x86_64-baseos-rpms
Red Hat Enterprise Linux 8 for x86_64 - BaseOS - Update Services for SAP Solutions RPMs 8.1 | rhel-8-for-x86_64-baseos-e4s-rpms
Red Hat Enterprise Linux 8 for x86_64 - SAP NetWeaver RPMs 8.1 | rhel-8-for-x86_64-sap-netweaver-rpms
Red Hat Enterprise Linux 8 for x86_64 - SAP NetWeaver - Update Services for SAP Solutions RPMs 8.1 | rhel-8-for-x86_64-sap-netweaver-e4s-rpms
Red Hat Enterprise Linux 8 for x86_64 - SAP Solutions RPMs 8.1 | rhel-8-for-x86_64-sap-solutions-rpms
Red Hat Enterprise Linux 8 for x86_64 - SAP Solutions - Update Services for SAP Solutions RPMs 8.1 | rhel-8-for-x86_64-sap-solutions-e4s-rpms
Red Hat Satellite Tools 6.8 for RHEL 8 x86_64 RPMs | satellite-tools-6.8-for-rhel-8-x86_64-rpms
Red Hat Satellite Tools 6.8 for RHEL 8 x86_64 - Update Services SAP Solutions RPMs 8.1 | satellite-tools-6.8-for-rhel-8-x86_64-e4s-rpms
Red Hat Enterprise Linux 8 for x86_64 - High Availability RPMs 8.1 | rhel-8-for-x86_64-highavailability-rpms
Red Hat Enterprise Linux 8 for x86_64 - High Availability - Update Services for SAP Solutions RPMs 8.1 | rhel-8-for-x86_64-highavailability-e4s-rpms
Red Hat Ansible Engine 2.9 for RHEL 8 x86_64 RPMs | ansible-2.9-for-rhel-8-x86_64-rpms
### Content Host Specifics
#### Host Group
HANA_Image
#### Lifecycle
All servers assigned to **Production**
#### Activation Keys
* SAP HANA Server
  * Release Version: 8.1
  * Environment: Production
  * Content View: RHEL SAP HANA Base
  * Subscriptions: Employee SKU (obviously this will vary for non-Employees)
  * Repository Sets
    * Red Hat Enterprise Linux 8 for x86_64 - BaseOS (RPMs)
    * Red Hat Enterprise Linux 8 for x86_64 - BaseOS - Update Services for SAP Solutions (RPMs)
    * Red Hat Enterprise Linux 8 for x86_64 - AppStream (RPMs)
    * Red Hat Enterprise Linux 8 for x86_64 - AppStream - Update Services for SAP Solutions (RPMs)
    * Red Hat Satellite Tools 6.8 for RHEL 8 x86_64 (RPMs)
    * Red Hat Satellite Tools 6.8 for RHEL 8 x86_64 - Update Services SAP Solutions (RPMs)
    * Red Hat Enterprise Linux 8 for x86_64 - SAP Solutions (RPMs)
    * Red Hat Enterprise Linux 8 for x86_64 - SAP Solutions - Update Services for SAP Solutions (RPMs)
    * Red Hat Enterprise Linux 8 for x86_64 - High Availability (RPMs)
    * Red Hat Enterprise Linux 8 for x86_64 - High Availability - Update Services for SAP Solutions (RPMs)
* SAP S4 Server
  * Release Version: 8.1
  * Environment: Production
  * Content View:
  * RHEL SAP HANA Base
  * Subscriptions: Employee SKU
  * Repository Sets
    * Red Hat Enterprise Linux 8 for x86_64 - BaseOS (RPMs)
    * Red Hat Enterprise Linux 8 for x86_64 - BaseOS - Update Services for SAP Solutions (RPMs)
    * Red Hat Enterprise Linux 8 for x86_64 - AppStream (RPMs)
    * Red Hat Enterprise Linux 8 for x86_64 - AppStream - Update Services for SAP Solutions (RPMs)
    * Red Hat Satellite Tools 6.8 for RHEL 8 x86_64 (RPMs)
    * Red Hat Satellite Tools 6.8 for RHEL 8 x86_64 - Update Services SAP Solutions (RPMs)
    * Red Hat Enterprise Linux 8 for x86_64 - SAP NetWeaver (RPMs)    
    * Red Hat Enterprise Linux 8 for x86_64 - SAP NetWeaver - Update Services for SAP Solutions (RPMs)
#### Content Views
##### RHEL 8.1 SOE
###### Repos
* Red Hat Enterprise Linux 8 for x86_64 - BaseOS RPMs 8.1
* Red Hat Enterprise Linux 8 for x86_64 - AppStream RPMs 8.1
* Red Hat Satellite Tools 6.8 for RHEL 8 x86_64 RPMs
##### SAP Application Server Overlay RHEL 8
###### Repos
* Red Hat Enterprise Linux 8 for x86_64 - SAP NetWeaver RPMs 8.1
* Red Hat Enterprise Linux 8 for x86_64 - SAP NetWeaver - Update Services for SAP Solutions RPMs 8.1
* Red Hat Enterprise Linux 8 for x86_64 - SAP Solutions RPMs 8.1
* Red Hat Enterprise Linux 8 for x86_64 - SAP Solutions - Update Services for SAP Solutions RPMs 8.1
* Red Hat Satellite Tools 6.8 for RHEL 8 x86_64 - Update Services SAP Solutions RPMs 8.1
* Red Hat Ansible Engine 2 for RHEL 8 x86_64 RPMs
##### SAP HANA Overlay RHEL 8
###### Repos
* Red Hat Enterprise Linux 8 for x86_64 - High Availability RPMs 8.1
* Red Hat Enterprise Linux 8 for x86_64 - High Availability - Update Services for SAP Solutions RPMs 8.1
* Red Hat Enterprise Linux 8 for x86_64 - SAP NetWeaver RPMs 8.1
* Red Hat Enterprise Linux 8 for x86_64 - SAP NetWeaver - Update Services for SAP Solutions RPMs 8.1     
* Red Hat Enterprise Linux 8 for x86_64 - SAP Solutions RPMs 8.1
* Red Hat Enterprise Linux 8 for x86_64 - SAP Solutions - Update Services for SAP Solutions RPMs 8.1
* Red Hat Satellite Tools 6.8 for RHEL 8 x86_64 - Update Services SAP Solutions RPMs 8.1
* Red Hat Ansible Engine 2 for RHEL 8 x86_64 RPMs
##### SAP Application Server RHEL 8
###### Content Views
* RHEL8 SOE
* SAP Application Server Overlay RHEL 8
##### SAP HANA Server RHEL 8
###### Content Views
*    RHEL8 SOE
*    SAP HANA Overlay RHEL 8
