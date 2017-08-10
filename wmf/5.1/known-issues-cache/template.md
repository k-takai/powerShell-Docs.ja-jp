---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, PowerShell, セットアップ"
title: "既知の問題または制限の書き込みのテンプレート例"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="5bfe8-103">注: わかりやすいタイトルと簡単な説明を提供します</span><span class="sxs-lookup"><span data-stu-id="5bfe8-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="5bfe8-104">例: Erroneous ExecutionPolicy エラー</span><span class="sxs-lookup"><span data-stu-id="5bfe8-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="5bfe8-105">Windows 7 で PowerShell モジュールと DSC リソースを使用すると、ExecutionPolicy についてレポートされるエラーとなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5bfe8-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="5bfe8-106">解決方法</span><span class="sxs-lookup"><span data-stu-id="5bfe8-106">Resolution</span></span>

<span data-ttu-id="5bfe8-107">解決するには、管理者特権の PowerShell セッション (管理者として実行) で、次のコマンドを実行して **ExecutionPolicy** を **RemoteSigned** に設定します。</span><span class="sxs-lookup"><span data-stu-id="5bfe8-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
