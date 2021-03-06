---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Visão geral do KMIP for VMware on IBM Cloud - Descontinuado
{: #kmip_considerations}

A versão atual do KMIP for VMware on IBM Cloud está sendo descontinuada. Para obter mais informações, [entre em contato com o suporte IBM](../vmonic/trbl_support.html).
{:deprecated}

O serviço KMIP para VMware no {{site.data.keyword.cloud}} fornece um serviço altamente disponível 24 horas por dia, 7 dias por semana para gerenciar chaves de criptografia que são usadas pelo VMware no {{site.data.keyword.cloud_notm}}. Esse serviço oferece a capacidade de tempo de execução para permitir que os clientes criem, recuperem, ativem, revoguem e destruam as chaves de criptografia. Ele também fornece a capacidade de gerenciamento para manter as
associações entre as credenciais do cliente e as chaves de criptografia.

## Especificações técnicas para o KMIP for VMware on IBM Cloud
{: #kmip_considerations-specs}

As especificações a seguir são incluídas com o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}:

* Um Key Management Interoperability Protocol (KMIP) compatível com VMware
* Um serviço gerenciado
* Disponível em múltiplas regiões geográficas em todo o mundo
* Um terminal de serviço KMIP altamente disponível em cada região

## Considerações ao instalar o KMIP for VMware on IBM Cloud
{: #kmip_considerations-install}

O KMIP for VMware on {{site.data.keyword.cloud_notm}} usa o serviço IBM Key Protect for {{site.data.keyword.cloud_notm}} para criar, criptografar e decriptografar chaves de criptografia. Portanto, antes de instalar o KMIP for VMware on {{site.data.keyword.cloud_notm}}, assegure-se de que:
* Você pediu um serviço Key Protect utilizável.
* Um ID do serviço {{site.data.keyword.cloud_notm}} foi criado seguindo as etapas em
[Criando um ID do serviço](../../../iam/serviceid.html). Esse ID do
serviço é usado para acessar a instância do serviço Key Protect que você criou.
* Você concedeu os seguintes níveis de acesso para o ID do serviço:
   * No nível de acesso de plataforma: autoridade de visualizador para sua instância do IBM Key Protect.
   * No nível de acesso de serviço: autoridade de gravador para sua instância do IBM Key Protect.
* Você tem uma chave API para o ID do serviço criado. A chave é necessária ao pedir o serviço.
* Você criou pelo menos uma chave raiz do cliente (CRK) por meio da interface com o usuário do Key Protect seguindo as
etapas em [Criando as
chaves raiz](../../keymgmt/keyprotect_create_root.html) ou usando a API de REST no [IBM Key
Protect](https://cloud.ibm.com/apidocs/key-protect).

   **Importante:** não é possível pedir o serviço sem CRKs. É altamente recomendado que você use o método
para criar uma CRK utilizando o material de chave existente e faça backup do material de chave que você está criando. Ao fazer isso, você assegura que poderá recuperar suas chaves se ocorrer uma falha do data center no qual o IBM Key Protect é aplicado para armazenar seus CRKs.

## Considerações ao usar o KMIP for VMware on IBM Cloud
{: #kmip_considerations-use}

* Para usar um serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} pedido como um Key Management
Server (KMS) que está registrado para o VMware vCenter Server, assegure-se de que a conectividade de rede do vCenter Server para o terminal
do serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} pedido esteja funcional.
* Para usar o serviço com a criptografia do VMware vSAN, assegure-se de que a conectividade de rede entre os hosts no vSAN de destino e o terminal do serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} esteja funcional.
* Quando você usa o KMIP for VMware com a criptografia vSAN, a verificação de funcionamento do vSAN pode emitir avisos periódicos de que ele não é capaz de se conectar ao cluster do KMS por meio de um ou mais hosts vSphere. Esses avisos ocorrem porque a conexão de verificação de funcionamento do vSAN atinge o tempo limite muito rapidamente. É possível ignorar esses avisos.

## Considerações ao remover o KMIP for VMware on IBM Cloud
{: #kmip_considerations-remove}

O certificado público do VMware fornecido durante o pedido ou quando você usa o serviço é usado como o certificado de cliente para se comunicar com a instância de serviço. Quando o serviço é removido, todas as chaves de criptografia que são criadas por essa instância de serviço para o certificado público do VMware associado também são removidas.

Portanto, antes de remover o serviço, assegure-se de que nenhuma máquina virtual ou vSAN esteja sendo criptografada usando as chaves que são criadas pelo serviço KMIP.

## Links relacionados
{: #kmip_considerations-related}

* [ Solicitando KMIP para VMware no  {{site.data.keyword.cloud_notm}} ](kmip_ordering.html)
* [Eventos do {{site.data.keyword.cloudaccesstrailshort}}](../vmonic/at-events.html)
* [IBM Key Protect para {{site.data.keyword.cloud_notm}}](../../keymgmt/index.html)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
