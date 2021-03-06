---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Aplicando atualizações às instâncias do vCenter Server
{: #vc_applyingupdates}

O processo de aplicação de correções e atualizações para instâncias do vCenter Server é automatizado somente para os componentes de gerenciamento. As atualizações do VMware devem ser aplicadas manualmente.

## Antes de iniciar
{: #vc_applyingupdates-prereq}

Ao fazer upgrade de uma instância do vCenter Server para uma instância do vCenter Server with Hybridity Bundle, deve-se primeiro aplicar pelo menos a atualização de software do vCenter Server V2.3 base. Deve-se fazer isso antes de poder executar o upgrade de licença para o Hybridity Bundle.
{:important}

Os usuários do Parceiro de Negócios não têm a opção de fazer upgrade de uma instância existente do vCenter Server para uma instância do vCenter Server with Hybridity Bundle.

Iniciando com a V2.5, as atualizações do IBM CloudDriver não são mais listadas porque as atualizações automáticas estão ativadas. Ações como a inclusão de um host, a inclusão de um cluster e a solicitação de um serviço atualizam automaticamente a instância para a versão mais recente. Para obter mais informações sobre atualizações automáticas, consulte a seção *Resiliência do IBM CloudDriver* em Notas sobre a liberação do [ para a V2.5](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-relnotes_v25).
{:note}

Antes de tentar aplicar uma atualização, expanda a entrada de atualização clicando na seta para baixo e verifique as informações a seguir:
* A versão da atualização. Deve-se aplicar as atualizações em sequência cronológica que é da mais antiga para a mais recente. Assegure-se de que tenha aplicado todas as atualizações anteriores antes de aplicar a mais recente. Por exemplo, deve-se aplicar a atualização V2.3 antes de tentar aplicar a atualização V2.4.
* Se o tempo de inatividade é necessário.
* O tempo estimado total para concluir a atualização.
* O impacto da atualização no ambiente virtual do VMware. A Tabela 1 mostra como os diferentes níveis de atualizações afetam o sistema.
* Os detalhes da atualização.

Tabela 1. Atualize os níveis e o impacto

<table>
  <tr>
    <th>Atualizar nível</th>
    <th>Impacto</th>
  </tr>
  <tr>
    <td>Baixo</td>
    <td>Esta atualização não afeta nenhum sistema. Não é necessário aplicá-lo durante o tempo de inatividade planejado.</td>
  </tr>
  <tr>
    <td>Médio</td>
  <td>Esta atualização pode afetar alguns sistemas. Recomenda-se aplicar durante o tempo de inatividade planejado.</td>
  </tr>
    <tr>
    <td>Grave</td>
  <td>Esta atualização afeta alguns ou todos os sistemas. Deve-se aplicá-lo durante o tempo de inatividade planejado.</td>
  </tr>
</table>

## Procedimento para aplicar atualizações e correções às instâncias do vCenter Server (V2.1 ou mais recente)
{: #vc_applyingupdates-procedure}

Este procedimento se aplica a instâncias que são implementadas na V2.1 ou mais recente. Para instâncias que são implementadas na V2.0 e anterior, deve-se aplicar as atualizações do VMware manualmente.

1. No console do {{site.data.keyword.vmwaresolutions_full}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância a ser atualizada.
3. Na página **Resumo**, verifique se todos os detalhes da instância são exibidos corretamente. Em seguida, clique em **Infraestrutura** na área de janela de navegação esquerda para verificar os detalhes na página **Infraestrutura**.
   Se os detalhes não forem exibidos, isso poderá indicar um problema de conectividade com a Virtual Server Instance (VSI) do IBM CloudDriver, como resultado de uma regra de firewall ou outro problema de rede. Resolva o problema antes de continuar com a próxima etapa, caso contrário, a atualização poderá falhar.
4. Clique em **Atualização e correção** na área de janela de navegação esquerda.

   A página **Atualização e correção** para uma instância contém somente os pacotes para atualizar os componentes de gerenciamento da IBM e não as atualizações do VMware. Atualizações do VMware devem ser aplicados manualmente.   O {{site.data.keyword.vmwaresolutions_short}} aplica atualizações do VMware às operações a seguir:
   * Quando uma nova instância do vCenter Server é implementada.
   * Quando novos servidores do ESXi forem incluídos, os novos servidores do ESXi serão provisionados com atualizações do VMware, mas os servidores do ESXi existentes não serão atualizados.
   * Quando novos clusters forem incluídos, os novos clusters serão provisionados com atualizações do VMware, mas os clusters existentes não serão atualizados.
   {:note}

5. Para upgrades de licença NSX, clique em  ** Upgrade **. Na janela **Atualizar NSX License Edition**, selecione a edição para a qual deseja fazer upgrade e clique em **Atualizar**. Downgrades da edição da licença não estão disponíveis.

   O upgrade de licença substitui todas as licenças NSX existentes na instância. Poderão incorrer encargos adicionais de uma sobreposição de licenças antigas e novas se você fizer upgrade no meio de um ciclo de faturamento. Para evitar encargos adicionais, recomenda-se fazer upgrade da licença no final do ciclo de faturamento.
   {:note}

6. Para atualizações de software, clique na seta para baixo para expandir a atualização que você deseja aplicar e, em seguida, conclua uma das etapas a seguir:
   *  Para iniciar a atualização imediatamente, clique no ícone de menu overflow na coluna **Ações** da entrada de atualização e, em seguida, clique em **Atualizar agora**.
   *  Para planejar uma atualização futura, clique no ícone de menu overflow na coluna **Ações** da entrada de atualização e, em seguida, clique em **Planejar atualização**. Selecione a data, o horário e o fuso horário quando desejar que a atualização seja iniciada. Clique em **OK**.
7. Se você estiver aplicando atualizações a instâncias de servidores vCenter na configuração de implementação de vários sites, uma seção intitulada **Etapas Necessárias para Atualização** será exibida. Esta seção lista as operações de atualização necessárias para todas as instâncias na implementação de vários sites. Deve-se concluir as etapas em sequência clicando em **Aplicar atualização** para cada etapa. Deve-se aguardar a conclusão da etapa anterior antes de iniciar a próxima etapa.   

## Procedimento para fazer upgrade para a instância do vCenter Server with Hybridity Bundle
{: #vc_applyingupdates-procedure-upgrade-to-hybridity}

Durante o upgrade de licença para o Hybridity Bundle, será feito upgrade automaticamente para o VMware NSX Advanced Edition se sua instância do vCenter Server estiver usando atualmente o VMware NSX Base Edition.

Se fizer upgrade para o Hybridity Bundle e sua instância do vCenter Server já tiver o armazenamento de arquivo NFS, você não será cobrado pelo armazenamento vSAN do VMware. Você será cobrado pela licença vSAN porque ela está incluída no Bundle Hybridity.
{:note}

Conclua as etapas a seguir para fazer upgrade de uma instância do vCenter Server para o vCenter Server with Hybridity Bundle.

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para fazer upgrade.
3. Na página **Resumo**, verifique se todos os detalhes da instância são exibidos corretamente. Em seguida, clique em **Infraestrutura** na área de janela de navegação esquerda para verificar os detalhes na página **Infraestrutura**.
   Se os detalhes não forem exibidos, isso poderá indicar um problema de conectividade com o IBM CloudDriver VSI, como resultado de uma regra de firewall ou de outro problema de rede. Resolva o problema antes de continuar com a próxima etapa, caso contrário, a atualização poderá falhar.
4. Clique em **Atualização e correção** na área de janela de navegação esquerda.
5. Aplique o upgrade de licença do pacote configurável. Na tabela **Upgrades de licença**, clique em **Fazer upgrade** na coluna **Ação**, revise o custo estimado e clique em **Fazer upgrade**.
6. Opcionalmente, implemente o serviço VMware HCX on {{site.data.keyword.cloud_notm}}. Quando o Hybridity Bundle estiver ativado na tabela **Upgrades**, conclua as etapas a seguir:
  1. Na tabela **Upgrades de licença**, clique em **Implementar o HCX on {{site.data.keyword.cloud_notm}}** na coluna **Ação**.
  2. Role para o cartão **HCX on {{site.data.keyword.cloud_notm}}** e clique em **Selecionar serviço**.
  3. Role para baixo e especifique as configurações necessárias para o serviço e clique em **Avançar**.
  4. Revise os termos que se aplicam ao serviço, revise o custo estimado e clique em **Fazer pedido**.

## Resultados
{: #vc_applyingupdates-results}

1. Depois que uma atualização for aplicada, aparecerá um registro na lista de status de atualização de software, no qual é possível visualizar o progresso detalhado e o status da atualização. Quando a atualização for concluída com êxito, um registro aparecerá na lista de atualizações de softwares instalados.

  Para recuperar o status mais recente para uma tarefa de atualização, clique no ícone de atualização no canto superior direito da página.
  {:tip}

2. Para obter detalhes sobre os status de atualização, veja a tabela a seguir.

   Tabela 2. Detalhes de status de atualização

    <table>
      <tr>
        <th>Status</th>
        <th>Detalhes</th>
      </tr>
      <tr>
        <td>Disponível</td>
        <td>A atualização está disponível para ser aplicada. Não é possível selecionar uma atualização disponível até que todas as suas atualizações anteriores sejam aplicadas.</td>
      </tr>
      <tr>
        <td>Em andamento</td>
      <td>A tarefa de atualização foi iniciada, mas não foi concluída ainda. Não será possível aplicar nenhuma outra atualização até que a tarefa de atualização atual esteja concluída. </td>
      </tr>
        <tr>
        <td>Instalado</td>
      <td>A tarefa de atualização está concluída. O componente correspondente da plataforma VMware foi atualizado.</td>
      </tr>
        <tr>
        <td>Com falha</td>
      <td>A tarefa de atualização falha. O console relata um erro para a falha de atualização. Revise o erro e corrija o problema relatado antes de reaplicar a atualização.</td>
      </tr>
          <tr>
        <td>Planejado</td>
      <td>A tarefa de atualização está planejada para um momento posterior. A tarefa de atualização é iniciada automaticamente no momento planejado.</td>
      </tr>
          <tr>
        <td>Desconhecido</td>
      <td>O status da tarefa de atualização não pode ser obtido. Entre em contato com o Suporte IBM para obter assistência.</td>
      </tr>
    </table>

3. Se o processo de atualização falhar em uma etapa específica, [entre em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) para obter assistência. Você será avisado sobre como resolver o problema e orientado a tentar o upgrade novamente a partir da etapa que falhou.

## Links relacionados
{: #vc_applyingupdates-related}

* [Visão geral do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas Mais Frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
