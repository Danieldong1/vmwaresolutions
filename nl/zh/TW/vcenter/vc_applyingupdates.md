---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 將更新套用至 vCenter Server 實例
{: #vc_applyingupdates}

只會針對管理元件自動進行將修補程式及更新套用至 vCenter Server 實例的處理程序。必須手動套用 VMware 更新。

## 開始之前
{: #vc_applyingupdates-prereq}

將 vCenter Server 實例升級至 vCenter Server with Hybridity Bundle 實例時，您必須先至少套用基礎 vCenter Server 2.3 版軟體更新。必須先執行此動作，才能執行授權升級至 Hybridity Bundle。
{:important}

「事業夥伴」使用者無法選擇將現有 vCenter Server 實例升級至 vCenter Server with Hybridity Bundle 實例。

因為已啟用自動更新，所以從 2.5 版開始，不再列出 IBM CloudDriver 更新。例如新增主機、新增叢集及訂購服務等動作，會自動將實例更新至最新版本。如需自動更新的相關資訊，請參閱 [2.5 版的版本注意事項](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-relnotes_v25)中的 *IBM CloudDriver 備援* 小節。
{:note}

在您嘗試套用更新之前，請按一下向下箭頭來展開更新項目，並驗證下列資訊：
* 更新的版本。您必須依最早到最新的時間順序來套用更新。套用最新的更新之前，請確定已套用所有先前的更新。例如，嘗試套用 2.4 版更新之前，您必須套用 2.3 版更新。
* 是否需要關閉時間。
* 完成更新的總估計時間。
* 更新對 VMware 虛擬環境的影響。表 1 顯示不同的更新層次對於系統有何影響。
* 更新詳細資料。

表 1. 更新層次及影響

<table>
  <tr>
    <th>更新層次</th>
    <th>影響</th>
  </tr>
  <tr>
    <td>低</td>
    <td>此更新不會影響任何系統。您不需要在排定的關閉時間套用它。</td>
  </tr>
  <tr>
    <td>中</td>
  <td>此更新可能會影響部分系統。建議您在排定的關閉時間套用它。</td>
  </tr>
    <tr>
    <td>重大</td>
  <td>此更新會影響部分或所有系統。您必須在排定的關閉時間套用它。</td>
  </tr>
</table>

## 將更新及修補程式套用至 vCenter Server 實例的程序（2.1 版或更新版本）
{: #vc_applyingupdates-procedure}

此程序適用於已部署在 2.1 版或更新版本的實例。對於已部署在 2.0 版及更早版本的實例，您必須手動套用 VMware 更新。

1. 從 {{site.data.keyword.vmwaresolutions_full}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下要更新的實例。
3. 在**摘要**頁面上，驗證所有實例詳細資料都已正確顯示。然後，按一下左導覽窗格上的**基礎架構**，以驗證**基礎架構**頁面上的詳細資料。
   如果未顯示詳細資料，這可能表示因為防火牆規則或其他網路問題的緣故，而有 IBM CloudDriver 虛擬伺服器實例 (VSI) 連線問題。請先解決問題，再繼續下一步，否則更新可能會失敗。
4. 在左導覽窗格上，按一下**更新及修補程式**。

   實例的**更新及修補程式**頁面只包含用來更新 IBM 管理元件的套件，而不包含 VMware 更新。必須手動套用 VMware 更新。{{site.data.keyword.vmwaresolutions_short}} 會針對下列作業套用 VMware 更新：
   * 部署新的 vCenter Server 實例時。
   * 新增 ESXi 伺服器時，會使用 VMware 更新來佈建新的 ESXi 伺服器，但不會更新現有的 ESXi 伺服器。
   * 新增叢集時，會使用 VMware 更新來佈建新的叢集，但不會更新現有的叢集。
   {:note}

5. 若要升級 NSX 授權，請按一下**升級**。在**升級 NSX 授權版本**視窗中，選取您要升級至的版本，然後按一下**升級**。無法進行授權版本降級。

   授權升級會取代實例上的所有現有 NSX 授權。如果您在計費週期中途進行升級，則可能因為新舊授權重疊而產生其他費用。為了避免產生其他費用，建議在計費週期結束時升級授權。
   {:note}

6. 對於軟體更新，請按一下向下箭頭來展開您要套用的更新，然後完成下列其中一個步驟：
   *  若要立即啟動更新，請按一下更新項目之**動作**直欄中的溢位功能表圖示，然後按一下**立即更新**。
   *  若要排定未來的更新，請按一下更新項目之**動作**直欄中的溢位功能表圖示，然後按一下**排定更新**。選取您要啟動更新的日期、時間及時區。按一下**確定**。
7. 如果您要在多站台部署配置中將更新套用至 vCenter Server 實例，則會顯示標題為**更新所需要的步驟**的區段。本節列出多站台部署中所有實例所需的更新作業。您必須對每個步驟按一下**套用更新**，來依序完成步驟。您必須先等待上一步完成，再開始下一步。   

## 升級至 vCenter Server with Hybridity Bundle 實例的程序
{: #vc_applyingupdates-procedure-upgrade-to-hybridity}

在授權升級至 Hybridity Bundle 期間，如果您的 vCenter Server 實例目前使用 VMware NSX Base 版本，則會自動升級至 VMware NSX Advanced 版本。

如果您升級至 Hybridity Bundle，而且 vCenter Server 實例已有 NFS 檔案儲存空間，則不會向您收取 VMware vSAN 儲存空間的費用。會向您收取 vSAN 授權的費用，因為它包含在 Hybridity Bundle 中。
{:note}

完成下列步驟，以將 vCenter Server 實例升級至 vCenter Server with Hybridity Bundle。

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下要升級的實例。
3. 在**摘要**頁面上，驗證所有實例詳細資料都已正確顯示。然後，按一下左導覽窗格上的**基礎架構**，以驗證**基礎架構**頁面上的詳細資料。
   如果未顯示詳細資料，這可能表示因為防火牆規則或其他網路問題的緣故，而有 IBM CloudDriver VSI 連線問題。請先解決問題，再繼續下一步，否則更新可能會失敗。
4. 在左導覽窗格上，按一下**更新及修補程式**。
5. 套用 Hybridity Bundle 授權升級。在**授權升級**表格中，按一下**動作**直欄中的**升級**、檢閱預估成本，然後按一下**升級**。
6. （選用）部署 VMware HCX on {{site.data.keyword.cloud_notm}} 服務。在**授權升級**表格上啟用 Hybridity Bundle 時，請完成下列步驟：
  1. 在**授權升級**表格中，按一下**動作**直欄中的**部署 HCX on {{site.data.keyword.cloud_notm}}**。
  2. 捲動至 **HCX on {{site.data.keyword.cloud_notm}}** 卡片，然後按一下**選取服務**。
  3. 向下捲動，並指定服務的必要設定，然後按**下一步**。
  4. 檢閱適用於服務的條款、檢閱預估成本，然後按一下**下訂單**。

## 結果
{: #vc_applyingupdates-results}

1. 在您套用更新之後，軟體更新狀態清單中會出現一筆記錄，您可以在其中檢視更新的詳細進度及狀態。更新順利完成時，已安裝的軟體更新清單中會出現一筆記錄。

  若要擷取更新工作的最新狀態，請按一下頁面右上角的重新整理圖示。
  {:tip}

2. 如需更新狀態的詳細資料，請參閱下表。

   表 2. 更新狀態的詳細資料

    <table>
      <tr>
        <th>狀態</th>
        <th>詳細資料      </th>
      </tr>
      <tr>
        <td>可用</td>
        <td>更新可供套用。在套用所有先前的更新之前，您無法選取可用的更新。</td>
      </tr>
      <tr>
        <td>進行中</td>
      <td>更新工作已起始，但尚未完成。在現行更新工作完成之前，您無法套用任何其他更新。</td>
      </tr>
        <tr>
        <td>已安裝</td>
      <td>更新工作已完成。會更新 VMware 平台的對應元件。</td>
      </tr>
        <tr>
        <td>失敗</td>
      <td>更新工作失敗。主控台會報告更新失敗的錯誤。請先檢閱錯誤並修正報告的問題，再重新套用更新。</td>
      </tr>
          <tr>
        <td>已排定</td>
      <td>已排定稍後執行更新工作。更新工作會在您排定的時間自動啟動。</td>
      </tr>
          <tr>
        <td>不明</td>
      <td>無法取得更新工作的狀態。請與 IBM 支援中心聯絡，以取得協助。</td>
      </tr>
    </table>

3. 如果更新處理程序在特定步驟失敗，請[與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)以取得協助。會建議您如何解決問題，並引導您從失敗的步驟重新嘗試升級。

## 相關鏈結
{: #vc_applyingupdates-related}

* [vCenter Server 概觀](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
