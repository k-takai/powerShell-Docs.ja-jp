---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "ギャラリー, PowerShell, コマンドレット, PSGallery"
title: psgallery_search_syntax
ms.openlocfilehash: 409ae607557af760f9cec4e3c54f39e51b5fac18
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
<a id="gallery-search-syntax" class="xliff"></a>

# ギャラリー検索構文

PowerShell ギャラリーでは単語、フレーズ、キーワード表現を使用して検索結果を絞り込むテキスト検索ボックスが用意されています。

<a id="search-by-keywords" class="xliff"></a>

## キーワードで検索

    dsc azure sql

検索では、3 つのキーワードを含む関連ドキュメントを検索すると、最も効果的に一致ドキュメントが返されます。

<a id="search-using-phrases-and-keywords" class="xliff"></a>

## フレーズとキーワードを使用して検索

    "azure sql" deployment

引用符 ("") の間にフレーズを入力すると、個々のキーワードではなく、特定のフレーズの検索に変わります。
一致するドキュメントには通常、大文字と小文字のバリエーション (例: "Azure SQL" など) を含む "azure sql" そのままのフレーズを含み、また通常は 'deployment' という単語も含まれます。

<a id="filtering-on-fields" class="xliff"></a>

## フィールドのフィルター処理

特定の項目 ID (または 'Id'、'id') を検索するか、検索語句の前にフィールド名を付けて他の特定のフィールドを検索します。

検索可能フィールドは現在、'Id'、'Version'、'Tags'、'Author'、'Owner'、'Functions'、'Cmdlets'、'DscResources'、'PowerShellVersion' です。

[ID とタイトルの間の違いは何ですか。 ID とは、コンソールで使用する名前です。 タイトルとは、検索結果の項目ページの上部に表示される内容です。]

<a id="examples" class="xliff"></a>

## 例

    ID:"PSReadline"
    id:"AzureRM.Profile"

ID フィールドの "PSReadline" または "AzureRM.Profile" 項目をそれぞれ検索するとします。

    Id:"AzureRM.Profile"

ID フィールドで "AzureRM.Profile" のある項目を検索する別の方法です。

'Id' フィルターは部分文字列の一致のため、次のように検索した場合、

    Id:"azure"
    
'AzureRM.Profile' と 'Azure.Storage' のような結果が得られます。

また、1 つのフィールドで複数のキーワードを検索することもできます。 または、フィールドを組み合わせて一致させます。

    id:azure tags:intellisense
    id:azure id:storage

また、フレーズ検索も行うことができます。

    id:"azure.storage"


DSC タグのあるすべての項目を検索します。

    Tags:"DSC"

指定した関数のあるすべての項目を検索します。

    Functions:"Update-AzureRM"

指定したコマンドレットのあるすべての項目を検索します。
    
    Cmdlets:"Get-AzureRmEnvironment"

指定した DSC リソース名のあるすべての項目を検索します。

    DscResources:"xArchive"

指定した PowerShellVersion のあるすべての項目を検索します。

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


最後に、'commands' など、サポートされていないフィールドを使用すると、単に無視され、すべてのフィールドが検索されます。 そのため、次のクエリ

    commands:blobs storage
    
は次のクエリと同じものとして解釈されます。

    blobs storage

