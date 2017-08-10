---
ms.date: 2017-06-05
keywords: "PowerShell, コマンドレット"
title: "PowerShellTab オブジェクト"
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: d4e9374202d352a30b3eb46bcf1e4e40dea49822
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2017
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="5cf55-103">PowerShellTab オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5cf55-103">The PowerShellTab Object</span></span>
  <span data-ttu-id="5cf55-104">**PowerShellTab** オブジェクトは、Windows PowerShell ランタイム環境を表します。</span><span class="sxs-lookup"><span data-stu-id="5cf55-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="5cf55-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5cf55-105">Methods</span></span>

###  <span data-ttu-id="5cf55-106"><a name="invoke"></a> Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="5cf55-106"><a name="invoke"></a> Invoke\( Script \)</span></span>
  <span data-ttu-id="5cf55-107">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5cf55-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5cf55-108">指定したスクリプトを [PowerShell] タブで実行します。</span><span class="sxs-lookup"><span data-stu-id="5cf55-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="5cf55-109">このメソッドは、その他の [PowerShell] タブでのみ機能し、実行元となる [PowerShell] タブでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="5cf55-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="5cf55-110">このコマンドはオブジェクトや値を返しません。</span><span class="sxs-lookup"><span data-stu-id="5cf55-110">It does not return any object or value.</span></span> <span data-ttu-id="5cf55-111">このコードによって変数が変更されると、その変更はコマンドが呼び出されたタブで保持されます。</span><span class="sxs-lookup"><span data-stu-id="5cf55-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

 <span data-ttu-id="5cf55-112">**Script** - System.Management.Automation.ScriptBlock または文字列。実行するスクリプト ブロック。</span><span class="sxs-lookup"><span data-stu-id="5cf55-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="5cf55-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="5cf55-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>
  <span data-ttu-id="5cf55-114">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="5cf55-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="5cf55-115">指定したスクリプトを [PowerShell] タブで実行します。</span><span class="sxs-lookup"><span data-stu-id="5cf55-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="5cf55-116">このメソッドは、その他の [PowerShell] タブでのみ機能し、実行元となる [PowerShell] タブでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="5cf55-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="5cf55-117">スクリプト ブロックが実行され、スクリプトから返される値はコマンドを呼び出した実行環境に返されます。</span><span class="sxs-lookup"><span data-stu-id="5cf55-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="5cf55-118">コマンドが **millesecondsTimeout** の値で指定した時間内に完了しない場合、コマンドが失敗して例外 "処理がタイムアウトになりました。" が発生します。</span><span class="sxs-lookup"><span data-stu-id="5cf55-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

 <span data-ttu-id="5cf55-119">**Script** - System.Management.Automation.ScriptBlock または文字列。実行するスクリプト ブロック。</span><span class="sxs-lookup"><span data-stu-id="5cf55-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

 <span data-ttu-id="5cf55-120">**\[useNewScope\]** - 省略可能なブール値で、既定は **$true**
 です。**$true** に設定されると、そのコマンドを実行する新しいスコープが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5cf55-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true**
 If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="5cf55-121">コマンドで指定されている [PowerShell] タブのランタイム環境は変更されません。</span><span class="sxs-lookup"><span data-stu-id="5cf55-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

 <span data-ttu-id="5cf55-122">**\[millisecondsTimeout\]** - **500** を既定値とする省略可能な整数。</span><span class="sxs-lookup"><span data-stu-id="5cf55-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="5cf55-123">指定した時間内にコマンドが完了しない場合、コマンドによって **TimeoutException** が生成され、"処理がタイムアウトになりました。" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5cf55-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```
# create a new PowerShell tab and then switch back to the first
$PSise.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0]) 

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1',$false)
# You can switch to the other tab and type “$x” to see that the value is saved there.

# This example sets a value in the other tab (in a different scope) 
# and returns it through the pipeline to this tab to store in $a
$a=$psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z') 
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
measure-command {$psISE.PowerShellTabs[1].InvokeSynchronous("sleep 10",$false,5000)}

