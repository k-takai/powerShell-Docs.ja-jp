---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, PowerShell, 構成, セットアップ"
title: "Linux 用 DSC の nxGroup リソース"
ms.openlocfilehash: fcd1dfd3110b1358ed7ef9ca8d57154186b271f6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
<a id="dsc-for-linux-nxgroup-resource" class="xliff"></a>

# Linux 用 DSC の nxGroup リソース

PowerShell Desired State Configuration (DSC) の **nxGroup** リソースは、Linux ノード上でローカル グループを管理するためのメカニズムを備えています。

<a id="syntax" class="xliff"></a>

## 構文

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

<a id="properties" class="xliff"></a>

## プロパティ

|  プロパティ |  説明 | 
|---|---|
| GroupName| 特定の状態を保証するグループの名前を指定します。| 
| Ensure| グループが存在するかどうかを決定します。 グループが存在することを保証するには、このプロパティを "Present" に設定します。 グループが存在しないことを保証するには、"Absent" に設定します。 既定値は "Present" です。| 
| [メンバー]| グループを形成するメンバーを指定します。| 
| MembersToInclude| グループのメンバーであることを保証するユーザーを指定します。| 
| MembersToExclude| グループのメンバーでないことを保証するユーザーを指定します。| 
| PreferredGroupID| 可能であれば、グループ id を指定の値に設定します。 そのグループ id が現在使用中である場合は、次に使用可能なグループ id が使用されます。| 
| DependsOn | このリソースを構成する前に、他のリソースの構成を実行する必要があることを示します。 たとえば、最初に実行するリソース構成スクリプト ブロックの **ID** が **ResourceName** で、そのタイプが **ResourceType** である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。| 

<a id="example" class="xliff"></a>

## 例

次の例では、ユーザー "monuser" が存在し、グループ "DBusers" のメンバーであることを保証しています。

```
Import-DSCResource -Module nx 

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```

