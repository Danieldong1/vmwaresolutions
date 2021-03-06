---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 擴充在主控台以外建立的叢集
{: #vs_orderingforclustersoutside}

您可以使用 VMware vSphere 供應項目來擴充在 {{site.data.keyword.vmwaresolutions_full}} 主控台以外建立的現有 vSphere 叢集。若要擴充在主控台以外建立的 vSphere 叢集，請使用與主控台相同的設定來重建叢集，然後擴充叢集。

## 需求
{: #vs_orderingforclustersoutside-req}

請確定您已完成下列作業：
*  您已在**設定**頁面上配置 {{site.data.keyword.cloud_notm}} 基礎架構認證。如需相關資訊，請參閱[管理使用者帳戶及設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)。
*  您已檢閱 [VMware vSphere on {{site.data.keyword.cloud_notm}} 的需求及規劃](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)中的需求及考量。

## 擴充在主控台以外建立的叢集的程序
{: #vs_orderingforclustersoutside-procedure}

1. 從 {{site.data.keyword.cloud_notm}} 型錄中，按一下左導覽窗格上的 **VMware**，然後按一下**虛擬資料中心**區段中的 **VMware vSphere**。
2. 在 **VMware vSphere on IBM Cloud** 頁面上，按一下**建立**。  
   請確定您位於**建立新項目**標籤，並在**叢集配置**清單中顯示**新叢集**。
3. 使用與現有叢集相同的設定來建立叢集，而現有叢集是在 {{site.data.keyword.vmwaresolutions_short}} 主控台以外所建立。如需相關資訊，請參閱[訂購新的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)。  
   對於網路介面，若要擴充在 {{site.data.keyword.vmwaresolutions_short}} 主控台以外建立的叢集，您必須為叢集選取現有的 VLAN。
   {:note}
4. 在**訂單摘要**窗格中，驗證叢集配置，然後按一下**儲存配置**。   
5. 在**開始使用**頁面上，按一下 **VMware vSphere on IBM Cloud** 卡片。
6. 在 **VMware vSphere on IBM Cloud** 頁面上，按一下**建立**。
7. 按一下**擴充現有項目**標籤。從**叢集配置**清單中，選取您最近建立的叢集。
8. 在 **{{site.data.keyword.baremetal_short}}** 區段中，指定您要新增至叢集的 {{site.data.keyword.baremetal_short}} 數目。
9. 如果該叢集在其公用 VLAN 上未包含「FortiGate 300 系列 Security Appliance HA 配對」，則您可以在 **FortiGate Physical Appliance 300 系列 HA 配對**下選取**購買隨附**，為它訂購一組。
10. 在**訂單摘要**窗格中，驗證實例配置及預估成本，並確定要收費的帳戶正確，然後檢閱並接受條款，再按一下**佈建**。

## 結果
{: #vs_orderingforclustersoutside-results}

叢集的部署會自動啟動，且您會收到電子郵件確認，指出正在處理該訂單。當叢集已備妥可供使用時，會透過電子郵件通知您。

vSphere 叢集不會連同 vCenter Server 實例及 Cloud Foundation 實例顯示在**資源**頁面上。
{:note}

## 相關鏈結
{: #vs_orderingforclustersoutside-related}

* [訂購新的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [根據現有配置來訂購 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [擴充現有的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
