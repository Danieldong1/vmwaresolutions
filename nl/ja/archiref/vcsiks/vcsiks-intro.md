---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# vCenter Server および IBM Kubernetes サービスの概要

このドキュメントでは、{{site.data.keyword.cloud}} へのアプリケーション・モダナイゼーション・ジャーニーについて、マルチクラウド統合環境をアプリケーション・モダナイゼーションで使用できるようにする次のプラットフォームのネットワークの側面に焦点を当てて説明します。

このドキュメントでは、{{site.data.keyword.cloud_notm}} へのアプリケーション・モダナイゼーションについて、マルチクラウド統合環境をアプリケーション・モダナイゼーションで使用できるようにするクラウド管理コンポーネントに焦点を当てて説明します。

- **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - vCenter Server は、{{site.data.keyword.vmwaresolutions_full}} のオファリングであり、{{site.data.keyword.cloud_notm}} 上で自動的にプロビジョンされる VMware ベースのプラットフォームです。
- **{{site.data.keyword.cloud_notm}} Private** - ICP はコンテナー化アプリケーションを開発および管理するためのアプリケーション・プラットフォームです。コンテナー化アプリケーションは、VMware などの仮想化インフラストラクチャー・プラットフォームにデプロイされます。
- **IBM Kubernetes Services** - IKS は、オーケストレーション・エンジンとして Kubernetes を使用してシングル・テナント・クラスターのアプリケーション・コンテナーのデプロイ、スケーリング、および運用を自動化する {{site.data.keyword.cloud_notm}} のマネージド・サービスです。
- **IBM Multi-Cluster Manager** – MCM は、複数のクラウドおよびクラスターにおけるユーザー可視性、アプリケーション中心の管理 (ポリシー、デプロイメント、正常性、操作)、ポリシー・ベースのコンプライアンスを提供します。 MCM を使用することで、Kubernetes クラスターを制御できます。
- **{{site.data.keyword.cloud_notm}} Automation Manager** – CAM は、ICP 上で実行されるマルチクラウド・セルフサービス管理プラットフォームであり、開発者と管理者がビジネス要求に対応できるようにします。

## IBM Cloud でのアプリケーション・モダナイゼーション
アプリケーション・モダナイゼーションとは、既存のアプリケーションを移行してクラウド上の新しいアプローチを使用するプロセスを表す用語です。 昨今のお客様は、ビジネスやアプリケーションの複雑さに基づいてこの移行を行うために役立つ革新的で効率的なアプローチを模索しています。

ビジネスのプレッシャーにより、市場投入までの時間を短縮することが求められています。 お客様の既存の資産には、アプリケーションだけでなく、データ、プロセス、ビジネス・ロジック、ユーザー・インターフェースが含まれ、これらはすべて、新しいビジネス要求に対応するための適合が必要になっています。

アプリケーション・モダナイゼーションの利点には、以下が含まれます。
- 開発者の生産性の向上。
- 運用効率の向上。
- 新しい機能を構築するためのコストの削減。
- 短時間でのキャパシティー拡張の実現。

IBM は、プライベート・クラウドの 70% が、アプリケーション環境をモダナイズする必要性によって導入されたものであると認識しています。しかし、ほとんどの組織は段階的なアプローチでアプリケーション・モダナイゼーションを進めているので、以下のようなハイブリッドやマルチクラウドの環境が必要になっています。
- メインフレームまたは UNIX システムで通常実行される一体構造の複雑なレガシー・アプリケーションは、オンプレミスのまま運用されます。
- SoR (Systems of Record、定型業務処理システム) で使用される x86 環境、あるいは、セキュリティー・センシティブなワークロードまたは規制されたワークロードのアプリケーションは、仮想化インフラストラクチャーまたはプライベート・クラウドに配置されます。
- SAP やハイパフォーマンス・コンピューティングなどのアプリケーションは、ベアメタル・リソースを消費します。
- パブリック・クラウドに移行できる、セキュリティー・センシティブなワークロードと規制されたワークロードは、専用の環境に移行します。
- Web、モバイル、IoT、AI、ビデオなどの SoE (Systems of Engagement、協働のための情報活用システム) は、パブリック・クラウドに移動します。

例えば、一般的なパターンは、フロントエンド SOE アプリケーションをコンテナーとしてデプロイし、データベースとレガシー・ミドルウェアをプライベート・クラウド上の VM にデプロイすることです。

