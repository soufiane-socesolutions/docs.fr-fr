---
title: "Effectuer des tests unitaires avec Visual Basic dans .NET Core à l’aide de dotnet test et de xUnit"
description: "Apprenez les concepts des tests unitaires dans .NET Core de manière interactive en créant un exemple de solution Visual Basic pas à pas à l’aide de dotnet test et de xUnit."
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.topic: article
dev_langs: vb
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 01922e3ad3b19e13ebea755decf21c6b09e4be37
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a>Effectuer des tests unitaires sur les bibliothèques .NET Core Visual Basic à l’aide de dotnet test et de xUnit

Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires. Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) avant de commencer. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Création du projet source

Ouvrez une fenêtre d’interpréteur de commandes. Créez un répertoire appelé *unit-testing-vb-using-dotnet-test* qui contiendra la solution.
Dans ce nouveau répertoire, exécutez [`dotnet new sln`](../tools/dotnet-new.md) pour créer une solution. Cette méthode permet de simplifier la gestion de la bibliothèque de classes et du projet de test unitaire.
Dans le répertoire de la solution, créez un répertoire *PrimeService*. Vous disposez de la structure du répertoire et des fichiers suivante :

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Accédez au répertoire *PrimeService* et exécutez [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) pour créer le projet source. Renommez *Class1.VB* en *PrimeService.VB*. Pour utiliser le développement piloté par les tests (TDD), vous créez une implémentation défaillante de la classe `PrimeService` :

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Accédez de nouveau au répertoire *unit-testing-vb-using-dotnet-test*. Exécutez [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) pour ajouter le projet de la bibliothèque de classes à la solution.

## <a name="creating-the-test-project"></a>Création du projet de test

Ensuite, créez le répertoire *PrimeService.Tests*. La structure du répertoire est illustrée ci-dessous :

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de [`dotnet new xunit -lang VB`](../tools/dotnet-new.md). Cette commande crée un projet de test qui utilise xUnit comme bibliothèque de test. Le modèle généré configure le Test Runner dans *PrimeServiceTests.vbproj* :

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires. `dotnet new` a ajouté xUnit et le Test Runner xUnit à l’étape précédente. Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet. Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) sur GitHub.

Le dossier final se présente comme suit :

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

Exécutez [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) dans le répertoire *unit-testing-vb-using-dotnet-test*. 

## <a name="creating-the-first-test"></a>Création du premier test

L’approche TDD impose d’écrire un test défaillant, de le corriger pour qu’il réussisse, puis de répéter le processus. Supprimez *UnitTest1.vb* du répertoire *PrimeService.Tests* et créez un fichier Visual Basic nommé *PrimeService_IsPrimeShould.VB*. Ajoutez le code suivant :

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

L’attribut `<Fact>` désigne une méthode de test qui est exécutée par le Test Runner. À partir de *unit-testing-using-dotnet-test*, exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests. Le Test Runner xUnit contient le point d’entrée de programme qui permet d’exécuter vos tests. `dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.

Votre test échoue. Vous n’avez pas encore créé l’implémentation. Effectuez ce test en écrivant le code le plus simple dans la classe `PrimeService` qui fonctionne :

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

Dans le répertoire *unit-testing-vb-using-dotnet-test*, réexécutez `dotnet test`. La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`. Après la création des deux projets, il exécute ce test unique. Le test réussit.

## <a name="adding-more-features"></a>Ajout de fonctionnalités supplémentaires

Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code. Il existe quelques autres cas simples pour des nombres premiers : 0, -1. Vous pouvez ajouter ces cas en tant que nouveaux tests, avec l’attribut `<Fact>`, mais cela devient vite fastidieux. D’autres attributs xUnit vous permettent d’écrire une suite de tests similaires.  L’attribut `<Theory>` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents. Vous pouvez utiliser l’attribut `<InlineData>` pour spécifier des valeurs pour ces entrées.

Au lieu de créer de nouveaux tests, appliquez ces deux attributs pour créer une théorie unique. La théorie est une méthode qui teste plusieurs valeurs inférieures à deux, qui est le plus petit nombre premier :

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Exécutez `dotnet test`, et deux de ces tests échouent. Pour que tous les tests réussissent, modifiez la clause `if` au début de la méthode :

```vb
if candidate < 2
```

Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale. Vous disposez de la [version finale des tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) et de [l’implémentation complète de la bibliothèque](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService/PrimeService.vb).

Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque. Vous avez structuré la solution afin que l’ajout de nouveaux packages et tests fasse partie du flux de travail normal. Vous avez concentré la plupart de votre temps et de vos efforts sur la résolution des objectifs de l’application.
