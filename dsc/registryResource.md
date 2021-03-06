---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, PowerShell, 構成, セットアップ"
title: "DSC Registry リソース"
ms.openlocfilehash: 649cb60578c053c04a7fcc7446881fb76daee26a
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2017
---
<a id="dsc-registry-resource" class="xliff"></a>

# DSC Registry リソース

> 適用先: Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) の **Registry** リソースは、ターゲット ノードでレジストリ キーと値を管理するためのメカニズムを備えています。

<a id="syntax" class="xliff"></a>

## 構文

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

<a id="properties" class="xliff"></a>

## プロパティ
|  プロパティ  |  説明   | 
|---|---| 
| キー| 特定の状態を確認するレジストリ キーのパスを示します。 このパスには、ハイブを含める必要があります。| 
| ValueName| レジストリ値の名前を示します。 レジストリ キーを追加または削除するには、ValueType または ValueData を指定せずに、このプロパティを空の文字列で指定します。 レジストリ キーの既定値を変更または削除するには、ValueType または ValueData を指定し、このプロパティを空の文字列で指定します。| 
| Ensure| キーと値が存在するかどうかを示します。 それらが存在することを保証するには、このプロパティを "Present" に設定します。 それらが存在しないことを保証するには、このプロパティを "Absent" に設定します。 既定値は "Present" です。| 
| Force| 指定のレジストリ キーが存在する場合、__Force__ はそのキーを新しい値で上書きします。 レジストリ キーをサブキーと共に削除する場合は、これが __$true__ である必要があります。| 
| Hex| 16 進形式でデータを表現するかどうかを示します。 指定した場合、DWORD/QWORD 値データが 16 進形式で表示されます。 その他の種類に対しては無効です。 既定値は __$false__ です。| 
| DependsOn| このリソースを構成する前に、他のリソースの構成を実行する必要があることを示します。 たとえば、最初に実行するリソース構成スクリプト ブロックの ID が __ResourceName__ で、そのタイプが __ResourceType__ である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。| 
| ValueData| レジストリ値のデータ。| 
| ValueType| 値の種類を示します。 サポートされている型は次のとおりです。 
<ul><li>文字列 (REG_SZ)</li>


<li>バイナリ (REG-BINARY)</li>


<li>Dword 32 ビット (REG_DWORD)</li>


<li>Qword 64 ビット (REG_QWORD)</li>


<li>複数行文字列 (REG_MULTI_SZ)</li>


<li>展開可能な文字列 (REG_EXPAND_SZ)</li></ul>

<a id="example" class="xliff"></a>

## 例
次の例では、"ExampleKey" という名前のキーが **HKEY\_LOCAL\_MACHINE** ハイブに存在していることを確認します。
```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

>**注:** **HKEY\_CURRENT\_USER** レジストリ設定を変更するには、構成がシステムとしてではなくユーザーの資格情報で実行されている必要があります。
>**PsDscRunAsCredential** プロパティを使用すれば、構成に対してユーザー資格情報を指定できます。 例については、「[ユーザーの資格情報を指定して DSC を実行する](runAsUser.md)」を参照してください。



