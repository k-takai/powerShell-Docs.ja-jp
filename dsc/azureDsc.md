---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, PowerShell, 構成, セットアップ"
title: "Microsoft Azure での DSC の使用"
ms.openlocfilehash: 9b7d301c3e011b8933b9ee49219e7f0949a5c886
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="9c2d1-103">Microsoft Azure での DSC の使用</span><span class="sxs-lookup"><span data-stu-id="9c2d1-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="9c2d1-104">Microsoft Azure の Desired State Configuration (DSC) は、[Azure Desired State Configuration 拡張機能ハンドラー](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)および [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9c2d1-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) and through [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="9c2d1-105">Azure Desired State Configuration 拡張機能ハンドラー</span><span class="sxs-lookup"><span data-stu-id="9c2d1-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="9c2d1-106">Azure DSC 拡張機能を使用すると、Microsoft Azure でホストされている VM を DSC で管理することができます。</span><span class="sxs-lookup"><span data-stu-id="9c2d1-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span> <span data-ttu-id="9c2d1-107">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c2d1-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="9c2d1-108">Azure Desired State Configuration 拡張機能ハンドラーの概要</span><span class="sxs-lookup"><span data-stu-id="9c2d1-108">Azure Desired State Configuration extension handler</span></span>](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [<span data-ttu-id="9c2d1-109">Azure Resource Manager テンプレートを使用した Windows VMSS および Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="9c2d1-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [<span data-ttu-id="9c2d1-110">資格情報を Azure DSC 拡張機能ハンドラーに渡す</span><span class="sxs-lookup"><span data-stu-id="9c2d1-110">Passing credentials to the Azure DSC extension handler</span></span>](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)

## <a name="azure-automation-dsc"></a><span data-ttu-id="9c2d1-111">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="9c2d1-111">Azure Automation DSC</span></span>

<span data-ttu-id="9c2d1-112">[Azure Automation サービス](https://azure.microsoft.com/services/automation/) を使用すると、DSC 構成、リソース、管理対象ノードを Azure 内で管理することができます。</span><span class="sxs-lookup"><span data-stu-id="9c2d1-112">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="9c2d1-113">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c2d1-113">For more information, see the following topics:</span></span>

- [<span data-ttu-id="9c2d1-114">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="9c2d1-114">Azure Automation DSC</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="9c2d1-115">Azure Automation DSC の使用</span><span class="sxs-lookup"><span data-stu-id="9c2d1-115">Getting started with Azure Automation DSC</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="9c2d1-116">Azure Automation DSC による管理のためのマシンのオンボード</span><span class="sxs-lookup"><span data-stu-id="9c2d1-116">Onboarding machines for management by Azure Automation DSC</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding)
