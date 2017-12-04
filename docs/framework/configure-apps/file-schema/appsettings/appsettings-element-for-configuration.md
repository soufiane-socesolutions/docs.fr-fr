---
title: "&lt;appSettings&gt; , élément pour &lt;configuration&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cb59120d88816ea193bd8588b152d6b848b682d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="c4f00-102">\<appSettings >, élément pour \<configuration ></span><span class="sxs-lookup"><span data-stu-id="c4f00-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="c4f00-103">Contient des paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c4f00-103">Contains custom application settings.</span></span> <span data-ttu-id="c4f00-104">Il s’agit d’une section de configuration prédéfinie fournie par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4f00-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="c4f00-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c4f00-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="c4f00-106">&nbsp;&nbsp;**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="c4f00-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c4f00-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4f00-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="c4f00-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="c4f00-108">Attribute</span></span>

|           | <span data-ttu-id="c4f00-109">Description</span><span class="sxs-lookup"><span data-stu-id="c4f00-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c4f00-110">**fichier**</span><span class="sxs-lookup"><span data-stu-id="c4f00-110">**file**</span></span>  | <span data-ttu-id="c4f00-111">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4f00-111">Optional attribute.</span></span><br><br><span data-ttu-id="c4f00-112">Spécifie un chemin d’accès relatif vers un fichier externe qui contient les paramètres de configuration d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c4f00-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="c4f00-113">Le fichier spécifié contient le même type de paramètres qui sont spécifiés dans le  **\<Ajouter >**,  **\<Supprimer >**, et  **\<Effacer >** éléments et utilise la même paire clé/valeur de format que ces éléments.</span><span class="sxs-lookup"><span data-stu-id="c4f00-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="c4f00-114">Le chemin d’accès spécifié est relatif au fichier de configuration principal.</span><span class="sxs-lookup"><span data-stu-id="c4f00-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="c4f00-115">Pour une application Windows Forms, c’est le dossier binaire (tel que */bin/debug*), pas l’emplacement du fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="c4f00-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="c4f00-116">Pour les applications Web Forms, le chemin d’accès est relatif à la racine de l’application, où le *web.config* fichier se trouve.</span><span class="sxs-lookup"><span data-stu-id="c4f00-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="c4f00-117">Notez que le runtime ignore l’attribut si le fichier spécifié est introuvable.</span><span class="sxs-lookup"><span data-stu-id="c4f00-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="c4f00-118">Élément parent</span><span class="sxs-lookup"><span data-stu-id="c4f00-118">Parent element</span></span>

|     | <span data-ttu-id="c4f00-119">Description</span><span class="sxs-lookup"><span data-stu-id="c4f00-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c4f00-120">**\<configuration >** élément</span><span class="sxs-lookup"><span data-stu-id="c4f00-120">**\<configuration>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="c4f00-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4f00-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c4f00-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c4f00-122">Child elements</span></span>

|     | <span data-ttu-id="c4f00-123">Description</span><span class="sxs-lookup"><span data-stu-id="c4f00-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c4f00-124">**\<add>**</span><span class="sxs-lookup"><span data-stu-id="c4f00-124">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="c4f00-125">Ajoute un paramètre d’application personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c4f00-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="c4f00-126">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="c4f00-126">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="c4f00-127">Efface tous les paramètres d’application définis précédemment.</span><span class="sxs-lookup"><span data-stu-id="c4f00-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="c4f00-128">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="c4f00-128">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="c4f00-129">Supprime un paramètre d’application défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="c4f00-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c4f00-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="c4f00-130">Remarks</span></span>

<span data-ttu-id="c4f00-131">Le  **\<appSettings >** élément stocke les informations de configuration d’application personnalisée, tels que les chaînes de connexion de base de données, les chemins d’accès de fichier, des URL de service Web XML ou d’autres informations de configuration personnalisée pour un application.</span><span class="sxs-lookup"><span data-stu-id="c4f00-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="c4f00-132">Les paires clé/valeur spécifiées dans le  **\<appSettings >** élément sont accessibles dans le code à l’aide la <xref:System.Configuration.ConfigurationSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="c4f00-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="c4f00-133">Vous pouvez utiliser la **fichier** d’attribut dans le  **\<appSettings >** élément de la *Web.config* et les fichiers de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="c4f00-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="c4f00-134">Cet attribut spécifie un fichier de configuration qui fournit des paramètres supplémentaires ou substitue les paramètres spécifiés dans le  **\<appSettings >** élément.</span><span class="sxs-lookup"><span data-stu-id="c4f00-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="c4f00-135">Le **fichier** attribut peut être utilisé dans les scénarios de développement en équipe de contrôle de code source, telles que lorsqu’un utilisateur souhaite remplacer les paramètres du projet spécifiés dans un fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="c4f00-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="c4f00-136">Les fichiers de configuration spécifiés par le **fichier** attribut doit avoir un nœud racine de  **\<appSettings >** plutôt que  **\<configuration >**.</span><span class="sxs-lookup"><span data-stu-id="c4f00-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="c4f00-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4f00-137">Example</span></span>

<span data-ttu-id="c4f00-138">L’exemple suivant montre un fichier de paramètres d’application externe (*custom.config*) qui définit un paramètre d’application personnalisé :</span><span class="sxs-lookup"><span data-stu-id="c4f00-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="c4f00-139">L’exemple suivant montre un fichier de configuration d’application qui consomme le paramètre dans le fichier de paramètres externes et définit un paramètre d’application qui lui est propre :</span><span class="sxs-lookup"><span data-stu-id="c4f00-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="c4f00-140">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="c4f00-140">Configuration file</span></span>

<span data-ttu-id="c4f00-141">Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* les fichiers qui ne sont pas au niveau du répertoire d’application.</span><span class="sxs-lookup"><span data-stu-id="c4f00-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4f00-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4f00-142">See also</span></span>

[<span data-ttu-id="c4f00-143">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c4f00-143">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)