---
title: "Configuration de la liaison d&#39;assembly | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "assemblys (.NET Framework), redirection de liaison"
  - "exécution côte à côte, redirection de liaison d'assembly"
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# Configuration de la liaison d&#39;assembly
Par défaut, les applications utilisent le jeu d'assemblys .NET Framework qui est fourni avec la version du runtime utilisée pour compiler l'application.  Vous pouvez spécifier l'attribut **appliesTo** avec l'élément [\<assemblyBinding\>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) dans un fichier de configuration de l'application pour rediriger les références de liaison d'assembly vers une version spécifique des assemblys .NET Framework.  Cet attribut facultatif utilise un numéro de version .NET Framework pour indiquer la version à laquelle il s'applique.  Si aucun attribut **appliesTo** n'est spécifié, l'élément **\<assemblyBinding\>** s'applique à toutes les versions du .NET Framework.  
  
 L'attribut **appliesTo** a été introduit dans .NET Framework 1.1 ; il est donc ignoré dans .NET Framework 1.0.  Cela signifie que tous les éléments **\<assemblyBinding\>** sont pris en compte dans .NET Framework 1.0, même si un attribut **appliesTo** est spécifié.  
  
> [!NOTE]
>  Utilisez l'attribut **appliesTo** pour limiter la redirection de liaison d'assembly vers une version spécifique du runtime.  
  
 Par exemple, pour rediriger la liaison d'assembly pour un assembly du .NET Framework 1.0, vous devez inclure le code XML suivant dans votre fichier de configuration de l'application.  
  
```  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 Les éléments **\<assemblyBinding\>** sont traités dans l'ordre.  Ainsi, vous devez d'abord entrer les informations de redirection des liaisons des assemblys du .NET Framework 1.0, puis celles des assemblys du .NET Framework 1.1.  Enfin, vous devez entrer les informations de redirection des liaisons d'assembly pour toutes les redirections d'assembly du .NET Framework qui n'utilisent pas d'attribut **appliesTo** et qui s'appliquent donc à toutes les versions du .NET Framework.  En cas de conflit de redirection, la première instruction de redirection correspondante dans le fichier de configuration est utilisée.  
  
 Par exemple, pour rediriger une référence à un assembly du .NET Framework 1.0 et une autre à un assembly du .NET Framework 1.1, utilisez le modèle indiqué dans le pseudo\-code suivant.  
  
```  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
<! — .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
    <! — .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
<!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## Débogage des erreurs de fichier de configuration  
 Le runtime analyse les fichiers de configuration au moment de la création d'un domaine d'application, puis il charge le code dans ce domaine d'application.  Le common language runtime gère les erreurs dans un fichier de configuration en ignorant l'entrée.  Le runtime ignore tout le fichier de configuration si celui\-ci contient du code XML incorrectement formé.  En présence de code XML non valide, seules les sections non valides sont ignorées.  
  
 Vous pouvez déterminer si un fichier de configuration est actuellement utilisé en vérifiant si des redirections de liaison d'assembly ont lieu.  Utilisez [Fuslogvw.exe \(visionneuse du journal de liaison d'assembly](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) pour voir quels assemblys sont chargés.  Pour voir toutes les liaisons d'assembly, ajoutez une entrée pour **ForceLog** dans le Registre.  
  
## Voir aussi  
 [Comment : activer et désactiver la redirection de liaison automatique](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)