```

## <a name="properties"></a><span data-ttu-id="5cf55-124">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5cf55-124">Properties</span></span>

###  <span data-ttu-id="5cf55-125"><a name="AddOnsMenu"></a> AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="5cf55-125"><a name="AddOnsMenu"></a> AddOnsMenu</span></span>
  <span data-ttu-id="5cf55-126">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5cf55-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5cf55-127">[PowerShell] タブのアドオン メニューを取得する読み取り専用のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5cf55-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

###  <span data-ttu-id="5cf55-128"><a name="CanExecute"></a> CanInvoke</span><span class="sxs-lookup"><span data-stu-id="5cf55-128"><a name="CanExecute"></a> CanInvoke</span></span>
  <span data-ttu-id="5cf55-129">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5cf55-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5cf55-130">スクリプトを [Invoke( Script )](#invoke) メソッドで呼び出すことが可能な場合は **$true** を返す、読み取り専用のブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5cf55-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke) method.</span></span>

```
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab. 
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psise.PowerShellTabs[1] 
$secondTab.CanInvoke 
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke

```

###  <span data-ttu-id="5cf55-131"><a name="Commandpane"></a> Consolepane</span><span class="sxs-lookup"><span data-stu-id="5cf55-131"><a name="Commandpane"></a> Consolepane</span></span>
  <span data-ttu-id="5cf55-132">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="5cf55-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="5cf55-133">Windows PowerShell ISE 2.0 では、このパラメータの名前は **CommandPane** でした。</span><span class="sxs-lookup"><span data-stu-id="5cf55-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

 <span data-ttu-id="5cf55-134">コンソール ウィンドウの [editor](../ise/The-ISEEditor-Object.md) オブジェクトを取得する読み取り専用のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5cf55-134">The read-only property that gets the Console pane [editor](../ise/The-ISEEditor-Object.md) object.</span></span>

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

###  <span data-ttu-id="5cf55-135"><a name="Displayname"></a> DisplayName</span><span class="sxs-lookup"><span data-stu-id="5cf55-135"><a name="Displayname"></a> DisplayName</span></span>
  <span data-ttu-id="5cf55-136">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5cf55-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5cf55-137">[PowerShell] タブに表示されるテキストを取得または設定する読み取り/書き込みプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5cf55-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab.</span></span> <span data-ttu-id="5cf55-138">既定では、タブ名は "PowerShell #" となり、「#」には番号が入ります。</span><span class="sxs-lookup"><span data-stu-id="5cf55-138">By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

###  <span data-ttu-id="5cf55-139"><a name="ExpandedScript"></a> ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="5cf55-139"><a name="ExpandedScript"></a> ExpandedScript</span></span>
  <span data-ttu-id="5cf55-140">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5cf55-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5cf55-141">スクリプト ウィンドウが展開されているか非表示かどうかを特定する読み取り/書き込みブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5cf55-141">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

###  <span data-ttu-id="5cf55-142"><a name="Files"></a> Files</span><span class="sxs-lookup"><span data-stu-id="5cf55-142"><a name="Files"></a> Files</span></span>
  <span data-ttu-id="5cf55-143">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5cf55-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5cf55-144">[PowerShell] タブで開かれている[スクリプト ファイルのコレクション](../ise/The-ISEFileCollection-Object.md)を取得する読み取り専用のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5cf55-144">The read-only property that gets the [collection of script files](../ise/The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

###  <span data-ttu-id="5cf55-145"><a name="Output"></a> Output</span><span class="sxs-lookup"><span data-stu-id="5cf55-145"><a name="Output"></a> Output</span></span>
  <span data-ttu-id="5cf55-146">この機能は、Windows PowerShell ISE 2.0 に存在しますが、それよりも後のバージョンの ISE では削除されているか、名前が変更されています。</span><span class="sxs-lookup"><span data-stu-id="5cf55-146">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="5cf55-147">Windows PowerShell ISE 2.0 より後のバージョンでは、**ConsolePane** オブジェクトを同じ目的で使用できます。</span><span class="sxs-lookup"><span data-stu-id="5cf55-147">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

 <span data-ttu-id="5cf55-148">現在の[エディター](../ise/The-ISEEditor-Object.md)の出力ウィンドウが取得する読み取り専用のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5cf55-148">The read-only property that gets the Output pane of the current [editor](../ise/The-ISEEditor-Object.md).</span></span>

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

###  <span data-ttu-id="5cf55-149"><a name="Prompt"></a> Prompt</span><span class="sxs-lookup"><span data-stu-id="5cf55-149"><a name="Prompt"></a> Prompt</span></span>
  <span data-ttu-id="5cf55-150">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5cf55-150">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5cf55-151">現在のプロンプト テキストを取得する読み取り専用のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5cf55-151">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="5cf55-152">注: **Prompt** 関数は、ユーザーのプロファイルで上書きできます。</span><span class="sxs-lookup"><span data-stu-id="5cf55-152">Note: the **Prompt** function can be overridden by the user’s profile.</span></span> <span data-ttu-id="5cf55-153">結果が単純な文字列以外の場合、このプロパティは何も返しません。</span><span class="sxs-lookup"><span data-stu-id="5cf55-153">If the result is other than a simple string, then this property returns nothing.</span></span>

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

###  <span data-ttu-id="5cf55-154"><a name="ShowCommands"></a> ShowCommands</span><span class="sxs-lookup"><span data-stu-id="5cf55-154"><a name="ShowCommands"></a> ShowCommands</span></span>
  <span data-ttu-id="5cf55-155">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="5cf55-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="5cf55-156">コマンド ウィンドウが現在表示されているかどうかを示す読み取り/書き込みプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5cf55-156">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

###  <span data-ttu-id="5cf55-157"><a name="StatusText"></a> StatusText</span><span class="sxs-lookup"><span data-stu-id="5cf55-157"><a name="StatusText"></a> StatusText</span></span>
  <span data-ttu-id="5cf55-158">Windows PowerShell ISE 2.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5cf55-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5cf55-159">**PowerShellTab** ステータス テキストを取得する読み取り専用のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5cf55-159">The read-only property that gets the **PowerShellTab** status text.</span></span>

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

###  <span data-ttu-id="5cf55-160"><a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="5cf55-160"><a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened</span></span>
  <span data-ttu-id="5cf55-161">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="5cf55-161">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="5cf55-162">水平方向のアドオン ツール ウィンドウが現在開いているかどうかを示す読み取り専用のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5cf55-162">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

###  <span data-ttu-id="5cf55-163"><a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**</span><span class="sxs-lookup"><span data-stu-id="5cf55-163"><a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**</span></span>
  <span data-ttu-id="5cf55-164">Windows PowerShell ISE 3.0 以降でサポートされており、それよりも前のバージョンには存在しません。</span><span class="sxs-lookup"><span data-stu-id="5cf55-164">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="5cf55-165">垂直方向のアドオン ツール ウィンドウが現在開いているかどうかを示す読み取り専用のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5cf55-165">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="5cf55-166">参照</span><span class="sxs-lookup"><span data-stu-id="5cf55-166">See Also</span></span>
- [<span data-ttu-id="5cf55-167">PowerShellTabCollection オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5cf55-167">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md) 
- [<span data-ttu-id="5cf55-168">Windows PowerShell ISE スクリプト オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="5cf55-168">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="5cf55-169">Windows PowerShell ISE オブジェクト モデル リファレンス</span><span class="sxs-lookup"><span data-stu-id="5cf55-169">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="5cf55-170">ISE オブジェクト モデルの階層</span><span class="sxs-lookup"><span data-stu-id="5cf55-170">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  