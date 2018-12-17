---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# IBM Cloud のネットワーキングとインフラストラクチャー

## Virtual Routing and Forwarding (VRF)
{{site.data.keyword.cloud}} アカウントは、VRF アカウントとして構成することもできます。 VRF アカウントは VLAN スパンニングと同様の機能を提供し、サブネット IP ブロック間の自動ルーティングを可能にします。Direct Link 接続を使用するアカウントはすべて、VRF アカウントに変換するか、VRF アカウントとして作成する必要があります。

## Direct Link
{{site.data.keyword.cloud_notm}} Direct Link Connect を利用することで、ローカルの {{site.data.keyword.CloudDataCent_notm}}を経由した {{site.data.keyword.cloud_notm}} インフラストラクチャーへのプライベート・アクセスと、ネットワーク・サービス・プロバイダーにリンクされた他のクラウドへのプライベート・アクセスが実現します。 このオプションは、単一環境にマルチクラウド接続を作成する場合に最適です。
共有帯域幅トポロジーを使用して、お客様を {{site.data.keyword.cloud_notm}} Private ネットワークに接続します。 すべての Direct Link 製品と同様に、すべての {{site.data.keyword.cloud_notm}} ロケーションへのプライベート・ネットワーク・トラフィックを使用できるようにする、グローバル・ルーティングを追加できます。

## 仮想プライベート・ネットワーク

### strongSwan VPN
strongSwan IPSec VPN サービスは、業界標準の Internet Protocol Security (IPSec) プロトコル・スイートに基づき、インターネット上にセキュアなエンドツーエンドの通信チャネルを確立します。

### Hybridity (HCX)
VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle はオンプレミス・データ・センターのネットワークを {{site.data.keyword.cloud_notm}} にシームレスに拡張するので、変換も変更も行わずに {{site.data.keyword.cloud_notm}} との間で仮想マシン (VM) をマイグレーションできるようになります。


## 物理構造

vCenter Server クラスターをデプロイするために必要な物理インフラストラクチャーの最小仕様を次に示します。


表 1. vCenter Server の仕様

  | NFS デプロイメント | VSAN デプロイメント
---|---|---
サーバー数 | 3 | 4
CPU | 28 コア 2.2GHZ | 28 コア 2.2GHZ
メモリー | 384 GB | 384 GB
ストレージ|管理: 2 TB 2 IOPS、ワークロード: 2 TB 4 IOPS|最小 SSD: 960 GB(x2)   

IKS デプロイメント・オプションは、ワーカー・ノードの要件によって異なります。

表 2. IKS の仕様

  | 仮想マシン | ベア・メタル
--|---|--
サーバー数 | 3 | 3
CPU | 2 – 56 コア | 4 – 28 コア
メモリー | 4 GB - 242 GB | 32 GB - 512 GB
ストレージ | 100 GB |  SATA: 2 TB / SSD: 960 GB

## 仮想構造

図 1. IKS と ICP デプロイメントの物理構造

![IKS と ICP デプロイメントの物理構造](vcsiks-phy-ics-iks-deployment.svg)

vCenter Server インスタンス内で、お客様の VMS は専用の NSX
Edge Services Gateway (ESG) と分散論理ルーター (DLR) にデプロイされます。

アウトバウンド・トラフィックを許可するための SNAT が ESG に構成されて、インターネット接続で ICP 前提条件をダウンロードできるようになり、GitHub および Docker または Web プロキシーへの接続を使用してインターネット接続を行えます。 ESG はプライベート・ネットワークを介して DNS および NTP サービスにアクセスするように構成されています。
IKS インスタンスへの統合は、vCenter Server インスタンスと IKS の間の
{{site.data.keyword.cloud_notm}} ネットワーキングを介して可能です。

## vCenter Server コンポーネント

図 2. vCenter Server プラットフォーム・コンポーネント
![vCenter Server 環境の図](vcsiks-vcs-env.svg)

### Platform Service Controller
vCenter Server デプロイメントでは、管理 VM に関連付けられたプライベート VLAN 内のポータブル・サブネット上にインストールされた単一の外部プラットフォーム・サービス・コントローラー (PSC) を使用します。 このデフォルト・ゲートウェイは、バックエンド・カスタマー・ルーター (BCR) に設定されます。

### vCenter Server
PSC と同様に、vCenter Server はアプライアンスとしてデプロイされます。
また、vCenter は、管理 VM に関連付けられたプライベート VLAN 上のポータブル・サブネットにインストールされます。
このデフォルト・ゲートウェイは、BCR に設定されます。

### NSX Manager
NSX Manager は初期 vCenter Server クラスター内にデプロイされます。 また、NSX Manager は、管理コンポーネント用に指定されたプライベート・ポータブル・アドレス・ブロックの IP アドレスを割り当てられます。


### NSX Controller
{{site.data.keyword.cloud_notm}} の自動化機能によって、初期クラスター内に 3 つの NSX Controller がデプロイされます。 管理コンポーネント用に指定されたプライベート・ポータブル・サブネットから IP アドレスがコントローラーに割り当てられます。


### NSX ESG / DLR
NSX Edge Services Gateway (ESG) のペアがデプロイされます。 すべての場合において、プライベート・ネットワークに常駐する自動化コンポーネントからのアウトバウンド・トラフィックにゲートウェイ・ペアが 1 つ使用されます。 vCenter Server と ICP のための 2 つ目のゲートウェイ (ICP 管理エッジと呼ばれる) がデプロイされ、パブリック・ネットワークへのアップリンクとプライベート・ネットワークに割り当てられたインターフェースが構成されます。
分散論理ルーター (DLR)、論理スイッチ、ファイアウォールなどの必要な NSX コンポーネントは、管理者が構成できます。 ソリューションの一部としてデプロイされる NSX Edges について詳しくは、[vCenter Server ネットワーキング・ガイド](../vcsnsxt/vcsnsxt-intro.html)を参照してください。

次の表は、ICP ESG/DLR の仕様を要約したものです。

表 3. ICP ESG の仕様

属性 |  仕様
--|--
Edge Service Gateway | 仮想アプライアンス
Edge サイズ「大」 | vCPU 数	2
メモリー	| 1 GB
ディスク	| ローカル・データストアに 1000 GB

表 4. ICP DLR の仕様

属性  |  仕様
--|--|
分散論理ルーター |	仮想アプライアンス
Edge サイズ「コンパクト」 | vCPU 数	1
メモリー	| 512 MB
ディスク	| ローカル・データストアに 1000 GB

## IKS コンポーネント

図 3. IKS コンポーネント
![IKS コンポーネントの図](vcsiks-iks-components.svg)

### Kubernetes マスター

Kubernetes マスターは、クラスター内のすべてのコンピュート・リソース、ネットワーク・リソース、ストレージ・リソースを管理します。 Kubernetes マスターは、コンテナー化されたアプリとサービスがクラスター内のワーカー・ノードに均等にデプロイされるようにします。

###	ワーカー・ノード
各ワーカー・ノードは、物理マシン (ベア・メタル) であるか、クラウド環境内の物理ハードウェアで実行される VM です。 ワーカー・ノードをプロビジョンする際に、そのワーカー・ノード上でホストされるコンテナーで使用できるリソースを決定します。 すぐに使用できるように、ワーカー・ノードには、IBM 管理の Docker エンジン、別個のコンピュート・リソース、ネットワーキング、ボリューム・サービスがセットアップされます。 標準装備のセキュリティー機能は、分離機能、リソース管理機能、そしてワーカー・ノードのセキュリティー・コンプライアンスを提供します。

### 関連リンク

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](../vcs/vcs-hybridity-intro.html)