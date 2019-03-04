---
ms.date: 06/12/2017
keywords: DSC, PowerShell, 構成, セットアップ
title: DSC ファイル リソース
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047771"
---
# <a name="dsc-file-resource"></a>DSC ファイル リソース

> 適用先:Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) の File リソースは、ターゲット ノード上でファイルとフォルダーを管理するためのメカニズムを備えています。

>**注:****MatchSource** プロパティが **$false** (既定値) に設定されている場合、最初に構成が適用されるとき、コピー対象のコンテンツがキャッシュされます。
>構成の後続のアプリケーションは、**SourcePath** で指定された更新済みのファイルやフォルダーを確認しません。 構成が適用されるたびに **SourcePath** のファイルまたはフォルダーの更新を確認する場合、**MatchSource** を **$true** に設定します。

## <a name="syntax"></a>構文
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>プロパティ

|  プロパティ  |  説明   |
|---|---|
| DestinationPath| ファイルまたはディレクトリの状態を保証する場所を示します。|
| 属性| 対象となるファイルまたはディレクトリの属性の望ましい状態を指定します。|
| チェックサム| 2 つのファイルが同じであるかどうかを決定するときに使用するチェックサム タイプを示します。 __Checksum__ が指定されていない場合、ファイルまたはディレクトリ名のみが比較に使用されます。 有効な値は次のとおりです。Sha-1、sha-256、sha-512、createdDate、modifiedDate です。|
| 内容| 特定の文字列など、ファイルの内容を指定します。|
| Credential| ソース ファイルなどのリソースにアクセスする必要がある場合、このようなアクセスに必要な資格情報を示します。|
| Ensure| ファイルまたはディレクトリが存在するかどうかを示します。 ファイルまたはディレクトリが存在しないことを保証するには、このプロパティを "Absent" に設定します。 ファイルまたはディレクトリが存在することを保証するには、このプロパティを "Present" に設定します。 既定は "Present" です。|
| Force| 特定のファイル操作 (ファイルの上書き、空でないディレクトリの削除など) によって、エラーが発生します。 Force プロパティを使用すると、このようなエラーがオーバーライドされます。 既定値は __$false__ です。|
| Recurse| サブディレクトリが含まれるかどうかを示します。 サブディレクトリを含めるようにするには、このプロパティを __$true__ に設定します。 既定値は __$false__ です。 **注**:このプロパティは、Type プロパティがディレクトリに設定されている場合のみ有効です。|
| DependsOn | このリソースを構成する前に、他のリソースの構成を実行する必要があることを示します。 たとえば、最初に実行するリソース構成スクリプト ブロックの ID が __ResourceName__ で、そのタイプが __ResourceType__ である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。|
| SourcePath| ファイルまたはフォルダー リソースのコピー元のパスを示します。|
| 種類| 構成されているリソースがディレクトリまたはファイルのいずれであるかを示します。 リソースがディレクトリであることを示すには、このプロパティを "Directory" に設定します。 リソースがファイルであることを示すには、"File" に設定します。 既定値は "File" です。|
| MatchSource| 既定値の __$false__ に設定した場合、最初に構成が適用されるときにソース (たとえば、ファイル A、B、および C) 上のファイルが宛先に追加されます。 新しいファイル (D) がソースに追加された場合、構成が後で再適用された場合にも、このファイルは宛先に追加されません。 値が __$true__ の場合、構成が適用されるたびに、後でソースで検出された新しいファイル (この例のファイル D など) が宛先に追加されます。 既定値は **$false** です。|

## <a name="example"></a>例

次の例は、File リソースを使用して、("プル" サーバーなどの) ソース コンピューター上のパス `C:\Users\Public\Documents\DSCDemo\DemoSource` のディレクトリがターゲット ノードにも (すべてのサブディレクトリと共に) 存在することを保証する例を示しています。 また、完了時に確認メッセージもログに書き込まれ、ログ記録操作の前にファイル チェック操作が実行されるようにするステートメントが含まれます。

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```