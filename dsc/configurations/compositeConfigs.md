---
ms.date: 06/12/2017
keywords: DSC, PowerShell, 構成, セットアップ
title: 構成を入れ子にする
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402278"
---
# <a name="nesting-dsc-configurations"></a>DSC 構成を入れ子にする

入れ子構成 (複合構成とも呼ぶ) とは、別の構成内でリソースとして呼び出される構成です。
両方の構成は、同じファイルで定義する必要があります。

簡単な例を見てみましょう。

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

この例では、`FileConfig` は **CopyFrom** および **CopyTo** という 2 つの必須パラメーターを受け取り、それらは `File` リソース ブロック内の **SourcePath** プロパティおよび **DestinationPath** プロパティの値として使用されます。
`NestedConfig` 構成は `FileConfig` をリソースとして呼び出します。
`NestedConfig` リソース ブロック内のプロパティ (**CopyFrom** と **CopyTo**) は、`FileConfig` 構成のパラメーターです。

## <a name="see-also"></a>参照

- [複合リソース: リソースとしての DSC 構成の使用](../resources/authoringResourceComposite.md)