---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, PowerShell, 構成, セットアップ"
title: "DSC の PackageManagementSource リソース"
ms.openlocfilehash: 80d157aff5bf7685a797baaf6a26215f02473096
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
<a id="dsc-packagemanagementsource-resource" class="xliff"></a>

# DSC の PackageManagementSource リソース

> 適用先: Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) の **PackageManagementSource** リソースは、ターゲット ノードで Package Management ソースを登録または登録解除するメカニズムを備えています。 **この方法で登録された Package Management ソースは System コンテキストで登録されるため、System アカウントまたは DSC エンジンで使用することができます。** このリソースには **PackageManagement** モジュールが必要です。これは、http://PowerShellGallery.com から入手できます。

<a id="syntax" class="xliff"></a>

## 構文

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

<a id="properties" class="xliff"></a>

## プロパティ
|  プロパティ  |  説明   | 
|---|---| 
| 名前| システムで登録または登録解除するパッケージ ソースの名前を指定します。| 
| Ensure| パッケージ ソースを登録または登録解除するかどうかを決定します。| 
| InstallationPolicy| パッケージ ソースを信頼するかどうかを決定します。 "Untrusted" または "Trusted" のどちらかです。| 
| ProviderName| パッケージ ソースとの相互運用に使用できる OneGet プロバイダーの名前を指定します。| 
| SourceUri| パッケージ ソースの URI を指定します。| 
| SourceCredential| リモート ソースのパッケージへのアクセスを提供します。| 

<a id="example" class="xliff"></a>

## 例

この例では、**PackageManagementSource** DSC リソースを使用して http://nuget.org パッケージ ソースを登録しています。

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

