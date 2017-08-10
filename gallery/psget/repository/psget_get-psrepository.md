---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "ギャラリー, PowerShell, コマンドレット, PSGet"
title: Get-PSRepository
ms.openlocfilehash: 96f87428312c233757aa5fcae405a192aadff385
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
# <a name="get-psrepository"></a><span data-ttu-id="f5c90-103">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f5c90-103">Get-PSRepository</span></span>

<span data-ttu-id="f5c90-104">コンピューター上の登録されているリポジトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="f5c90-104">Gets the registered repositories on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="f5c90-105">説明</span><span class="sxs-lookup"><span data-stu-id="f5c90-105">Description</span></span>

<span data-ttu-id="f5c90-106">Get-PSRepository コマンドレットでは、コンピューター上の現在のユーザーに対して登録されている PowerShell モジュール リポジトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="f5c90-106">The Get-PSRepository cmdlet gets PowerShell module repositories that are registered for the current user on a computer.</span></span>

<span data-ttu-id="f5c90-107">登録されている各リポジトリに対して、Get-PSRepository は PSRepository オブジェクトを返します。これは必要に応じて登録済みのリポジトリの登録を解除するための Unregister-PSRepository にパイプできます。</span><span class="sxs-lookup"><span data-stu-id="f5c90-107">For each registered repository, Get-PSRepository returns a PSRepository object which can optionally be piped to Unregister-PSRepository for unregistering a registered repository.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="f5c90-108">コマンドレット構文</span><span class="sxs-lookup"><span data-stu-id="f5c90-108">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="f5c90-109">コマンドレット オンライン ヘルプ リファレンス</span><span class="sxs-lookup"><span data-stu-id="f5c90-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="f5c90-110">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f5c90-110">Get-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517127)

## <a name="example-commands"></a><span data-ttu-id="f5c90-111">コマンド例</span><span class="sxs-lookup"><span data-stu-id="f5c90-111">Example commands</span></span>

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```
