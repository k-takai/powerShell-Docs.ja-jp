---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, PowerShell, 構成, セットアップ"
title: "Linux 用 DSC の nxSshAuthorizedKeys リソース"
ms.openlocfilehash: 3c145eeb86d971dc00e1c7cea60fb50c83d7b9a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
<a id="dsc-for-linux-nxsshauthorizedkeys-resource" class="xliff"></a>

# Linux 用 DSC の nxSshAuthorizedKeys リソース

PowerShell Desired State Configuration (DSC) の **nxAuthorizedKeys** リソースは、特定のユーザーの承認された ssh キーを管理するためのメカニズムを備えています。

<a id="syntax" class="xliff"></a>

## 構文

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

<a id="properties" class="xliff"></a>

## プロパティ

|  プロパティ |  説明 | 
|---|---|
| KeyComment| キーの一意のコメント。 これは、キーを一意に識別するために使用されます。| 
| Ensure| キーが定義されるかどうかを指定します。 ユーザーの承認されたキー ファイルにキーが存在しないようにするには、このプロパティに "Absent" を設定します。 ユーザーの承認されたキー ファイルにキーが定義されるようにするには、このプロパティに "Present" を設定します。| 
| Username| 承認された ssh キーを管理するユーザー名。 定義されていない場合、既定のユーザーは "root" です。| 
| キー| キーの内容。 **Ensure** が "Present" に設定されている場合、これは必須です。| 
| DependsOn | このリソースを構成する前に、他のリソースの構成を実行する必要があることを示します。 たとえば、最初に実行するリソース構成スクリプト ブロックの **ID** が **ResourceName** で、そのタイプが **ResourceType** である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。| 

<a id="example" class="xliff"></a>

## 例

次の例では、ユーザー "monuser" の公開 ssh 承認済みキーを定義しています。

```
Import-DSCResource -Module nx 

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
} 
}
```

