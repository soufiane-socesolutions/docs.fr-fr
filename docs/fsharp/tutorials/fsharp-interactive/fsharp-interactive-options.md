---
title: "Options F# Interactive"
description: 'En savoir plus sur les options de ligne de commande pris en charge par F # Interactive, fsi.exe.'
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9f3e39b-ce6c-41ff-991f-0625f46441ae
ms.openlocfilehash: a9b36a12aa9ffcfa26ea50d72d018a25f5f65243
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="f-interactive-options"></a>Options F# Interactive

> [!NOTE]
Cet article ne traite pour le moment que de l’expérience Windows.  Il va être réécrit.

Cette rubrique décrit les options de ligne de commande pris en charge par F # Interactive, `fsi.exe`. F # Interactive accepte la plupart des options de ligne de commande de même que le compilateur F #, mais accepte également des options supplémentaires.

## <a name="using-f-interactive-for-scripting"></a>À l’aide de F # Interactive pour l’écriture de scripts
F # Interactive, `fsi.exe`, peut être lancé interactivement, ou il peut être lancé depuis la ligne de commande pour exécuter un script. La syntaxe de ligne de commande est

```
> fsi.exe [options] [ script-file [arguments] ]
```

L’extension de fichier pour les fichiers de script F # est `.fsx`.

## <a name="table-of-f-interactive-options"></a>Tableau des Options F # Interactive
Le tableau suivant résume les options prises en charge par F # Interactive. Vous pouvez définir ces options sur la ligne de commande ou via l’IDE de Visual Studio. Pour définir ces options dans l’IDE de Visual Studio, ouvrez le **outils** menu, sélectionnez **Options...** , puis développez le **outils F #** nœud et sélectionnez **F # Interactive**.

Lorsque des listes figurent dans les arguments de l’option F # Interactive, les éléments de liste sont séparés par des points-virgules (`;`).

|Option|Description|
|------|-----------|
|**--**|Utilisé pour indiquer à F # Interactive de traiter les arguments restants en tant qu’arguments de ligne de commande au programme F # ou script, auquel vous pouvez accéder dans le code à l’aide de la liste **fsi.CommandLineArgs**.|
|**--vérifiée**[**+**&#124; **-**]|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**page de codes-- :&lt;int&gt;**|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--crossoptimize**[**+**&#124; **-**]|Activer ou désactiver les optimisations intermodules.|
|**--debug**[**+**&#124; **-**]<br /><br />**--debug :**[**complète**&#124; **pdbonly**]<br /><br />**-g**[**+**&#124; **-**]<br /><br />**-g:**[**complète**&#124; **pdbonly**]|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--définir :&lt;chaîne&gt;**|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--exec**|Fait en sorte que F # interactive quitte après le chargement des fichiers ou le fichier de script sur la ligne de commande en cours d’exécution.|
|**/fullpaths--**|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--l’interface graphique utilisateur**[**+**&#124; **-**]|Active ou désactive la boucle d’événements Windows Forms. Les styles sont activés par défaut.|
|**--aide**<br /><br />**-?**|Utilisé pour afficher la syntaxe de ligne de commande et une brève description de chaque option.|
|**--lib :&lt;-liste des dossiers&gt;**<br /><br />**-I&lt;-liste des dossiers&gt;**|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--charger :&lt;nom de fichier&gt;**|Compile le code source donné au démarrage et charge les constructions F # compilées dans la session. Si la source de la cible contient des directives de script telles que **#use** ou **#load**, vous devez utiliser **--utilisez** ou **#use** au lieu de **--charger** ou **#load**.|
|**--mlcompatibility**|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--noframework**|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez [Options du compilateur](../../language-reference/compiler-options.md)|
|**/nologo--**|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--nowarn :&lt;-liste d’avertissements&gt;**|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--optimiser**[**+**&#124; **-**]|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--silencieux**|Supprimer la sortie de F # Interactive pour le **stdout** flux.|
|**--les quotations de débogage**|Spécifie que les informations de débogage supplémentaires doivent être émises pour les expressions qui sont dérivées de littéraux de guillemets F # et répercutées définitions. Les informations de débogage sont ajoutées pour les attributs personnalisés d’un nœud d’arborescence de l’expression F #. Consultez [Quotations de Code](../../language-reference/code-quotations.md) et [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[**+**&#124; **-**]|Activer ou désactiver la saisie semi-automatique par tabulation en mode interactif.|
|**--référence :&lt;nom de fichier&gt;**<br /><br />**-r:&lt;nom de fichier&gt;**|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--tailcalls**[**+**&#124; **-**]|Activer ou désactiver l’utilisation de l’instruction de langage intermédiaire de fin, ce qui entraîne le frame de pile être réutilisées pour les fonctions récursives tail. Cette option est activée par défaut.|
|**--utiliser :&lt;nom de fichier&gt;**|Indique à l’interpréteur à utiliser le fichier spécifié au démarrage en tant qu’entrée initiale.|
|**--utf8output**|Identique à l’option de compilateur fsc.exe. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--avertir :&lt;niveau d’avertissement&gt;**|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--/warnaserror**[**+**&#124; **-**]|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|
|**--/warnaserror**[**+**&#124; **-** ] :**&lt;int-liste&gt;**|Identique à la **fsc.exe** option du compilateur. Pour plus d’informations, consultez l’article [Options du compilateur](../../language-reference/compiler-options.md).|

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----|-----------|
|[Options du compilateur](../../language-reference/compiler-options.md)|Décrit les options de ligne de commande disponibles pour le compilateur F #, **fsc.exe**.|
