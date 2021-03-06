---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, PowerShell, セットアップ"
title: "WMF 5.1 のバグ修正"
ms.openlocfilehash: 137095f50f9f926d3488ff9c1ce8270ddbda63eb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
<a id="bug-fixes-in-wmf-51" class="xliff"></a>

# WMF 5.1 のバグ修正

<a id="bug-fixes" class="xliff"></a>

## バグ修正 ##

WMF 5.1 では、次の重要なバグが修正されました。

<a id="module-auto-discovery-fully-honors-envpsmodulepath" class="xliff"></a>

### モジュールの自動検出の完全な受け入れ `$env:PSModulePath` ###

モジュールの自動検出 (コマンド呼び出し時に Import-Module を明示的に指定しないモジュールの自動的な読み込み) が、WMF 3 で導入されました。 導入時、PowerShell は `$env:PSModulePath` を使用する前に `$PSHome\Modules` のコマンドを確認していました。

WMF 5.1 では、この動作が `$env:PSModulePath` を完全に受け入れるように変更されています。 これにより、PowerShell によって提供されるコマンド (`Get-ChildItem` など) を定義するユーザー作成のモジュールを、自動的に読み込み、組み込みコマンドを正しくオーバーライドできます。

<a id="file-redirection-no-longer-hard-codes--encoding-unicode" class="xliff"></a>

### ファイルのリダイレクトの非ハードコード化 `-Encoding Unicode` ###

PowerShell のこれまでのすべてのバージョンでは、PowerShell が `-Encoding Unicode` を追加していたため、ファイル リダイレクト演算子 (`Get-ChildItem > out.txt` など) によって使用されるファイル エンコードを制御できませんでした。

WMF 5.1 からは、`$PSDefaultParameterValues` を設定することによってリダイレクトのファイル エンコードを変更できます。

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

<a id="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo" class="xliff"></a>

### メンバーへのアクセスでのバグ再発の修正 `System.Reflection.TypeInfo` ###

WMF 5.0 で新しく発生したバグにより、`System.Reflection.RuntimeType` のメンバーにアクセスできませんでした (`[int].ImplementedInterfaces` など)。
WMF 5.1 ではこのバグが修正されています。


<a id="fixed-some-issues-with-com-objects" class="xliff"></a>

### COM オブジェクトでのいくつかの問題の修正 ###

WMF 5.0 では、COM オブジェクト上のメソッドを呼び出して COM オブジェクトのプロパティにアクセスする新しい COM バインダーが導入されました。 この新しいバインダーによりパフォーマンスが大幅に向上しましたが、バグもいくつか含まれていました。WMF 5.1 ではそれが修正されました。

<a id="argument-conversions-were-not-always-performed-correctly" class="xliff"></a>

#### 引数の変換が正常に実行されないことがあった ####

次に例を示します。

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

SendKeys メソッドは string を受け取りますが、PowerShell は char を string に変換せず、変換を IDispatch::Invoke に延期していました。このメソッドは VariantChangeType を使用して変換を行います。この例では、結果として、期待される Volume.Mute キーではなくキー "1"、"7"、"3" が送られます。

<a id="enumerable-com-objects-not-always-handled-correctly" class="xliff"></a>

#### 列挙可能な COM オブジェクトが正しく処理されないことがある ####

PowerShell は通常ほとんどの列挙可能なオブジェクトを列挙しますが、WMF 5.0 で発生したバグにより、IEnumerable を実装する COM オブジェクトの列挙が行われませんでした。  たとえば、次のように入力します。

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

上の例では、WMF 5.0 が、キーと値のペアを列挙せずに、誤って Scripting.Dictionary をパイプラインに書き込みます。

この変更は、[Connect の問題 1752224](https://connect.microsoft.com/PowerShell/feedback/details/1752224) も解消します。

<a id="ordered-was-not-allowed-inside-classes" class="xliff"></a>

### `[ordered]` がクラス内で許可されなかった ###

WMF 5.0 では、クラスで使用されるリテラル形を検証するクラスが導入されました。  
`[ordered]` はリテラル形のように見えますが、真の .Net 型ではありません。 WMF 5.0 は、クラスの内の `[ordered]` で誤ってエラーを報告しました。

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


<a id="help-on-about-topics-with-multiple-versions-does-not-work" class="xliff"></a>

### 複数のバージョンがあるトピックについてのヘルプが機能しない ###

WMF 5.1 より前では、複数のバージョンのモジュールがインストールされていて、そのすべてがヘルプ トピック (about_PSReadline など) を共有している場合、`help about_PSReadline` は複数のトピックを返し、実際のヘルプを表示する明確な方法はありませんでした。

WMF 5.1 では、最新バージョンのトピックのヘルプを返すことでこれが解決されています。

`Get-Help` では、必要なヘルプのバージョンを指定する方法はありません。 これを回避するには、モジュール ディレクトリに移動し、好みのエディターなどのツールで直接ヘルプを表示します。 

<a id="powershellexe-reading-from-stdin-stopped-working" class="xliff"></a>

### STDIN からの powershell.exe の読み込みが停止する

ネイティブ アプリから `powershell -command -` を使用して STDIN によるスクリプトで渡される PowerShell を実行していたが、コンソール ホストにほかの変更が加えられたため、これが壊れてしまいました。

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

<a id="powershellexe-creates-spike-in-cpu-usage-on-startup" class="xliff"></a>

### powershell.exe の起動時に CPU 使用率が急増する

PowerShell は、ログインの遅延を回避するために WMI クエリを使用して、グループ ポリシーから起動したかどうかを確認します。
WMI クエリによって、最終的にシステムのすべてのプロセスに tzres.mui.dll が挿入されます。これは、WMI の Win32_Process クラスがローカルのタイムゾーン情報を取得しようとするためです。
結果的に、wmiprvse (WMI プロバイダーのホスト) で、大規模な CPU 使用率の急増が発生します。
修正プログラムでは、WMI を使用する代わりに、Win32 API 呼び出しを使用して同じ情報を取得します。

