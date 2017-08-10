---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "ギャラリー, PowerShell, コマンドレット, PSGallery, PsGet"
title: "PowerShell ギャラリー"
ms.openlocfilehash: 3e324f15b251822163c3ea9b6655767419a5ac4e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="d102b-103">PowerShell ギャラリー</span><span class="sxs-lookup"><span data-stu-id="d102b-103">The PowerShell Gallery</span></span>

<span data-ttu-id="d102b-104">PowerShell ギャラリーは、PowerShell コンテンツの中央リポジトリです。</span><span class="sxs-lookup"><span data-stu-id="d102b-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="d102b-105">ギャラリーには、新しい PowerShell コマンドや Desired State Configuration (DSC) リソースがあります。</span><span class="sxs-lookup"><span data-stu-id="d102b-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="d102b-106">PowerShellGet 概要</span><span class="sxs-lookup"><span data-stu-id="d102b-106">PowerShellGet Overview</span></span>

<span data-ttu-id="d102b-107">PowerShellGet モジュールには、https://www.PowerShellGallery.com でモジュール、DSC リソース、ロール機能、スクリプトなどの PowerShell アーティファクトを検索、インストール、更新、公開するためのコマンドレットとその他のプライベート リポジトリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d102b-107">PowerShellGet module contains cmdlets for discovering, installing, updating and publishing the PowerShell artifacts like Modules, DSC Resources, Role Capabilities and Scripts from the https://www.PowerShellGallery.com and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="d102b-108">ギャラリーをお使いになる前に</span><span class="sxs-lookup"><span data-stu-id="d102b-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="d102b-109">ギャラリーからアイテムをインストールするには、PowerShellGet の最新版が必要です。これは、Windows 10、Windows Management Framework (WMF) 5.0、MSI ベースのインストーラー (PowerShell 3 と 4) で利用できます。</span><span class="sxs-lookup"><span data-stu-id="d102b-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="d102b-110">[**Windows 10 を入手する**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)、</span><span class="sxs-lookup"><span data-stu-id="d102b-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="d102b-111">[**WMF 5.0 を入手する**](http://go.microsoft.com/fwlink/?LinkId=398175)、</span><span class="sxs-lookup"><span data-stu-id="d102b-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="d102b-112">**MSI インストーラーを入手する**</span><span class="sxs-lookup"><span data-stu-id="d102b-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="d102b-113">最新の [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) モジュールで次の操作が可能になります。</span><span class="sxs-lookup"><span data-stu-id="d102b-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="d102b-114">[**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) と [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) でギャラリー内のアイテムを検索する</span><span class="sxs-lookup"><span data-stu-id="d102b-114">Search through items in the Gallery with [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="d102b-115">[**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) と [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) でギャラリーのアイテムをシステムに保存する</span><span class="sxs-lookup"><span data-stu-id="d102b-115">Save items to your system from the Gallery with [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="d102b-116">[**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) と [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) でギャラリーからアイテムをインストールする</span><span class="sxs-lookup"><span data-stu-id="d102b-116">Install items from the Gallery with [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="d102b-117">[**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) と [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) でギャラリーにアイテムをアップロードする</span><span class="sxs-lookup"><span data-stu-id="d102b-117">Upload items to the Gallery with [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="d102b-118">[**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) で独自のリポジトリを追加する</span><span class="sxs-lookup"><span data-stu-id="d102b-118">Add your own custom repository with [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>

<span data-ttu-id="d102b-119">ギャラリーで PowerShellGet コマンドを使用する方法については、[[はじめに]](psgallery/psgallery_gettingstarted.md) ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d102b-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="d102b-120">*Update-Help -Module PowerShellGet* を実行し、コマンドのローカル ヘルプをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d102b-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="d102b-121">サポートされるオペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="d102b-121">Supported Operating Systems</span></span>

<span data-ttu-id="d102b-122">**PowerShellGet** モジュールは **PowerShell 3.0 以降**を必要とします。</span><span class="sxs-lookup"><span data-stu-id="d102b-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="d102b-123">そのため、**PowerShellGet** は次のいずれかのオペレーティング システムを必要とします。</span><span class="sxs-lookup"><span data-stu-id="d102b-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="d102b-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="d102b-124">Windows 10</span></span>
- <span data-ttu-id="d102b-125">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="d102b-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="d102b-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="d102b-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="d102b-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d102b-127">Windows 7 SP1</span></span>
- <span data-ttu-id="d102b-128">Windows Server 2016 TP5</span><span class="sxs-lookup"><span data-stu-id="d102b-128">Windows Server 2016 TP5</span></span>
- <span data-ttu-id="d102b-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d102b-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="d102b-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d102b-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="d102b-131">**PowerShellGet** には、.NET Framework 4.5 以降も必要です。</span><span class="sxs-lookup"><span data-stu-id="d102b-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="d102b-132">.NET Framework 4.5 以降を[ここ](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)からインストールできます。</span><span class="sxs-lookup"><span data-stu-id="d102b-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="d102b-133">ご質問または</span><span class="sxs-lookup"><span data-stu-id="d102b-133">Got a question?</span></span> <span data-ttu-id="d102b-134">フィードバックがある場合は、</span><span class="sxs-lookup"><span data-stu-id="d102b-134">Have feedback?</span></span>

<span data-ttu-id="d102b-135">PowerShell ギャラリーと PowerShellGet の詳細を [[はじめに]](psgallery/psgallery_gettingstarted.md) ページで確認できます。</span><span class="sxs-lookup"><span data-stu-id="d102b-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="d102b-136">[UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) でご意見とご感想をお寄せください。問題がございましたら、ご報告ください。</span><span class="sxs-lookup"><span data-stu-id="d102b-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
