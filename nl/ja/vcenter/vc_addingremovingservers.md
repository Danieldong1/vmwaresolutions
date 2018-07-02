---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# vCenter Server インスタンスの容量の拡張と縮小

ビジネス・ニーズに応じて、ESXi サーバーを追加または削除することで VMware vCenter Server インスタンスの容量を拡張または縮小することができます。

初期クラスターのストレージが vSAN の場合、デプロイメント後に 1 つ以上の ESXi サーバーを追加すると、クラスター・ストレージの容量を増やすことができます。

## 始める前に

* VMware vSphere Web クライアントから ESXi サーバーの追加や削除を行わないでください。 vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_short}} コンソールと同期されません。
* NFS ストレージのある vCenter Server インスタンスには、少なくとも 2 つの ESXi サーバーが必要です。 V2.1 以降にデプロイされたインスタンスの場合、デフォルト・クラスターについては、ESXi サーバーを最大 51 台まで配置して拡張できます。 デフォルト以外の各クラスターは、最大 59 台の ESXi サーバーを含むように拡張できます。
* vSAN ストレージのある vCenter Server インスタンスには、少なくとも 4 つの ESXi サーバーが必要です。
* F5 on {{site.data.keyword.cloud_notm}} サービスまたは FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスがインストールされている ESXi サーバーの場合は、そのサーバーを削除する前に、F5 BIG-IP と FortiGate の VM を、現時点で VM をホスティングしている ESXi サーバーとは別のサーバーにマイグレーションする必要があります。
* IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} サービスがインストールされている ESXi サーバーを削除する前に、アクティブな (失敗したか、進行中の) バックアップ操作またはリストア操作がないことを確認してください。こうしたアクティブな操作があると、ESXi サーバーが削除されない可能性があるためです。
* ESXi サーバーを削除する際には、そのサーバーは保守モードになります。その後、そこで実行されているすべての仮想マシン (VM) は、vCenter Server からそのサーバーが削除される前にマイグレーションされます。 VM の再配置を最大限に制御するために、VMware vSphere Web Client を使用して、手動により、削除する ESXi サーバーを保守モードにし、サーバーで実行されている VM を移行することをお勧めします。 その後、{{site.data.keyword.vmwaresolutions_full}} コンソールを使用して ESXi サーバーを削除します。
* V2.0 以前にデプロイされた vCenter Server インスタンスの場合、クラスターごとに、ESXi サーバーを最大 32 個まで配置して拡張できます。 一度に追加できる{{site.data.keyword.baremetal_short}}の数は、以下のとおりです。
   * **「スモール」**、**「ミディアム」**、**「ラージ」**の各構成では、一度に 1 から 10 個の ESXi サーバーを追加できます。
   * **「カスタマイズ型」**構成では、一度に 1 から 20 個の ESXi サーバーを追加できます。 最小限の ESXi サーバーについて詳しくは、[2 ノードの vCenter Server インスタンスの可用性は高いですか?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-) を参照してください。

## 手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を拡張または縮小するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを追加/削除するクラスターをクリックします。
5. ESXi サーバーを追加するには、以下の手順を実行します。
   1. **「ESXi サーバー」**セクションで**「追加」**をクリックします。
   2. **「サーバーの追加」**ウィンドウで、追加するサーバーの数を入力し、見積もりコストを確認して、**「追加」**をクリックします。
6. ESXi サーバーを削除するには、**「ESXi サーバー」**セクションで削除するサーバーを選択し、**「削除」**をクリックします。

## 結果

追加操作または削除操作を開始後、インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、インスタンス状況にわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。

ESXi サーバーを追加または削除する要求の処理中であることが、E メールで通知されます。 ESXi サーバーに関連付けられたクラスターの状況が、**「変更中」**に変更されます。 サーバーを削除すると、{{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクル (通常 30 日) の最後に、{{site.data.keyword.cloud_notm}} インフラストラクチャーによって ESXi サーバーに全面的な再利用処理が施されることにご注意ください。

**注意:** 削除した ESXi サーバーについては、 {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルが終了するまで課金されます。

リストに新しく追加した ESXi サーバーがクラスター内にない場合は、E メールかコンソールの通知を確認して、失敗に関する詳細を調べてください。

## 関連リンク

* [vCenter Server の部品構成表](vc_bom.html)
* [vCenter Server インスタンスの要件と計画](vc_planning.html)
* [vCenter Server インスタンスのクラスターの追加、表示、削除](vc_addingviewingclusters.html)
* [ホストをメンテナンス モードに切り替える](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}