---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight のデプロイメント・モデル
{: #caveonix-deploy}

このセクションでは、Caveonix RiskForesight のデプロイメント・モデル、およびソリューションをインストールするためのインストール・プロセスについて説明します。

{{site.data.keyword.vmwaresolutions_full}} RiskForesight オプションを選択する場合、デプロイメントの初期の手順は自動化されているので、すべての手順をユーザーが実行する必要はありません。 ただし、デプロイメントとアーキテクチャーの全体像を理解するときや、初期デプロイメントの後にソリューションをスケールアウトするときには、詳細について理解しておく必要があります。

RiskForesight のインストールに含まれる手順の概要は以下のとおりです。

1. [初期の計画立案と前提条件](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step1) – デプロイメント・オプションを理解して選択します。アプリケーション・コンポーネント用に FQDN/IP の解決を行うために DNS を構成します。
2. [仮想マシンのデプロイメント](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step2) – OVF テンプレートから VM をデプロイします。 VM にはすべてのアプリケーション・コンポーネントがインストールされています。
3. [アプリケーションの構成](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step3) – 各 VM のアプリケーション・コンポーネントを構成する Caveonix 構成スクリプトを実行します。
4. [アプリケーションのセットアップ](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step4) – サービス・プロバイダーと、テナントまたは組織をセットアップして、ユーザーがアプリケーションにアクセスできるようにします。

自動インストールによって、1 つの VM がプロビジョンされ、その VM にすべてのアプリケーション・コンポーネントが構成されます。
{:note}

## デプロイメントのサイズ
{: #caveonix-deploy-sizing}

デプロイメントのサイズは、以下のボリュームを使用して算出されます。

表 1. ボリューム

|データ・タイプ	|ボリューム |
|---|---|
|日次のスキャン回数	|1 |
|スキャン・データ (MB)	|20 |
|ログ・データ (MB)	|500 |
|フロー・データ (MB)	|200 |
|資産データ (MB)	|46 |
|日次の資産ごとのストレージ合計 (MB)	|766 |
|データ・レプリケーション乗数	|2 |
|索引ストレージ合計 / 資産 / 日 (MB)	|1532 |

索引ストア (Elastic Search) はデフォルトで索引の n+1 個のレプリケーションを使用するので、データ・レプリケーション乗数は 2 に設定されます。
{:note}

スケーリング VM の数は、アセットの数、および索引作成するデータの日数から計算されます。

表 2. スケーリング VM のパラメーター

|資産の数	|100	|500	|5000 |
|---|---|---|---|
|データの日数	|30	|30	|30 |
|索引ストレージ合計 / 資産 / 日 (MB)	|1532	|1532	|1532 |
|索引ストレージ合計 / 資産 / 30 日 (TB)	|4	|22	|219 |
|スケーリング・ノードごとのサポートされるデータ (TB)	|0	|8	|8 |
|必要なスケーリング VM	|0	|3	|27 |

必要なストレージの量は、以下の方法で計算されます。

表 3. ストレージのパラメーター

|資産の数	|100	|500	|5000 |
|---|---|---|---|
|長期データ保存 (月数)	|8	|8	|8 |
|日次の資産ごとのストレージ合計 (MB)	|766	|766	|766 |
|データの日数	|30	|30	|30 |
|短期データ保存 (TB)	|7	|33	|329 |
|長期データ保存 (TB)	|18	|88	|877 |

データの観点から見ると、データは以下のように使用されます。

-	スキャン・データはコンプライアンス管理で使用されます
-	ログ・データはフォレンジック管理で使用されます
-	ポリシーおよびフロー・データはリスク管理で使用され、フロー・データは NSX Manager からのみ使用できます

データ・ストレージには、以下の 3 つの層があります。

-	複製
-	短期
-	長期

以下の表に、デプロイメントの要約を示します。

表 4. 要約

|デプロイメント・モデル	|「オールインワン」	|部分分散	|完全分散 |
|---|---|---|---|
|資産の数	|100	|500	|5000 |
|30 日間に生成されたオンライン・データ (TB)	|4	|22	|219 |
|ニアライン・データ保存 (90 日) (TB)	|7	|33	|329 |
|オフライン・データ保存 (8 カ月) (TB)	|18	|88	|877 |
|合計データ・ストレージ保存 (1 年) (TB)	|28	|142	|1425 |
|基本 VM の数	|1	|1	|20 |
|スケーリング VM の数	|0	|3	|28 |
|VM の合計数	|1	|4	|48 |

## 関連リンク
{: #caveonix-deploy-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)