---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, PowerShell, 構成, セットアップ"
title: "構成を入れ子にする"
ms.openlocfilehash: 4de53b94056df46d74923dda56e02841cfac2cd1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="a5bfd-103">DSC 構成を入れ子にする</span><span class="sxs-lookup"><span data-stu-id="a5bfd-103">Nesting DSC configurations</span></span>

<span data-ttu-id="a5bfd-104">入れ子構成 (複合構成とも呼ぶ) とは、別の構成内でリソースとして呼び出される構成です。</span><span class="sxs-lookup"><span data-stu-id="a5bfd-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="a5bfd-105">両方の構成は、同じファイルで定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5bfd-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="a5bfd-106">簡単な例を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="a5bfd-106">Let's look at a simple example:</span></span>

```powershell
Configuration FileConfig 
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }
    
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

<span data-ttu-id="a5bfd-107">この例では、`FileConfig` は **CopyFrom** および **CopyTo** という 2 つの必須パラメーターを受け取り、それらは `File` リソース ブロック内の **SourcePath** プロパティおよび **DestinationPath** プロパティの値として使用されます。</span><span class="sxs-lookup"><span data-stu-id="a5bfd-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="a5bfd-108">`NestedConfig` 構成は `FileConfig` をリソースとして呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a5bfd-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="a5bfd-109">`NestedConfig` リソース ブロック内のプロパティ (**CopyFrom** と **CopyTo**) は、`FileConfig` 構成のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="a5bfd-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5bfd-110">参照</span><span class="sxs-lookup"><span data-stu-id="a5bfd-110">See Also</span></span>

- [<span data-ttu-id="a5bfd-111">複合リソース: リソースとしての DSC 構成の使用</span><span class="sxs-lookup"><span data-stu-id="a5bfd-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
