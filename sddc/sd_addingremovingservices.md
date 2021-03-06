---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-06"

subcollection: vmware-solutions


---

# Ordering, viewing, and removing services for Cloud Foundation instances
{: #sd_addingremovingservices}

You can order services for your VMware Cloud Foundation instances, such as a disaster recovery solution. When you no longer need these services, you can remove them from your instances.

## Available services for Cloud Foundation instances
{: #sd_addingremovingservices-available-services}

The following table shows the services that are available to Cloud Foundation instances, together with the installed service versions.

Table 1. Available services for Cloud Foundation instances

| Service name | Current service version | Instance version |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | BIG-IP VE v14.1.0.2 | V1.9 and later |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)       | 300 series | V1.8 and later |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | 6.0.3 | V2.0 and later |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)              | 5.4.2 | V2.3 and later |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)              | 4.2.1 | V2.3 and later |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations) | 4.2 | V2.5 and later |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)  | 10.1.2 | V2.2 and later |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) |  2.0 | N/A |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) | 9.5u4 | V1.8 and later |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) | 6.5 update 3 | V1.2 and later |

## Procedure to add services to Cloud Foundation instances
{: #sd_addingremovingservices-adding-procedure}

To add a service to your Cloud Foundation instance, click the appropriate service link in the previous table to review the considerations for the service and check the components that are deployed. Then, follow the instructions in the appropriate ordering services topic to add the service to your instance.

### Service installation results
{: #sd_addingremovingservices-adding-results}

When the installation of the service is completed successfully, you are notified by email, and the service is displayed on the **Services** page of the instance with the **Installed** status.

## Procedure to view services for Cloud Foundation instances
{: #sd_addingremovingservices-viewing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **Cloud Foundation Instances** table, click the instance for which you want to view services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, click a service to review information about it, such as the service status and other details.
5. Depending on the viewed service, you can access the service consoles by using the credentials that are provided on the service details and you can manage the service from here.

## Procedure to remove services for Cloud Foundation instances
{: #sd_addingremovingservices-removing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** on the left navigation pane.
2. In the **Cloud Foundation Instances** table, click the instance for which you want to remove services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, locate the service instance that you want to remove and click the **Delete** icon.
5. In the **Delete Service** window, review the considerations or warnings if there are any. Select **I Understand** and click **Delete**.

### Service removal results
{: #sd_addingremovingservices-removing-results}

After your request for service removal is accepted, the service status is changed to **Removing**.

When the removal of the service is completed successfully, you're notified by email, and the service is removed from the **Services** page of the instance.

You are billed until the end of the {{site.data.keyword.cloud_notm}} billing cycle for the removed services.
{:note}

## Related links
{: #sd_addingremovingservices-related}

* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
