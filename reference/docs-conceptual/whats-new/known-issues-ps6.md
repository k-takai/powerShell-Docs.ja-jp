---
ms.date: 05/17/2018
keywords: PowerShell、コア
title: PowerShell 6.0 の既知の問題
ms.openlocfilehash: 7fa6b9935ae75b62df72609b8a9ec16246b1c610
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893690"
---
# <a name="known-issues-for-powershell-60"></a>PowerShell 6.0 の既知の問題

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Windows 以外のプラットフォームでの PowerShell に関する既知の問題

Linux および macOS での PowerShell のアルファ版リリースは、ほとんど正常に機能しますが、重要な制限事項と使いやすさの問題がいくつかあります。 Linux および macOS での PowerShell のベータ版リリースは、アルファ版リリースよりもよく機能し安定していますが、まだ機能セットの一部が足りなかったり、バグを含んでいたりする可能性があります。 こうした問題は、単純にまだ修正されていないバグである場合があります。 それ以外の場合は (ls、cp などの既定のエイリアスと同様)、改善に関するコミュニティからのフィードバックをお待ちしております。

注: Linux と macOS の PowerShell は、ベースになっている多くのサブシステムの類似性により、機能とバグの両面において成熟度が同じレベルである傾向があります。 一部の例外を除き、このセクションの問題は両方のオペレーティング システムに該当します。

### <a name="case-sensitivity-in-powershell"></a>PowerShell での大文字と小文字の区別

従来、PowerShell では一様に、少数の例外を除いて、大文字と小文字が区別されませんでした。 UNIX 系のオペレーティング システムでは、大部分のファイル システムで大文字と小文字が区別されます。PowerShell はファイル システムの標準に準拠します。この事実は、明白な場合もそうでない場合も、さまざまな形になって現れます。

#### <a name="directly"></a>直接的な場合

- PowerShell でファイルを指定する場合、大文字と小文字を正確に区別する必要があります。

#### <a name="indirectly"></a>間接的な場合

- モジュールを読み込むスクリプトにおいて、モジュール名の大文字と小文字が正しく区別されていないと、モジュールの読み込みに失敗します。 これは、既存のスクリプトで、モジュールを参照する名前と実際のファイル名が一致していない場合に、問題を発生させる可能性があります。
- ファイル名の大文字と小文字が正しくない場合、タブ補完のオート コンプリートが機能しません。 補完するファイル名の断片は、大文字と小文字を正しく区別する必要があります。 (型名と型のメンバーの補完では、大文字と小文字は区別されません。)

### <a name="ps1-file-extensions"></a>ファイル拡張子 .PS1

PowerShell スクリプトの末尾は `.ps1` である必要があります。これは、スクリプトを読み込んで現在のプロセスで実行する方法を、インタープリターに理解させるためです。 現在のプロセスでスクリプトを実行することは、PowerShell の予期される通常の動作です。 拡張子 `.ps1` を持たないスクリプトには、マジック ナンバー `#!` が追加される場合があります。しかし、この場合、スクリプトは新しい PowerShell インスタンスで実行され、オブジェクトを置き換えるとスクリプトは正常に動作しなくなります。 (注: `bash` またはその他のシェルから PowerShell スクリプトを実行する場合は、この動作が適切である場合があります。)

### <a name="missing-command-aliases"></a>なくなったコマンドのエイリアス

Linux/macOS では、基本的なコマンド `ls`、`cp`、`mv`、`rm`、`cat`、`man`、`mount`、`ps` に対する "便利なエイリアス" は削除されています。 Windows では、ユーザーの利便性のために、Linux コマンドの名前にマッピングするエイリアスのセットが PowerShell に用意されています。 これらのエイリアスは、Linux/macOS ディストリビューションの既定の PowerShell から削除されています。これにより、パスの指定なしでネイティブ実行可能ファイルを実行できます。

これには長所と短所があります。 エイリアスを削除することによって、PowerShell ユーザーはネイティブ コマンドを使用できるようになりますが、ネイティブ コマンドはオブジェクトではなく文字列を返すため、シェルの機能が損なわれます。

