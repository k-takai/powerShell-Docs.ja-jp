---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "ギャラリー, PowerShell, コマンドレット, PSGet"
title: psget_moduledependencypopulation
ms.openlocfilehash: 126cd65ac35a31f4118474bc36dac1836ec0f22e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
<a id="logic-for-preparing-the-module-dependencies-during-publish-operation" class="xliff"></a>

# 発行操作中にモジュールの依存関係を準備するためのロジック
1.  RequiredModules の一部として一覧表示されているモジュールは、依存関係として見なされます。
2.  NestedModules の一部として一覧表示されているモジュール (モジュール ベースが指定されたモジュール ベースの下にないモジュール) は、依存関係として見なされます。

3.  上記の依存関係は同じターゲット リポジトリで利用できる必要があります。それ以外の場合、発行操作を実行するとエラーが発生します。
    たとえば、'SnippetPx' をリポジトリで使用できない場合は、以下のエラーがスローされます。
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  一部のモジュールの依存関係は外部で管理できます。その場合は、モジュール マニフェストの PSData セクション内の ExternalModuleDependencies エントリに追加する必要があります。
    上記のエラー メッセージの後半部分
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*モジュールのインストール時に、上記の準備された依存関係一覧が依存関係のインストールに使用されます。*

*発行操作中にモジュールの依存関係がシステムの $env:PSModulePath で使用可能なことを確認してください。*

