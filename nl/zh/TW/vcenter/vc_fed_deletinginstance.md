---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 刪除 VMware Federal 實例

若要釋出您在 VMware Federal 實例中訂購的元件，請刪除該實例。

當您刪除 VMware Federal 實例時，會循序釋出下列元件：

1. 支援與服務費用
2. VMware 產品授權
3. ESXi 伺服器
4. 子網路

由於資源相依關係，當您刪除實例時，不會立即釋放實例中的元件。例如，在 {{site.data.keyword.cloud}} 基礎架構完整收回 ESXi 伺服器（發生於 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束時）之前，無法刪除子網路。當 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束（通常是 30 天），就會刪除子網路，並且完成實例刪除。

將針對已刪除的實例，向您收取到 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束為止的費用。
{:note}

## 從已部署的實例頁面刪除實例的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，尋找要刪除的實例。
3. 在**動作**直欄中，按一下「刪除」圖示。
   實例的狀態會變更為**正在刪除**。順利刪除實例後，會釋出該實例的元件，且該實例的狀態會變更為**已刪除**。
4. 如果您要從 {{site.data.keyword.vmwaresolutions_short}} 主控台移除實例記錄，請完成下列步驟：
   1. 在**動作**直欄中，再按一次「刪除」圖示。
   2. 在**刪除實例**視窗中，按一下**確定**。

## 從實例詳細資料頁面刪除實例的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下要刪除的實例。
3. 按一下 **vCenter 主控台**旁的溢位功能表圖示，然後按一下**刪除實例**。實例的狀態會變更為**正在刪除**。順利刪除實例後，會釋出該實例的元件，且該實例的狀態會變更為**已刪除**。
4. 如果您要從 {{site.data.keyword.vmwaresolutions_short}} 主控台移除實例記錄，請完成下列步驟：
   1. 再按一次 **vCenter 主控台**旁的溢位功能表圖示，然後按一下**刪除實例**。
   2. 在**刪除實例**視窗中，按一下**確定**。

### 相關鏈結

* [VMware Federal on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/vcenter/vc_fed_overview.html)
* [訂購 VMware Federal 實例](/docs/services/vmwaresolutions/vcenter/vc_fed_orderinginstance.html)
* [保護 VMware Federal 實例](/docs/services/vmwaresolutions/vcenter/vc_fed_securinginstance.html)
* [檢視 VMware Federal 實例](/docs/services/vmwaresolutions/vcenter/vc_fed_viewinginstance.html)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
