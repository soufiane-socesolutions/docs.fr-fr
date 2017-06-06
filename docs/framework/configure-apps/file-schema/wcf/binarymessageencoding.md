---
title: "&lt;binaryMessageEncoding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;binaryMessageEncoding&gt;
Définit un encodeur de message binaire qui encode des messages de Windows Communication Foundation \(WCF\) en binaire sur le câble.  
  
## Syntaxe  
  
```  
  
<binaryMessageEncoding   
      maxReadPoolSize="Integer"  
   maxSessionSize="Integer"   
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10” />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|maxReadPoolSize|Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.  Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.  La valeur par défaut est 64.|  
|maxSessionSize|Entier positif qui définit la taille, en octets, de la mémoire tampon utilisée pour l'encodage.  Une mémoire tampon plus importante augmente la vitesse d'encodage aux dépens de la taille de la plage de travail.  La valeur par défaut est 2048.|  
|maxWritePoolSize|Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.  Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.  La valeur par défaut est 16.|  
|messageVersion|Spécifie le message SOAP et les versions WS\-Addressing qui sont utilisées ou attendues.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison d'une liaison personnalisée.|  
  
## Notes  
 L'encodage est le processus de transformation d'un message en une séquence d'octets.  Le décodage est le processus inverse.  Windows Communication Foundation \(WCF\) inclut trois types d'encodage des messages SOAP : Texte, Binaire et MTOM \(Message Transmission Optimization Mechanism\).  
  
 L'élément `binaryMessageEncoding` spécifie le format binaire .NET pour le code XML et propose des options permettant de spécifier l'encodage de caractères et la version SOAP et WS\-Addressing à utiliser.  L'encodeur de message binaire encode des messages de Windows Communication Foundation \(WCF\) en binaire sur le câble.  Même si cet encodage permet une transmission très rapide des messages, l'interopérabilité basée sur les normes WS\-\* est perdue.  
  
## Exemple  
  
```  
<binaryMessageEncoding maxReadPoolSize="211"  
   maxWritePoolSize="2132"  
   maxSessionSize="3141" />  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>   
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>   
 [Encodage de message](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)   
 [Sélection d'un encodeur de message](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)