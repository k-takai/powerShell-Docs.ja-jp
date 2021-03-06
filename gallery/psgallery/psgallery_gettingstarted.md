---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "ギャラリー, PowerShell, コマンドレット, PSGallery"
title: psgallery_gettingstarted
ms.openlocfilehash: 6b2119a736cc428598c245526e5af970d86af998
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2017
---
<a id="get-started-with-the-powershell-gallery" class="xliff"></a>

# PowerShell ギャラリーの概要

<a id="what-is-the-powershell-gallery" class="xliff"></a>

## PowerShell ギャラリーとは

PowerShell ギャラリーは、PowerShell コンテンツの中央リポジトリです。
ここには、PowerShell コマンドと Desired State Configuration (DSC) リソースを含む、便利な PowerShell モジュールがあります。 また、PowerShell スクリプトもあり、その一部には一連のタスクとそのタスクの順序の概要を示す PowerShell ワークフローが含まれています。
この項目の一部は Microsoft によって作成されており、その他は PowerShell コミュニティによって作成されています。

<a id="requirements" class="xliff"></a>

## 要件

PowerShell ギャラリーからシステムに項目をダウンロードするには、[PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) モジュールが必要です。 PowerShellGet モジュールは次のいずれかで見つかります。 PowerShell ギャラリーから項目をダウンロードするのにサインインする必要はありません。

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [MSI インストーラー (PowerShell 3 および 4 の場合)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

PowerShellGet では、PowerShell ギャラリーと連携する [NuGet プロバイダー](http://go.microsoft.com/fwlink/?LinkId=722208) も必要です。 PowerShellGet を最初にインストールするときに、NuGet プロバイダーが次の場所にない場合、自動的に NuGet プロバイダーをインストールするよう求められます。

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

または、`Install-PackageProvider -Name NuGet -Force` を実行して、NuGet プロバイダーのダウンロードとインストールを自動化できます。

  
NuGet の 2.8.5.201 より前のバージョンがある場合は、以下の PowerShell コマンドレットを呼び出し、NuGet の最新バージョンをインストールして切り替える必要があります。

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  上記のインストール場所から、NuGet の古いバージョンを削除します。

詳細については、<http://oneget.org/> をご覧ください。

  
注: パッケージの形式が変更されたため、最近更新された項目をインストールするには、PowerShellGet と PackageManagement の最新バージョンに更新することをお勧めします。 PowerShellGet は Windows 10 に含まれています。詳細については、[こちら](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)をご覧ください。
PowerShellGet は Windows Management Framework (WMF) 5.0 の一部でもあり、[こちら](http://go.microsoft.com/fwlink/?LinkId=398175)からダウンロードできます。

<a id="discovering-items-from-the-powershell-gallery" class="xliff"></a>

## PowerShell ギャラリーでの項目の検出

この Web サイトで**検索**コントロールを使用するか、[モジュールとスクリプト] ページを閲覧すると PowerShell ギャラリーの項目が見つかります。 また、[**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) および [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) コマンドレットを、アイテムの種類に応じて `-Repository PSGallery` を指定して実行すると、PowerShell ギャラリーからアイテムを検索できます。

次の [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) および [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) パラメーターを使用すると、ギャラリーからの結果をフィルター処理できます。

- 名前
- AllVersions
- MinimumVersion
- RequiredVersion
- タグ
- Includes
- DscResource
- RoleCapability
- コマンド
- フィルター

ギャラリー内の特定の DSC リソースのみを検出したい場合は、[**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) コマンドレットを実行します。
[**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) では、ギャラリーに含まれている DSC リソースのデータが返されます。 DSC リソースは常にモジュールの一部として配布されるため、この DSC リソースをインストールする場合も [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) を実行する必要があります。

<a id="learning-about-items-in-the-powershell-gallery" class="xliff"></a>

## PowerShell ギャラリーの項目の詳細

関心のある項目を特定できたら、その詳細を入手することができます。 これは、ギャラリー上で項目の特定のページを調べると見つかります。 そのページでは、その項目と共にアップロードされているメタデータをすべて参照することができます。 この項目のメタデータは項目の作成者が提供するものであり、Microsoft で検証したものではありません。 項目の所有者は、項目の公開に使用したギャラリーのアカウントと厳密に関連付けられており、[作成者] フィールドよりも信頼性があります。

誠意をもって公開されていると思われない項目が見つかった場合は、その項目のページの **[不正使用を報告]** をクリックします。

[**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) または [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) を実行している場合、返される PSGetModuleInfo オブジェクトにこのデータが表示されます。 たとえば、[**Find-Module -Name PSReadLine -Repository PSGallery | Get-Member**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) を実行すると、ギャラリーの PSReadLine モジュールにデータが返されます。

<a id="downloading-items-from-the-powershell-gallery" class="xliff"></a>

## PowerShell ギャラリーでの項目のダウンロード

PowerShell ギャラリーから項目をダウンロードするとき、次のプロセスをお勧めします。

<a id="inspect" class="xliff"></a>

### 検査

検査のためにギャラリーから項目をダウンロードするには、項目の種類に応じて [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) または [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) コマンドレットを実行します。 これにより、項目をインストールすることなくローカルに保存し、項目の内容を検査することができます。 保存した項目は必ず手動で削除してください。

この項目の一部は Microsoft によって作成されており、その他は PowerShell コミュニティによって作成されています。 このギャラリーの項目の内容とコードは、インストールする前に確認することをお勧めします。

誠意をもって公開されていると思われない項目が見つかった場合は、その項目のページの **[不正使用を報告]** をクリックします。

<a id="install" class="xliff"></a>

### [インストール]

使用のためにギャラリーから項目をインストールするには、項目の種類に応じて [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) または [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) コマンドレットを実行します。

[**Install-module** ](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) は、既定では `$env:ProgramFiles\WindowsPowerShell\Modules` にモジュールをインストールします。 これには管理者アカウントが必要です。 `-Scope
CurrentUser` パラメーターを追加する場合は、モジュールは `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` にインストールされます。

[**Install-script** ](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) は、既定では、 `$env:ProgramFiles\WindowsPowerShell\Scripts` にスクリプトをインストールします。 これには管理者アカウントが必要です。 `-Scope
CurrentUser` パラメーターを追加する場合は、スクリプトは `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` にインストールされます。

既定では、 [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) および [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) は最新バージョンのアイテムをインストールします。 前のバージョンのアイテムをインストールするには、 `-RequiredVersion` パラメーターを追加します。

<a id="deploy" class="xliff"></a>

### 展開

項目を PowerShell ギャラリーから Azure Automation にデプロイするには、項目の詳細ページで **[Azure Automation にデプロイする]** をクリックします。 Azure 管理ポータルにリダイレクトされるため、そこでAzure アカウント資格情報を使用してサインインします。 依存関係のある項目をデプロイすると、すべての依存関係が Azure Automation にデプロイされることに注意してください。 [Azure Automation にデプロイする] ボタンは、**AzureAutomationNotSupported** タグを項目のメタデータに追加すると無効にできます。

Azure Automation の詳細については、[Azure Automation の Web サイト](http://azure.microsoft.com/en-us/services/automation/) をご覧ください。

<a id="updating-items-from-the-powershell-gallery" class="xliff"></a>

## PowerShell ギャラリーからの項目の更新

PowerShell ギャラリーからインストールされたアイテムを更新するには、 [**Update-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) または [**Update-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) コマンドレットを実行します。 パラメーターを追加せずに [**Update-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) を実行すると、[**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) を実行してインストールされた各モジュールが更新されます。
モジュールを選択して更新するには、`-Name` パラメーターを追加します。

同様に、パラメーターを追加せずに [**Update-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) を実行すると、[**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) を実行してインストールされた各スクリプトが更新されます。
スクリプトを選択して更新するには、`-Name` パラメーターを追加します。

<a id="list-items-that-you-have-installed-from-the-powershell-gallery" class="xliff"></a>

## PowerShell ギャラリーからインストールした項目の一覧

PowerShell ギャラリーからどのモジュールをインストールしたかを調べるには、[**Get-InstalledModule**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) コマンドレットを実行します。 このコマンドは、PowerShell ギャラリーから直接インストールした、システム上にあるモジュールをすべて一覧表示します。

同様に、PowerShell ギャラリーからどのスクリプトをインストールしたかを調べるには、[**Get-InstalledScript**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) コマンドレットを実行します。 このコマンドは、PowerShell ギャラリーから直接インストールした、システム上にあるスクリプトをすべて一覧表示します。

