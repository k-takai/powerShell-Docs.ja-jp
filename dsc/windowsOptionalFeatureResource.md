---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, PowerShell, 構成, セットアップ"
title: "DSC WindowsOptionalFeature リソース"
ms.openlocfilehash: 388fbe1bc430098d6680902e0b5643243fbf7f4c
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="d9df8-103">DSC WindowsOptionalFeature リソース</span><span class="sxs-lookup"><span data-stu-id="d9df8-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="d9df8-104">適用先: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d9df8-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d9df8-105">Windows PowerShell Desired State Configuration (DSC) の **WindowsOptionalFeature** リソースは、オプション機能をターゲット ノードで有効にするためのメカニズムを備えています。</span><span class="sxs-lookup"><span data-stu-id="d9df8-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9df8-106">構文</span><span class="sxs-lookup"><span data-stu-id="d9df8-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="d9df8-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d9df8-107">Properties</span></span>

|  <span data-ttu-id="d9df8-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d9df8-108">Property</span></span>  |  <span data-ttu-id="d9df8-109">説明</span><span class="sxs-lookup"><span data-stu-id="d9df8-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="d9df8-110">名前</span><span class="sxs-lookup"><span data-stu-id="d9df8-110">Name</span></span>| <span data-ttu-id="d9df8-111">有効または無効にする機能の名前を示します。</span><span class="sxs-lookup"><span data-stu-id="d9df8-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>| 
| <span data-ttu-id="d9df8-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="d9df8-112">Ensure</span></span>| <span data-ttu-id="d9df8-113">機能が有効化かどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d9df8-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="d9df8-114">機能を確実に有効にするには、このプロパティを "Enable" に設定します。機能を確実に無効にするには、このプロパティを "Disable" に設定します。</span><span class="sxs-lookup"><span data-stu-id="d9df8-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="d9df8-115">ソース</span><span class="sxs-lookup"><span data-stu-id="d9df8-115">Source</span></span>| <span data-ttu-id="d9df8-116">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="d9df8-116">Not implemented.</span></span>|
| <span data-ttu-id="d9df8-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="d9df8-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="d9df8-118">機能を有効にするソース ファイルを検索するとき、DISM が Windows Update (WU) を確認するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d9df8-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="d9df8-119">$true の場合、DISM は WU を確認しません。</span><span class="sxs-lookup"><span data-stu-id="d9df8-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="d9df8-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="d9df8-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="d9df8-121">**[$true]** に設定すると、無効時に (つまり、**[Ensure]** が "Absent" に設定されているとき)、機能に関連付けられているすべてのファイルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="d9df8-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="d9df8-122">ログ レベル</span><span class="sxs-lookup"><span data-stu-id="d9df8-122">LogLevel</span></span>| <span data-ttu-id="d9df8-123">ログに表示される最大の出力レベル。</span><span class="sxs-lookup"><span data-stu-id="d9df8-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="d9df8-124">有効な値は "ErrorsOnly" (エラーのみが記録されます)、"ErrorsAndWarning" (エラーと警告が記録されます)、"ErrorsAndWarningAndInformation" (エラー、警告、デバッグ情報が記録されます) です。</span><span class="sxs-lookup"><span data-stu-id="d9df8-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="d9df8-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="d9df8-125">LogPath</span></span>| <span data-ttu-id="d9df8-126">リソース プロバイダーの操作を記録するログ ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="d9df8-126">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="d9df8-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d9df8-127">DependsOn</span></span>| <span data-ttu-id="d9df8-128">このリソースを構成する前に、他のリソースの構成を実行する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d9df8-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d9df8-129">たとえば、最初に実行するリソース構成スクリプト ブロックの ID が __ResourceName__ で、そのタイプが __ResourceType__ である場合、このプロパティを使用する構文は `DependsOn = "[ResourceType]ResourceName"` になります。</span><span class="sxs-lookup"><span data-stu-id="d9df8-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
 


