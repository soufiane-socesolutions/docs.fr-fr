---
title: "Récupération des informations stockées dans les attributs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d3fd9a5a49d65b37d2cdb5107e9c516a6df5847
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-information-stored-in-attributes"></a>Récupération des informations stockées dans les attributs
La récupération d’un attribut personnalisé est un processus simple. Tout d’abord, déclarez une instance de l’attribut que vous souhaitez récupérer. Ensuite, utilisez la <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> méthode pour initialiser le nouvel attribut à la valeur de l’attribut que vous souhaitez récupérer. Une fois que le nouvel attribut est initialisé, vous utilisez simplement ses propriétés pour obtenir les valeurs.  
  
> [!IMPORTANT]
>  Cette rubrique décrit comment récupérer des attributs pour le code chargé dans le contexte d’exécution. Pour récupérer des attributs pour le code chargé dans le contexte de réflexion uniquement, vous devez utiliser le <xref:System.Reflection.CustomAttributeData> de classe, comme indiqué dans [Comment : charger des assemblys dans le contexte de Reflection](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 Cette section décrit les méthodes suivantes pour récupérer les attributs :  
  
-   [La récupération d’une seule instance d’un attribut](#cpconretrievingsingleinstanceofattribute)  
  
-   [Récupération d’instances multiples d’un attribut appliqué à la même étendue](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [Récupération d’instances multiples d’un attribut appliqué à différentes portées](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a>La récupération d’une seule Instance d’un attribut  
 Dans l’exemple suivant, la `DeveloperAttribute` (décrite dans la section précédente) est appliqué à la `MainApp` classe sur le niveau de la classe. Le `GetAttribute` utilise **GetCustomAttribute** pour récupérer les valeurs stockées dans `DeveloperAttribute` sur le niveau de la classe avant de les afficher dans la console.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Ce programme affiche le texte suivant lors de l’exécution.  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Si l’attribut est introuvable, la **GetCustomAttribute** méthode initialise `MyAttribute` à une valeur null. Cet exemple montre comment `MyAttribute` une telle instance et avertit l’utilisateur si aucun attribut n’est trouvé. Si la `DeveloperAttribute` est introuvable dans la portée de classe, le message suivant s’affiche dans la console.  
  
```  
The attribute was not found.   
```  
  
 Cet exemple suppose que la définition d’attribut est dans l’espace de noms actuel. N’oubliez pas d’importer l’espace de noms dans lequel se trouve la définition d’attribut s’il n’est pas dans l’espace de noms actuel.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Récupération d’Instances multiples d’un attribut appliqué à la même étendue  
 Dans l’exemple précédent, la classe à inspecter et l’attribut spécifique à rechercher sont passés à <xref:System.Attribute.GetCustomAttribute%2A>. Ce code fonctionne correctement uniquement si une instance d’un attribut est appliquée sur le niveau de la classe. Toutefois, si plusieurs instances d’un attribut sont appliquées au niveau de la même classe, la **GetCustomAttribute** méthode ne récupère pas toutes les informations. Dans les cas où plusieurs instances du même attribut sont appliquées à la même portée, vous pouvez utiliser <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> à placer toutes les instances d’un attribut dans un tableau. Par exemple, si deux instances de `DeveloperAttribute` sont appliquées au niveau de la même classe, la `GetAttribute` méthode peut être modifiée pour afficher les informations trouvées dans les deux attributs. N’oubliez pas d’appliquer plusieurs attributs au même niveau, l’attribut doit être défini avec la **AllowMultiple** propriété **true** dans le <xref:System.AttributeUsageAttribute>.  
  
 L’exemple de code suivant montre comment utiliser le **GetCustomAttributes** méthode pour créer un tableau qui fait référence à toutes les instances de `DeveloperAttribute` dans les classes données. Les valeurs de tous les attributs sont ensuite affichés sur la console.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Si aucun attribut n’est trouvé, ce code avertit l’utilisateur. Dans le cas contraire, les informations contenues dans les deux instances de `DeveloperAttribute` s’affiche.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Récupération d’Instances multiples d’un attribut appliqué à différentes portées  
 Le <xref:System.Attribute.GetCustomAttributes%2A> et <xref:System.Attribute.GetCustomAttribute%2A> méthodes ne pas rechercher une classe entière et retournent toutes les instances d’un attribut dans cette classe. Elles recherchent plutôt qu’une seule méthode spécifiée ou membre à la fois. Si vous avez une classe avec le même attribut appliqué à chaque membre et que vous souhaitez récupérer les valeurs de tous les attributs appliqués à ces membres, vous devez fournir chaque méthode ou membre individuellement à **GetCustomAttributes** et  **GetCustomAttribute**.  
  
 L’exemple de code suivant prend une classe en tant que paramètre et recherche le `DeveloperAttribute` (définie précédemment) sur le niveau de la classe et sur chaque méthode individuelle de cette classe.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Si aucune instance de la `DeveloperAttribute` se trouvent sur le niveau méthode ou classe, le `GetAttribute` avertit l’utilisateur qui a trouvé aucun attribut de méthode et affiche le nom de la méthode ou classe qui ne contient pas l’attribut. Si un attribut est trouvé, le `Name`, `Level`, et `Reviewed` champs sont affichés dans la console.  
  
 Vous pouvez utiliser les membres de la <xref:System.Type> classe pour obtenir les méthodes individuelles et les membres de la classe passée. Cet exemple interroge d’abord l'objet **Type** pour obtenir des informations d’attribut de niveau de la classe. Ensuite, il utilise <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> pour placer des instances de toutes les méthodes dans un tableau de <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> pour récupérer les informations d’attribut de niveau de la méthode. Vous pouvez également utiliser la méthode <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> permettant de vérifier les attributs de niveau de la propriété ou <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> pour vérifier les attributs au niveau du constructeur.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [Attributs](../../../docs/standard/attributes/index.md)
