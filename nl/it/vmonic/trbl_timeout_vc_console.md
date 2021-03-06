---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# Timeout raggiunto durante la connessione al client web VMware vSphere
{: #trbl_timeout_vc_console}

## Problema
{: #trbl_timeout_vc_console-problem}

Quando tenti di connetterti al client web vSphere, potresti visualizzare il seguente errore di timeout:

`The server at <IP_address> is taking too long to respond.`

## Risoluzione
{: #trbl_timeout_vc_console-resolution}

Utilizza la seguente procedura per analizzare e correggere il problema.

1. Assicurati di aver completato i passi dalla descrizione a comparsa che viene visualizzata quando passi con il mouse sul pulsante **Console vCenter**. Per
   comodità, di seguito vengono elencati questi passi:   
   1. Installa il plug-in Adobe Flash Player per il tuo browser.   
   2. Crea una password VPN dal {{site.data.keyword.slportal_full}}.    
   3. [Accedi alla VPN del data center](/docs/infrastructure/iaas-vpn?topic=VPN-gettingstarted-with-virtual-private-networking#login-to-the-vpn) utilizzando le credenziali VPN dell'infrastruttura {{site.data.keyword.cloud_notm}}.    
   4. Aggiungi l'associazione di indirizzo IP e nome host di PSC (Platform Services Controller) nel file `hosts` dal tuo computer locale. Utilizza il seguente formato:

      ```javascript
      IP_Address              Host_Name
      ```

2. Prendi nota dell'indirizzo IP che viene visualizzato perché ti servirà in uno dei passi successivi.
3. Assicurati di avere accesso alla VPN dell'infrastruttura {{site.data.keyword.cloud_notm}}. Completa la seguente procedura nel {{site.data.keyword.slportal}}:
   1. Fai clic su **Account > Accesso VPN**.
   2. Fai clic su **Link SSL** nella colonna **Accesso VPN**.
   3. Nella pagina **Accesso VPN per nome utente**, imposta l'opzione **Accesso alla sottorete** su **Manuale**.
   4. Nella stessa pagina, individua la sottorete per la coppia indirizzo IP/nome host. Per ulteriori informazioni, vedi il **Passo 2**.    

      Ad esempio, se l'indirizzo IP per la tua istanza è `xx.yyy.zz.15` e l'indirizzo IP per vCenter è `xx.yyy.zz.10`, devi concedere l'accesso per la sottorete `xx.yyy.zz.0/26`.

   5. Seleziona la casella di spunta **Concedi accesso** per tale sottorete e fai clic su **Salva**.
