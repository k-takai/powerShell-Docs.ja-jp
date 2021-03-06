---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "ギャラリー, PowerShell, コマンドレット, PSGet"
title: Find-DscResource
ms.openlocfilehash: 37ba7925d6f73c453126f25e0818b3f8839d3b3b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
<a id="find-dscresource" class="xliff"></a>

# Find-DscResource

モジュール内の DSC リソースを検索します。

<a id="description" class="xliff"></a>

## 説明

Find-DscResource コマンドレットは、登録したリポジトリから、指定した条件と一致するモジュールに含まれている [Desired State Configuration (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) リソースを検索します。
Find-DscResource は、このコマンドレットが検出した各モジュールに対して PSGetDscResourceInfo オブジェクトを返します。このオブジェクトを Install-Module にパイプすると、このコマンドレットから返されたリソースを含むモジュールをインストールすることができます。

DSC は、ソフトウェア サービスの構成データを展開および管理し、これらのサービスの実行環境を管理できる、Windows PowerShell の新しい管理プラットフォームです。

Desired State Configuration (DSC) リソースは、DSC 構成の構成要素を提供します。 リソースは、構成 (スキーマ) 可能なプロパティを公開し、また、指定されたことを実現するためにローカル構成マネージャー (LCM) が呼び出す PowerShell スクリプト関数が含まれています。

リソースでは、ファイルのように汎用的なものをモデル化したり、IIS サーバー設定のように具体的なものをモデル化したりできます。 リソースなどのグループは、DSC モジュールに結合されます。DSC モジュールでは、リソースの使用目的を識別するためのメタデータが含まれている移植可能な構造にすべての必須ファイルが編成されます。

- Find-DscResource は、次のバージョン パラメーターでフィルター処理できます。MinimumVersion、RequiredVersion、AllVersions。
  - これらのパラメーターは同時に指定できません。
  - これらのバージョン パラメーターは、ワイルドカードを含まない 1 つのモジュール名が指定されている場合にのみ許可されます。
  - RequiredVersion パラメーターが指定されていない場合、Find-DscResource は指定された最小バージョン以上の最新バージョンのモジュールを返すか、または最新バージョンのモジュールを返します (最小バージョンが指定されていない場合)。
  - RequiredVersion パラメーターが指定されている場合、Find-DscResource は指定したバージョンに完全に一致するバージョンのモジュールのみを返します。
- Find-DscResource では、-Tag パラメーターを使用してモジュールのメタデータをフィルター処理できます。
- Find-DscResource では、-Filter パラメーターを使用してリポジトリ固有の検索言語をフィルター処理できます。
- Find-DscResource では、登録されているリポジトリのすべてまたは一部からモジュール上でフィルター処理できます。

<a id="cmdlet-syntax" class="xliff"></a>

## コマンドレット構文
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>

## コマンドレット オンライン ヘルプ リファレンス

[Find-DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

<a id="example-commands" class="xliff"></a>

## コマンド例
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