お客様の IT インフラストラクチャー・ニーズとビジネス・ニーズはそれぞれ固有であるため、ビジネス価値の提供を促進し、リスクを軽減し、既存の投資を無駄にしないようにするモダナイゼーションへのアプローチが必要になります。 IBM は、アプリケーション・モダナイゼーションに関連するお客様固有のビジネス・ニーズとテクノロジー・ニーズに対応するようにカスタマイズできる、まさにそのようなアプローチを提供しています。

このドキュメントは、アプリケーション・モダナイゼーションの手順を経て {{site.data.keyword.cloud_notm}} に移行するまでに使用されるテクノロジーに関するさまざまな情報を提供する以下の 5 つのドキュメントの 1 つです。

* [vCenter Server および {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html) - 以下のプラットフォームをデプロイするためのリファレンス・アーキテクチャー。
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - {{site.data.keyword.vmwaresolutions_full}} のオファリングであり、{{site.data.keyword.cloud_notm}} に自動的にプロビジョンされる VMware ベースのプラットフォームです。
  - **{{site.data.keyword.cloud_notm}} Private** – コンテナー化されたアプリケーションを開発して管理するためのアプリケーション・プラットフォームです。 ICP は、コンテナー・オーケストレーター Kubernetes、プライベート・イメージ・リポジトリー、管理コンソール、モニター・フレームワーク、グラフィカル・ユーザー・インターフェースで構成される統合環境であり、ユーザーがアプリケーションのデプロイ、管理、モニター、スケーリングを行うことができる一元的な場所を提供します。
  - **{{site.data.keyword.cloud_notm}} Automation Manager** – エンタープライズ対応の Infrastructure as Code (IaC) プラットフォームであり、リポジトリーで保管およびバージョン管理されるテンプレートを使用するだけで、単一画面で VM ベースのワークロードと Kubernetes ベースのワークロードをプロビジョンできます。
* [vCenter Server および {{site.data.keyword.cloud_notm}} Private](../vcsiks/vcsiks-intro.html) - 以下のプラットフォームをデプロイするためのリファレンス・アーキテクチャー。
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - {{site.data.keyword.vmwaresolutions_full}} のオファリングであり、{{site.data.keyword.cloud_notm}} に自動的にプロビジョンされる VMware ベースのプラットフォームです。
  - **{{site.data.keyword.cloud_notm}} Kubernetes Service** – シングル・テナント・クラスターを対象としたアプリケーション・コンテナーのデプロイメント自動化、スケーリング、および運用を行うオーケストレーション・エンジンとして Kubernetes を使用する、{{site.data.keyword.cloud_notm}} 上の管理対象サービス。
* [vCenter Server ネットワーキング](../vcsnsxt/vcsnsxt-intro.html) - vCenter Server、ICP、および IKS 内で使用されるネットワーク・テクノロジー (NSX-V、NSX-T、Calico など) に焦点を当てて説明しています。
* [VMware および Skate Advisor コンセプト・カー](../vcscar/vcscar-intro.html) - このリファレンス・アーキテクチャーは、「コンセプト・カー」です。つまり、現実の世界の問題を解決するテクノロジーに焦点を当てて見せるためのメカニズムです。 IBM が実演したかったのは、Watson AI と機械学習の対話です。スケートボードの文化を通してユニークな方法でクラウド・サービスを披露しています。 この「コンセプト・カー」は、Skate Advisor という Acme Skateboard アプリケーションの機能拡張として実装されています。 Skate Advisor は、Watson 駆動型エンジンとの間でスケートボードの技についての会話ができるツールです。
* [VMware: Stock Trader のモダナイゼーション・ジャーニー](../vcscontent/vcscontent-modjourney.html) - このリファレンス・ユース・ケースでは、クラシックな WebSphere Application Server アプリケーションを、{{site.data.keyword.cloud_notm}} Private、IBM Middleware コンテンツ、{{site.data.keyword.cloud_notm}} Kubernetes Service、および vCenter Server on {{site.data.keyword.cloud_notm}} を利用してモダナイズする方法について説明しています。 だれもがクラウド・ジャーニーの途上にいますが、ジャーニーのどの段階にいるかは人それぞれです。アプリケーション設計者 Jane とクラウド・インフラストラクチャー設計者 Todd が段階的に手順を踏んで、Stock Trader という既存のアプリケーションをモダナイズしていきます。 ここでは、ジャーニーで各段階を進むときに参考になる例、および各段階の規模に関係なくビジネスに実現される価値を示します。 アプリケーション、DevOps、統合、および管理という 4 つのテーマに焦点を当てています。 各テーマは連携して目標の実現を助けます。つまり、他を残して 1 つのテーマだけをモダナイズしてもまったくうまくいきません。

### 関連リンク

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](../vcs/vcs-hybridity-intro.html)