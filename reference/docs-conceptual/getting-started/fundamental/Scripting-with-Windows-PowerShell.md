---
ms.date: 2017-06-05
keywords: "PowerShell, コマンドレット"
title: "Windows PowerShell を使用したスクリプト"
ms.assetid: c425d27a-bb41-4947-8d73-ba5480bc8ee0
ms.openlocfilehash: ac276938c71fa1627a2c9d3346269b89950184d9
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2017
---
# <a name="scripting-with-windows-powershell"></a><span data-ttu-id="e4f0d-103">Windows PowerShell を使用したスクリプト</span><span class="sxs-lookup"><span data-stu-id="e4f0d-103">Scripting with Windows PowerShell</span></span>

<span data-ttu-id="e4f0d-104">Windows PowerShell® は、システム管理に重点を置いて設計されたタスクベースのコマンド ライン シェルおよびスクリプト言語です。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-104">Windows PowerShell® is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="e4f0d-105">.NET Framework 上に構築された Windows PowerShell は、IT 技術者およびパワー ユーザーが Windows オペレーティング システムと Windows 上で実行するアプリケーションの管理の自動化を制御するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-105">Built on the .NET Framework, Windows PowerShell helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="e4f0d-106">*コマンドレット*と呼ばれる Windows PowerShell コマンドを使用すると、コマンド ラインからコンピューターを管理できます。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-106">Windows PowerShell commands, called *cmdlets*, let you manage the computers from the command line.</span></span> <span data-ttu-id="e4f0d-107">Windows PowerShell の*プロバイダー*を使用すると、レジストリや証明書ストアなどのデータ ストアに、ファイル システムにアクセスするのと同じくらい簡単にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-107">Windows PowerShell *providers* let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="e4f0d-108">さらに、Windows PowerShell には、豊富な式パーサーと、完全に開発されたスクリプト言語があります。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-108">In addition, Windows PowerShell has a rich expression parser and a fully developed scripting language.</span></span>

<span data-ttu-id="e4f0d-109">Windows PowerShell には、次に示す機能があります。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-109">Windows PowerShell includes the following features:</span></span>

-   <span data-ttu-id="e4f0d-110">レジストリ、サービス、プロセス、およびイベント ログの管理、Windows Management Instrumentation (WMI) の使用など、一般的なシステム管理タスクを実行するコマンドレットです。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-110">Cmdlets for performing common system administration tasks, such as managing the registry, services, processes, and event logs, and using Windows Management Instrumentation (WMI).</span></span>
-   <span data-ttu-id="e4f0d-111">既存のスクリプトおよびコマンド ライン ツール用のタスク ベースのスクリプト言語およびサポートです。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-111">A task-based scripting language and support for existing scripts and command-line tools.</span></span>
-   <span data-ttu-id="e4f0d-112">一貫した設計。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-112">Consistent design.</span></span> <span data-ttu-id="e4f0d-113">コマンドレットとシステム データ ストアは、共通の構文と命名規則を使用しているため、データを簡単に共有できるとともに、1 つのコマンドレットからの出力を、再フォーマットや操作を実行することなく別のコマンドレットへの入力として使用できます。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-113">Because cmdlets and system data stores use common syntax and naming conventions, data can be shared easily and the output from one cmdlet can be used as the input to another cmdlet without reformatting or manipulation.</span></span>
-   <span data-ttu-id="e4f0d-114">ユーザーがファイル システムの移動に使用するのと同じ手法を使用してレジストリおよびその他のデータ ストアを移動できるようにする、オペレーティング システムの簡略化されたコマンドベースのナビゲーションです。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-114">Simplified, command-based navigation of the operating system, which lets users navigate the registry and other data stores by using the same techniques that they use to navigate the file system.</span></span>
-   <span data-ttu-id="e4f0d-115">強力なオブジェクト操作機能です。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-115">Powerful object manipulation capabilities.</span></span> <span data-ttu-id="e4f0d-116">オブジェクトを直接操作したり、その他のツールやデータベースに送信したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-116">Objects can be directly manipulated or sent to other tools or databases.</span></span>
-   <span data-ttu-id="e4f0d-117">拡張可能なインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-117">Extensible interface.</span></span> <span data-ttu-id="e4f0d-118">独立系ソフトウェア ベンダーや企業の開発者は、自社のソフトウェアを管理するカスタム ツールとユーティリティをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="e4f0d-118">Independent software vendors and enterprise developers can build custom tools and utilities to administer their software.</span></span>
