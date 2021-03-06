---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud y supresión de la prueba de un solo nodo para instancias de VMware vCenter Server on IBM Cloud
{: #vc_trial_hybrid_orderinginstance}

La prueba de un solo nodo de VMware vCenter Server on {{site.data.keyword.cloud}} es una nube privada alojada de un solo arrendatario que proporciona la pila de VMware vSphere como servicio. Aunque el entorno gestionado por el cliente se suele desplegar con un mínimo de tres nodos, esta versión de prueba de un solo nodo proporciona un método de bajo coste para experimentar las ventajas de una implementación de nube híbrida.

Esta versión de prueba es ideal para una prueba de concepto que demuestra la velocidad de la automatización avanzada de IBM para el despliegue inicial y la facilidad de mover cargas de trabajo sencillas que no sean de producción a la nube. Mediante VMware Hybrid Cloud Extension (HCX), puede ampliar de forma segura su red de centro de datos local al {{site.data.keyword.CloudDataCent_notm}}, al tiempo que reduce la complejidad de configurar la interconexión en la red. HCX abstrae los recursos de red subyacentes para desplazarlos a través de Internet público de modo que pueda mover sin problemas las cargas de trabajo bidireccionalmente sin necesidad de volver a asignar IP a las máquinas virtuales (VM). Con HCX, no es necesario tener VMware NSX instalado de forma local y es compatible con versiones anteriores de vSphere.  

La prueba de un solo nodo solo es para prueba de concepto. No ejecute cargas de trabajo de producción en este entorno. Las funciones de gestión, como la adición y eliminación de hosts y clústeres, la solicitud de servicios complementarios adicionales y la aplicación de actualizaciones, no reciben soporte.
{:important}

Esta versión de prueba está pensada para utilizarla durante un máximo de 90 días. Cuando finalice el periodo de prueba, puede suprimir este entorno y luego suministrar un entorno de alta disponibilidad que se ajuste a sus necesidades de capacidad.

Para obtener información sobre el diseño de la arquitectura, consulte [Diseño de la arquitectura de HCX on IBM Cloud para la prueba de un solo nodo de vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/archiref/trial/vc_trial_hcx_arch.html).

## Especificaciones técnicas de la versión de prueba de un solo nodo de instancias de vCenter Server
{: #vc_trial_hybrid_orderinginstance-specs}

En la versión de prueba de un solo nodo de la instancia de vCenter Server se incluyen los siguientes componentes:

La disponibilidad y los precios de las configuraciones estandarizadas de hardware pueden variar en función del {{site.data.keyword.CloudDataCent_notm}} seleccionado para el despliegue.
{:note}

### Servidor nativo
{: #vc_trial_hybrid_orderinginstance-bare-metal}

Un procesador Dual Intel Xeon Gold 5120 (28 núcleos, 2,20 GHz) con 384 GB de RAM.

### Especificaciones de red de la versión de prueba de un solo nodo de instancias de vCenter Server
{: #vc_trial_hybrid_orderinginstance-networking-specs}

Se solicitan los siguientes componentes del sistema de redes:
*  Enlaces ascendentes de red pública y privada de 10 Gbps
*  Tres VLAN (LAN virtuales): una VLAN pública y dos VLAN privadas
*  Se despliega una VXLAN (LAN extensible virtual) con DLR (direccionador lógico distribuido) para una potencial comunicación este-oeste entre cargas de trabajo locales conectadas a redes de la capa 2 (L2). La VXLAN se despliega como una topología de direccionamiento de ejemplo, que puede modificar o eliminar o a la que puede añadir componentes. También puede añadir zonas de seguridad por conectar VXLAN adicionales a las nuevas interfaces lógicas del DLR.
*  Dos VMware NSX Edge Services Gateways:
  * Una Edge Services Gateway (ESG) de NSX de VMware de servicios de gestión segura para el tráfico de gestión de HTTPS saliente, desplegado por IBM como parte de la topología del sistema de redes de gestión. Las VM de gestión de IBM utilizan esta ESG para comunicarse con componentes externos específicos de gestión de IBM que están relacionados con la automatización.

    El usuario no puede acceder ni utilizar esta ESG. Si lo modifica, es posible que no pueda gestionar la prueba de un solo nodo para la instancia de vCenter Server desde la consola de {{site.data.keyword.vmwaresolutions_short}}. Además, tenga en cuenta que el uso de un cortafuegos o la inhabilitación de las comunicaciones ESG con componentes externos de gestión de IBM harán que {{site.data.keyword.vmwaresolutions_short}} quede inutilizable.
    {:important}
  * Una Edge Services Gateway de NSX de VMware gestionada por el cliente para el tráfico de salida y de entrada de carga de trabajo HTTPS, que IBM despliega como plantilla que puede modificar para proporcionar acceso VPN o acceso público.

### Instancias de servidor virtual
{: #vc_trial_hybrid_orderinginstance-vsi}

Se solicitan las siguientes instancias de servidor virtual (VSI):
* Una VSI para IBM CloudBuilder, que se cancela una vez completado el despliegue de la instancia.
* Se despliega y se puede consultar una VSI de Microsoft Windows Server para Microsoft Active Directory (AD). La VSI funciona como el DNS para la instancia en la que se han registrado los hosts y las máquinas virtuales.

### Licencias proporcionadas por IBM y tarifas
{: #vc_trial_hybrid_orderinginstance-license-and-fee}

En la versión de prueba de un solo nodo de la solicitud de una instancia de vCenter Server se incluyen las siguientes licencias:
* VMware vSphere Enterprise Plus 6.5
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

La versión de prueba de un solo nodo de instancias de vCenter Server no admiten la opción de traer su propia licencia.
{:note}

## Especificaciones técnicas de VMware HCX on IBM Cloud
{: #vc_trial_hybrid_orderinginstance-hcx-tech-specs}

La prueba de un solo nodo para vCenter Server incluye HCX on {{site.data.keyword.cloud_notm}}. Los componentes siguientes se solicitan y se incluyen en el servicio HCX on {{site.data.keyword.cloud_notm}}.

Las instancias de HCX locales incluyen solo la licencia y la activación.
{:note}

### Un par activo/pasivo de pasarelas de servicio VMware NSX Edge para la gestión de HCX
{: #vc_trial_hybrid_orderinginstance-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### Dispositivo de gestión HCX - máquina virtual
{: #vc_trial_hybrid_orderinginstance-hcs-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: 60 GB VMDK

Los dispositivos HCX adicionales se despliegan durante la configuración, según sean necesarios para la conectividad de L2, la optimización de WAN y las conexiones de pasarela.

### Especificaciones de red para el servicio HCX on IBM Cloud
{: #vc_trial_hybrid_orderinginstance-hcx-networking-specs}

* Una subred portátil pública con 16 direcciones IP
* Dos subredes portátiles privadas con 64 direcciones IP
* Ocho direcciones IP desde una subred vMotion portátil privada

## Requisitos y planificación para solicitar una versión de prueba de un solo nodo para instancias de vCenter Server
{: #vc_trial_hybrid_orderinginstance-req}

Asegúrese de cumplir con los siguientes requisitos y de haber completado las tareas siguientes:
* Requisitos para instancias locales de HCX:
 * Requiere VMware vSphere y vCenter 5.5 o superior.
 * El entorno de vSphere debe tener conmutadores distribuidos para el VMx que se migrará a {{site.data.keyword.cloud_notm}}.
 * El dispositivo virtual de HCX Manager debe poder desplegarse en una red privada en el entorno local y debe tener permiso para acceder a Internet público.
 * Para utilizar {{site.data.keyword.vmwaresolutions_short}} para solicitar instancias, debe tener una cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer). El coste de los componentes que se solicitan en las instancias se factura a dicha cuenta de {{site.data.keyword.cloud_notm}}.
 *  Configure las credenciales de la infraestructura {{site.data.keyword.cloud_notm}} en la página **Configuración**. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Valores** en el panel de navegación de la izquierda.
 * Revise los requisitos del nombre de la instancia:
    * Solo se permiten caracteres alfanuméricos y el guión (-).
    * El nombre de instancia debe empezar y terminar por un carácter alfanumérico.
    * La longitud máxima del nombre de instancia es de 10 caracteres.
    * El nombre de instancia debe ser exclusivo dentro de su cuenta.

## Procedimiento para solicitar la versión de prueba de un solo nodo para instancias de vCenter Server
{: #vc_trial_hybrid_orderinginstance-procedure}

1. En la página **Prueba de un solo nodo para VMware vCenter Server on {{site.data.keyword.cloud_notm}}**, pulse **Continuar**.
2. En la página **Prueba de un solo nodo para VMware vCenter Server**, siga los pasos para solicitar una cuenta de la infraestructura {{site.data.keyword.cloud_notm}} o especifique su **Nombre de usuario** y **Clave de API** existentes y pulse **Recuperar**.

 Esta sección está oculta si la clave de API ya existe.
 {:note}
3. Escriba el nombre de la instancia.
4. Seleccione el {{site.data.keyword.CloudDataCent_notm}} que va a alojar la instancia.  

 De forma predeterminada, aparece preseleccionado el {{site.data.keyword.CloudDataCent_notm}} DAL09. Seleccione otra ubicación de {{site.data.keyword.CloudDataCent_notm}} si es necesario.
 {:note}
5. En el panel **Resumen del pedido**, verifique la configuración de la instancia antes de realizar el pedido.
   1. Revise los valores de la instancia.
   2. Revise el coste estimado de la instancia. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen del pedido, pulse el icono **Imprimir** o **Descargar** en la parte superior derecha de la ventana del PDF.
   3. Pulse el enlace o enlaces de los términos que se aplican a su pedido y confirme que acepta estos términos antes de solicitar la instancia.
   4. Pulse **Suministro**.

### Resultados
{: #vc_trial_hybrid_orderinginstance-results}

El despliegue de la instancia comienza automáticamente y solicita la clave de activación del servicio HCX on {{site.data.keyword.cloud_notm}} local.

#### Proceso de despliegue de HCX on IBM Cloud
{: #vc_trial_hybrid_orderinginstance-hcs-deploy-process}

El despliegue de HCX on {{site.data.keyword.cloud_notm}} es automático. El proceso de automatización de {{site.data.keyword.vmwaresolutions_short}} lleva a cabo los siguientes pasos:
1. Se solicitan tres subredes para HCX desde la infraestructura de {{site.data.keyword.cloud_notm}}:
   * Dos subredes portátiles privadas para la gestión de HCX.
   * Una subred portátil pública para la activación y mantenimiento con VMware. Esta subred también se utiliza para las interconexiones HCX.

   Las direcciones IP de las subredes solicitadas para HCX están pensadas para que las gestione el proceso automático de VMware en {{site.data.keyword.cloud_notm}}. Estas direcciones IP no se pueden asignar a recursos de VMware, como VM y NSX Edges, creados por el cliente. Si necesita direcciones IP adicionales para los artefactos de VMware, debe solicitar sus propias subredes de {{site.data.keyword.cloud_notm}}.
   {:important}
3. Se crean tres agrupaciones de recursos y carpetas de VM para HCX, que son necesarias para las interconexiones de HCX, los componentes locales de HCX y los componentes remotos de HCX.
4. Se despliega y se configura un par de VMware NSX Edge Services Gateways (ESG) para el tráfico de gestión de HCX:
   * Se configuran interfaces de enlaces ascendentes públicos y privados utilizando las subredes solicitadas.
   * Se configuran los ESG como un par de dispositivos de extremo extra grandes con alta disponibilidad (HA) habilitada.
   * Se configuran reglas de cortafuegos y reglas de conversión de direcciones de red (NAT) para permitir el tráfico HTTPS de entrada y de salida procedente y destinado a HCX Manager.
   * Se configuran las agrupaciones de recursos y las reglas del equilibrador de carga. Estas reglas y agrupaciones de recursos se utilizan para reenviar el tráfico de entrada relacionado con HCX a los dispositivos virtuales adecuados de HCX Manager y vCenter Server (con el controlador de servicios de plataforma integrado).
   * Se aplica el certificado SSL para cifrar el tráfico HTTPS de entrada relacionado con HCX que llega a través de los ESG.

   El extremo de gestión HCX se dedica al tráfico de gestión HCX entre los componentes locales de HCX y los componentes en la nube de HCX. No modifique el extremo de gestión de HCX ni lo utilice para extensiones de red de HCX. En su lugar, crear otros extremos para extensiones de red. Además, el uso de un cortafuegos o la inhabilitación de las comunicaciones del extremo de gestión de HCX con componentes de gestión privados de IBM o con internet pública pueden afectar negativamente a las funciones de HCX.
   {:important}

5. Se despliega, se activa y se configura HCX Manager on {{site.data.keyword.cloud_notm}}:
   * Se registra HCX Manager con vCenter Server.
   * Se configuran los componentes HCX Manager, vCenter Server (con el controlador de servicios de plataforma integrado) y NSX Manager.
   * Se configura la flota HCX.
   * Se configuran contenedores de despliegue de HCX locales y remotos.
6. Se registra el nombre de host y la dirección IP de HCX Manager con el servidor DNS de VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

#### Visualización de detalles de una instancia
{: #vc_trial_hybrid_orderinginstance-view-inst-details}

Puede comprobar el estado del despliegue visualizando los detalles de la instancia. Pulse **Recursos** en el panel de navegación de la izquierda y localice la tabla **Instancias de vCenter Server** o **Instancias de HCX locales** para
ver información sobre las instancias que ha solicitado.

Cuando la instancia se ha desplegado correctamente, los componentes que se describen en las secciones *Especificaciones técnicas* de este tema se instalan en la plataforma virtual de VMware y la clave de activación del servicio HCX local en {{site.data.keyword.cloud_notm}} aparece listado en la tabla **Instancias de HCX locales**.

El estado de la instancia pasa a ser **Listo para su uso** y el usuario recibe una notificación por correo electrónico.

### Qué hacer a continuación
{: #vc_trial_hybrid_orderinginstance-next}

Instale HCX Enterprise Manager local y configure la conexión con el HCX en la instancia de {{site.data.keyword.cloud_notm}}.

1. Localice la clave de activación local en la página **Recursos**.
  1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
  2. En la tabla **Instancias de vCenter Server**, revise la columna **Tipo** para localizar la instancia de prueba de un solo nodo y anote el nombre de la instancia.
  3. Desplácese hasta la tabla **Instancias de HCX locales** y examine la columna **Nombre** para localizar la instancia que tiene el mismo nombre que la instancia de un solo nodo que ha solicitado con el prefijo *-OnPrem*.
  4. Anote la clave del campo **Clave de activación**.
2. Obtenga el HCX Enterprise Manager Open Virtual Appliance (OVA) local desde HCX en la consola de {{site.data.keyword.cloud_notm}} HCX Manager.
  1. Conéctese a la consola de HCX Cloud.
    1. En la tabla **Instancias de vCenter Server**, pulse la instancia de la prueba de un solo nodo para ver los detalles de la instancia.
    2. En **Información de acceso**, localice y anote las credenciales de vCenter.
    3. Pulse **Servicios** en el panel de navegación izquierdo.
    4. En la página **Servicios**, pulse **HCX on IBM Cloud**.
    5. En la página de detalles de **HCX on IBM Cloud**, localice y anote la **IP de HCX Cloud**.
    6. Asegúrese de que está conectado a la VPN para acceder a la red privada de {{site.data.keyword.cloud_notm}}.
    7. Pulse **Ver consola de HCX Cloud**.
  2. En la **consola de HCX Cloud**, siga estos pasos:
      1. Pulse el separador **Administración**.
      2. En el separador **Actualizaciones del sistema**, pulse **SOLICITAR ENLACE DE DESCARGA**.
      3. Pulse **COPIAR ENLACE** y utilice este enlace para descargar el cliente de HCX Enterprise en un entorno local con acceso a su entorno local de vSphere.
3. En el cliente web de VMware vSphere, despliegue el cliente de HCX Enterprise como dispositivo virtual de HCX Manager (HCX Manager) en el entorno local. Para obtener más información, consulte [Instalación de HCX Enterprise Manager OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-C61E107C-1F5F-4615-9BA9-351900CDB69E.html).

    Debe desplegar HCX Manager local en una red privada y debe otorgarle acceso a la red pública. Puede utilizar NSX Edge, Vyatta o pasarelas similares para permitir el acceso Internet al HCX Manager local. Si las pasarelas utilizadas para el acceso a la red privada y a la red pública son distintas, se recomienda utilizar la pasarela predeterminada para permitir el acceso a la red pública y a la **consola de administración de HCX Manager** privada para crear una ruta estática para el acceso a la red privada.  
    {:note}
4. Utilice la clave de activación local que ha anotado en el paso 1 para activar la máquina virtual de HCX Enterprise Manager local.
  1. Inicie una sesión en la VM de HCX Enterprise Manager local utilizando las credenciales especificadas al desplegar OVA.
  2. Escriba la clave de activación cuando se le solicite.

  Para obtener más información, consulte [Activación y configuración inicial de HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-6A4740C1-2225-444C-8ADC-CBE54F181536.html).
  {:note}
5. El servicio HCX on {{site.data.keyword.cloud_notm}} ha generado un certificado SSL autofirmado. Debe importar el certificado en el HCX Manager local siguiendo los siguientes pasos:
    1. En la **consola de administración de HCX Manager** local, pulse el separador **Administración**.
    2. En el panel de navegación de la izquierda, pulse **Certificado de CA de confianza** y luego pulse **IMPORTAR** a la derecha.
    3. Pulse **URL** y escriba el URL del certificado que desea aplicar, es decir, la **IP de HCX Cloud** (``https://<cloud-side public IP>``), que encontrará en la página de detalles del servicio HCX on {{site.data.keyword.cloud_notm}} en la consola de {{site.data.keyword.vmwaresolutions_short}}.
    4. Pulse **APLICAR**.
6. Continúe la configuración inicial y cree la interconexión. Para obtener más información, consulte [Instalación y configuración de VMware HCX Enterprise](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html).
7. Extienda las redes de VMware HCX del entorno local a {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Extensión de redes con VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html?hWord=N4IghgNiBcIKIA8AuBTAdgEwJZoOYAI0UkB3AewCcBrAZxAF8g).
8. Migre las VM del entorno local a {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Migración de máquinas virtuales con VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html?hWord=N4IghgNiBcILIEsDmAnMAXBA7JACAagiugK6S5xgDGAFtgKYDOuA7gujQXC2CvbgAkAwgA0QAXyA).

Solo debe gestionar los componentes de la infraestructura {{site.data.keyword.vmwaresolutions_short}} que se crean en la cuenta de {{site.data.keyword.cloud_notm}} desde la consola de {{site.data.keyword.vmwaresolutions_short}}, no a través del {{site.data.keyword.slportal}} ni por ningún otro medio fuera de la consola.
Si cambia estos componentes fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, los cambios no se sincronizan con la consola y pueden hacer que el entorno sea inestable.
{:important}

## Procedimiento para suprimir la versión de prueba de un solo nodo para instancias de vCenter Server
{: #vc_trial_hybrid_orderinginstance-deleting-procedure}

Cuando suprima una instancia de prueba de un solo nodo de vCenter Server, los siguientes componentes se liberarán en esta secuencia:

1. Todos los servicios desplegados
3. Licencias del producto VMware
4. Servidores ESXi
5. Subredes
6. VLAN

Debido a las dependencias entre recursos, los componentes de la instancia no se liberan inmediatamente cuando se suprime la instancia. Por ejemplo, las subredes y las VLAN no se pueden suprimir hasta que la infraestructura de {{site.data.keyword.cloud_notm}} haya reclamado por completo los servidores ESXi, lo cual sucede al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}. Al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días, se suprimen las subredes y las VLAN y se completa la supresión de la instancia.

Se le facturará por la instancia suprimida hasta el final del ciclo de facturación de la infraestructura {{site.data.keyword.cloud_notm}}.
{:note}

Siga los pasos siguientes para suprimir una instancia de prueba de un solo nodo para vCenter Server:

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, busque la instancia que desea suprimir.
3. En la columna **Acciones**, pulse el icono Suprimir.
   El estado de la instancia pasa a ser **Suprimiendo**. Cuando la instancia se haya suprimido correctamente, los componentes de la instancia se liberarán y el estado de la instancia pasará a ser **Suprimido**.
4. Si desea eliminar el registro de la instancia de la consola de {{site.data.keyword.vmwaresolutions_short}}, siga estos pasos:
   1. En la columna **Acciones**, pulse el icono Suprimir de nuevo.
   2. En la ventana **Suprimir instancia**, pulse **Aceptar**.

## Enlaces relacionados
{: #vc_trial_hybrid_orderinginstance-related}

* [Diseño de la arquitectura de HCX on IBM Cloud para la versión de prueba de un solo nodo para vCenter Server on IBM Cloud](https://console.bluemix.net/docs/services/vmwaresolutions/archiref/trial/vc_trial_hcx_arch.html)
* [Documentación de VMware Hybrid Cloud Extension](https://hcx.vmware.com/#/vm-documentation)
* [Obtención de HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)