> [!NOTE]
> PowerShell チームは、この領域に関するフィードバックをお待ちしております。
> 何が適切なソリューションでしょうか。 このままでよいでしょうか。または、便利なエイリアスを戻すべきでしょうか。 [問題 #929](https://github.com/PowerShell/PowerShell/issues/929) をご覧ください。

### <a name="missing-wildcard-globbing-support"></a>なくなったワイルドカード (グロビング) サポート

現在、PowerShell では、Windows の組み込みコマンドレット、外部コマンドまたはバイナリ、Linux のコマンドレットに対してのみワイルドカードの展開 (グロビング) を行っています。 つまり、`ls
*.txt` のようなコマンドは失敗します。アスタリスクがファイル名に一致するように展開されないためです。 これは、`ls (gci *.txt | % name)` としたり、`ls` と同等な PowerShell の組み込みを使用して単純に `gci *.txt` とすることで回避できます。

Linux/macOS でのグロビングのエクスペリエンス改善に関するフィードバックについては、[#954](https://github.com/PowerShell/PowerShell/issues/954) をご覧ください。

### <a name="net-framework-vs-net-core-framework"></a>.NET Framework と .NET Core Framework

Linux/macOS での PowerShell は .NET Core を使用しています。これは、Microsoft Windows の完全な .NET Framework のサブセットです。 これは重要です。なぜなら、PowerShell では、ベースとなるフレームワークの型、メソッドなどに対する直接アクセスが提供されるためです。このため、フレームワークの違いが原因で、Windows で動作するスクリプトが Windows 以外のプラットフォームでは動作しない場合があります。 .NET Core Framework について詳しくは、<https://dotnetfoundation.org/net-core> をご覧ください

[.NET Standard2.0](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/) の出現により、完全な .NET Framework に存在する従来の型やメソッドの多くが、.NET Core 2.0 で復活します。 つまり、従来の Windows PowerShell モジュールの多くを、変更なしで PowerShell Core に読み込むことができるようになります。 .NET Standard 2.0 に関連する作業については、[こちら](https://github.com/PowerShell/PowerShell/projects/4)をご覧ください。

### <a name="redirection-issues"></a>リダイレクトの問題

入力のリダイレクトは、すべてのプラットフォームの PowerShell でサポートされていません。
[問題 #1629](https://github.com/PowerShell/PowerShell/issues/1629)

ファイルのコンテンツをパイプラインに書き込むには、`Get-Content` を使用します。

リダイレクトされた出力には、既定の UTF-8 エンコードを使用する場合、Unicode バイト オーダー マーク (BOM) が含まれます。 BOM を予期しないユーティリティを操作する場合や、ファイルに追加する場合、BOM によって問題が発生します。 ASCII テキストを書き込むには、`-Encoding Ascii` を使用します (Unicode ではないため、BOM を含みません)。

> [!Note]
> すべてのプラットフォームにおける PowerShell Core のエンコードのエクスペリエンス改善に関するフィードバックについては、[RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) をご覧ください。 現在 BOM なしの UTF-8 のサポートに取り組んでおり、全プラットフォームのさまざまなコマンドレットに対してエンコードの既定値が変更される可能性があります。

### <a name="job-control"></a>ジョブ制御

Linux/macOS での PowerShell では、ジョブ制御はサポートされていません。
`fg` コマンドと `bg` コマンドは使用できません。

当面の間は、すべてのプラットフォームで動作する [PowerShell ジョブ](/powershell/module/microsoft.powershell.core/about/about_jobs)を使用できます。

### <a name="remoting-support"></a>リモート処理のサポート

現在、PowerShell Core では、基本認証 (macOS/Linux) および NTLM ベースの認証 (Linux) を使用した、WSMan 経由の PowerShell リモート処理 (PSRP) をサポートしています。 (Kerberos ベースの認証はサポートされていません。)

WSMan ベースのリモート処理に向けた作業は、[psl-omi-provider](https://github.com/PowerShell/psl-omi-provider) リポジトリで行われています。

また、PowerShell Core では、すべてのプラットフォーム (Windows、macOS、Linux) で、SSH 経由の PowerShell リモート処理 (PSRP) もサポートしています。 現在、これは運用環境ではサポートされていませんが、設定の詳細については[こちら](../core-powershell/ssh-remoting-in-powershell-core.md)をご覧ください。

### <a name="just-enough-administration-jea-support"></a>Just-Enough-Administration (JEA) のサポート

現在、Linux/macOS での PowerShell では、制限付き管理 (JEA) リモート処理エンドポイントを作成する機能は利用できません。 この機能は現在 6.0 のスコープに含まれていません。多くの設計作業を必要とするため、この案の検討は 6.0 以降になります。

### <a name="sudo-exec-and-powershell"></a>`sudo`､`exec`、PowerShell

PowerShell では、ほとんどのコマンドがメモリ内で実行されるため (Python や Ruby のように)、PowerShell の組み込み要素と共に sudo を直接使用することはできません。(もちろん、sudo から `powershell` を実行することはできます。)PowerShell 内から sudo と共に PowerShell コマンドレット (例: `sudo `Set-Date` 8/18/2016`) を実行する必要がある場合は、`sudo powershell `Set-Date` 8/18/2016` とします。 同様に、PowerShell の組み込み要素を直接実行することはできません。 代わりに、`exec powershell item_to_exec` とする必要があります。

現在、この問題は #3232 の一部として追跡されています。

### <a name="missing-cmdlets"></a>なくなったコマンドレット

通常 PowerShell で使用できるコマンド (コマンドレット) の多数が、Linux/macOS では利用できません。 多くの場合、このようなコマンドはこれらのプラットフォーム上では役に立ちません (例: レジストリのような Windows 固有の機能)。 サービス コントロール コマンド (Get/Start/Stop-Service) のようなその他のコマンドは、存在しますが機能しません。 これらの問題は今後のリリースで修正されます。バグのあるコマンドレットが直され、新しいコマンドレットが時間と共に追加されます。

### <a name="command-availability"></a>コマンドの可用性

Linux/macOS での PowerShell で動作しないことが知られているコマンドを、次の表に一覧表示します。

|コマンド |動作状態 | メモ|
|---------|------------------|------|
|`Get-Service`、`New-Service`、`Restart-Service`、`Resume-Service`、`Set-Service`、`Start-Service`、`Stop-Service`、`Suspend-Service`|使用できません。|これらのコマンドは認識されません。 将来のリリースで修正する必要があります。|
|`Get-Acl`、`Set-Acl`|使用できません。|これらのコマンドは認識されません。 将来のリリースで修正する必要があります。|
|`Get-AuthenticodeSignature`、`Set-AuthenticodeSignature`|使用できません。|これらのコマンドは認識されません。 将来のリリースで修正する必要があります。|
|`Wait-Process`|使用できますが、正常に動作しません。 |たとえば、`Start-Process gvim -PassThru | Wait-Process` は動作しません。プロセスの待機に失敗します。|
|`Register-PSSessionConfiguration`、`Unregister-PSSessionConfiguration`、`Get-PSSessionConfiguration`|使用できますが、動作しません。|コマンドが動作していないことを示すエラー メッセージが書き込まれます。 これらは、将来のリリースで修正する必要があります。|
|`Get-Event`、`New-Event`、`Register-EngineEvent`、`Register-WmiEvent`、`Remove-Event`、`Unregister-Event`|使用できますが、イベント ソースを使用できません。|PowerShell のイベント処理コマンドは存在はしますが、各コマンドで使用されるイベント ソース (System.Timers.Timer など) のほとんどが Linux では使用できません。そのため、アルファ版リリースではこれらのコマンドは役に立ちません。|
|`Set-ExecutionPolicy`|使用できますが、動作しません。|このプラットフォームでサポートされていないことを示すメッセージが返されます。 実行ポリシーとは、ユーザーに重点を置いた "安全ベルト" であり、ユーザーがコストの高いミスをすることを回避します。 これはセキュリティ境界ではありません。|
|`New-PSSessionOption`、`New-PSTransportOption`|使用できますが、`New-PSSession` が機能しません。|`New-PSSession` が動作するようになったため、`New-PSSessionOption` と `New-PSTransportOption` の動作は現在確認されていません。|