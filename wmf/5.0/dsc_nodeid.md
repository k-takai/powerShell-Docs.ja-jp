---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, PowerShell, セットアップ"
ms.openlocfilehash: 5b9eea1c90bfd5a8cee3897d832bf7775a750308
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="20fe5-102">ノード ID と構成 ID の分離</span><span class="sxs-lookup"><span data-stu-id="20fe5-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="20fe5-103">概要</span><span class="sxs-lookup"><span data-stu-id="20fe5-103">Overview</span></span>

<span data-ttu-id="20fe5-104">プル モードで DSC を使う場合の柔軟性を高め、簡素化するために、今回のリリースでいくつかの機能が追加されました。</span><span class="sxs-lookup"><span data-stu-id="20fe5-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="20fe5-105">これらの機能は、複数のノードに構成を容易にセットアップして展開できる柔軟性と同時に、各ノードの状態を追跡して情報を個別にレポートできる機能も実現します。</span><span class="sxs-lookup"><span data-stu-id="20fe5-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span> <span data-ttu-id="20fe5-106">追加された機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="20fe5-106">These features are as follows:</span></span>

* <span data-ttu-id="20fe5-107">コンピューターの構成を識別する構成名。</span><span class="sxs-lookup"><span data-stu-id="20fe5-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="20fe5-108">この名前は、複数のターゲット ノードで共有できます。</span><span class="sxs-lookup"><span data-stu-id="20fe5-108">This name can be shared by multiple target nodes</span></span> 
* <span data-ttu-id="20fe5-109">1 つのノードを一意に識別するエージェント ID</span><span class="sxs-lookup"><span data-stu-id="20fe5-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="20fe5-110">ターゲット ノードが初めてプル サーバーに接続した時点でのみ実行される登録ステップ</span><span class="sxs-lookup"><span data-stu-id="20fe5-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="20fe5-111">**注:** これらの機能は追加されたものです。既存のプル機能や概念と置き換わるものでありません。</span><span class="sxs-lookup"><span data-stu-id="20fe5-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="20fe5-112">このリリースで出荷された新しいプル サーバーでは、これらの新機能または以前の機能を使うことができます。</span><span class="sxs-lookup"><span data-stu-id="20fe5-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="20fe5-113">詳細については、「[構成名を使用したプル クライアントのセットアップ](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20fe5-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
