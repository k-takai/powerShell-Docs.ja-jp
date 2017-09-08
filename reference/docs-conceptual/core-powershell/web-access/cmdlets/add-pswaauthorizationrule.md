---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "PowerShell, コマンドレット"
ms.date: 2016-12-12
title: add pswaauthorizationrule
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 12f5cc30d4e3f9cfdd739cacbbab96134077e50a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2017
---
#  <a name="add-pswaauthorizationrule"></a><span data-ttu-id="1327b-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1327b-103">Add-PswaAuthorizationRule</span></span>

##  <a name="synopsis"></a><span data-ttu-id="1327b-104">概要</span><span class="sxs-lookup"><span data-stu-id="1327b-104">SYNOPSIS</span></span>

<span data-ttu-id="1327b-105">Windows PowerShell® Web Access 承認規則のセットに新しい承認規則を追加します。</span><span class="sxs-lookup"><span data-stu-id="1327b-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="1327b-106">構文</span><span class="sxs-lookup"><span data-stu-id="1327b-106">Syntax</span></span>

###  <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="1327b-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="1327b-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usergroupnamecomputername"></a><span data-ttu-id="1327b-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="1327b-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputergroupname"></a><span data-ttu-id="1327b-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="1327b-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputername"></a><span data-ttu-id="1327b-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="1327b-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="1327b-111">説明</span><span class="sxs-lookup"><span data-stu-id="1327b-111">DESCRIPTION</span></span>

<span data-ttu-id="1327b-112">**Add-PswaAuthorizationRule** コマンドレットは、Windows PowerShell® Web Access 承認規則のセットに新しい承認規則を追加します。</span><span class="sxs-lookup"><span data-stu-id="1327b-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="1327b-113">この規則には、ユーザー、コンピューター、Windows PowerShell エンドポイントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1327b-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="1327b-114">個々のユーザー アカウント名、コンピューター名、またはグループを指定して、ユーザーとコンピューターの両方を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1327b-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="1327b-115">Active Directory ドメインに参加しているコンピューターの場合、このコマンドレットは、コンピューターのセキュリティ識別子 (SID) を使用して規則を作成します。</span><span class="sxs-lookup"><span data-stu-id="1327b-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="1327b-116">そのため、サインイン ページの **[コンピューター名]** フィールドに、短い名前、完全修飾ドメイン名 (FQDN)、または IP アドレスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1327b-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="1327b-117">Active Directory ドメインに参加していないコンピューターの場合、このコマンドレットは、管理者が指定したコンピューター名を使用して規則を作成します。</span><span class="sxs-lookup"><span data-stu-id="1327b-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="1327b-118">このコンピューターに正常に接続するには、規則に指定されているとおりのコンピューター名をエンド ユーザーが正確に入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1327b-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="1327b-119">ネットワーク上に同じ名前のコンピューターが複数ある場合、短い名前では複数のコンピューターに解決される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1327b-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="1327b-120">その結果、接続を確立するときにあいまいさが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1327b-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="1327b-121">たとえば、"*Server1*" というワークグループ コンピューターの規則が存在し、*server1.contoso.com* という新しいコンピューターがネットワークに参加した場合、承認規則を使用した確認は成功し、PowerShell Web Access は、"*Server1*" というコンピューターに接続を確立しようとします。</span><span class="sxs-lookup"><span data-stu-id="1327b-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="1327b-122">指定されたワークグループ コンピューターで接続が確立されることは保証されません。試行は、"*Server1*" という名前のワークグループまたはドメイン コンピューターに対して行われます。</span><span class="sxs-lookup"><span data-stu-id="1327b-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="1327b-123">承認規則を作成するには、あいまいさを減らすために、対象コンピューターの FQDN を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1327b-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="1327b-124">承認規則は、代替資格情報ではなく、Windows PowerShell Web Access ユーザーのプライマリ サインイン資格情報を評価します (代替資格情報は、サインイン ページの **[オプションの接続設定]** セクションにある 2 つ目の資格情報セットです)。</span><span class="sxs-lookup"><span data-stu-id="1327b-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="1327b-125">この例については、「例 6」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1327b-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="1327b-126">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1327b-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="1327b-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="1327b-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="1327b-128">この規則がアクセス権を付与している Active Directory Domain Services (AD DS) のコンピューター グループまたはローカル グループの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="1327b-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="1327b-129">エイリアス</span><span class="sxs-lookup"><span data-stu-id="1327b-129">Aliases</span></span>                              | <span data-ttu-id="1327b-130">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-130">none</span></span>                                 |
| <span data-ttu-id="1327b-131">必須?</span><span class="sxs-lookup"><span data-stu-id="1327b-131">Required?</span></span>                            | <span data-ttu-id="1327b-132">true</span><span class="sxs-lookup"><span data-stu-id="1327b-132">true</span></span>                                 |
| <span data-ttu-id="1327b-133">位置は?</span><span class="sxs-lookup"><span data-stu-id="1327b-133">Position?</span></span>                            | <span data-ttu-id="1327b-134">名前付き</span><span class="sxs-lookup"><span data-stu-id="1327b-134">named</span></span>                                |
| <span data-ttu-id="1327b-135">既定値</span><span class="sxs-lookup"><span data-stu-id="1327b-135">Default Value</span></span>                        | <span data-ttu-id="1327b-136">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-136">none</span></span>                                 |
| <span data-ttu-id="1327b-137">パイプライン入力を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1327b-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1327b-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="1327b-139">ワイルドカード文字を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1327b-140">false</span><span class="sxs-lookup"><span data-stu-id="1327b-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="1327b-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="1327b-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="1327b-142">この規則がアクセス権を付与しているコンピューター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="1327b-142">Specifies the computer name to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="1327b-143">エイリアス</span><span class="sxs-lookup"><span data-stu-id="1327b-143">Aliases</span></span>                              | <span data-ttu-id="1327b-144">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-144">none</span></span>                                 |
| <span data-ttu-id="1327b-145">必須?</span><span class="sxs-lookup"><span data-stu-id="1327b-145">Required?</span></span>                            | <span data-ttu-id="1327b-146">true</span><span class="sxs-lookup"><span data-stu-id="1327b-146">true</span></span>                                 |
| <span data-ttu-id="1327b-147">位置は?</span><span class="sxs-lookup"><span data-stu-id="1327b-147">Position?</span></span>                            | <span data-ttu-id="1327b-148">名前付き</span><span class="sxs-lookup"><span data-stu-id="1327b-148">named</span></span>                                |
| <span data-ttu-id="1327b-149">既定値</span><span class="sxs-lookup"><span data-stu-id="1327b-149">Default Value</span></span>                        | <span data-ttu-id="1327b-150">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-150">none</span></span>                                 |
| <span data-ttu-id="1327b-151">パイプライン入力を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1327b-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1327b-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="1327b-153">ワイルドカード文字を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1327b-154">false</span><span class="sxs-lookup"><span data-stu-id="1327b-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="1327b-155">-ConfigurationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="1327b-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="1327b-156">この規則がアクセス権を付与している Windows PowerShell セッション構成 (実行空間とも呼ばれます) の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="1327b-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="1327b-157">エイリアス</span><span class="sxs-lookup"><span data-stu-id="1327b-157">Aliases</span></span>                              | <span data-ttu-id="1327b-158">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-158">none</span></span>                                 |
| <span data-ttu-id="1327b-159">必須?</span><span class="sxs-lookup"><span data-stu-id="1327b-159">Required?</span></span>                            | <span data-ttu-id="1327b-160">true</span><span class="sxs-lookup"><span data-stu-id="1327b-160">true</span></span>                                 |
| <span data-ttu-id="1327b-161">位置は?</span><span class="sxs-lookup"><span data-stu-id="1327b-161">Position?</span></span>                            | <span data-ttu-id="1327b-162">名前付き</span><span class="sxs-lookup"><span data-stu-id="1327b-162">named</span></span>                                |
| <span data-ttu-id="1327b-163">既定値</span><span class="sxs-lookup"><span data-stu-id="1327b-163">Default Value</span></span>                        | <span data-ttu-id="1327b-164">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-164">none</span></span>                                 |
| <span data-ttu-id="1327b-165">パイプライン入力を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1327b-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1327b-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="1327b-167">ワイルドカード文字を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1327b-168">false</span><span class="sxs-lookup"><span data-stu-id="1327b-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="1327b-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="1327b-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="1327b-170">Windows PowerShell Web Access 承認規則の変更に使用するユーザー アカウントの **PSCredential** オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="1327b-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="1327b-171">このパラメーターを追加しない場合、現在ログオンしているユーザー アカウントがコマンドレットにより使用されます。</span><span class="sxs-lookup"><span data-stu-id="1327b-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="1327b-172">承認規則をリモートから追加するために必要な **PSCredential** オブジェクトを取得するには、[Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="1327b-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="1327b-173">エイリアス</span><span class="sxs-lookup"><span data-stu-id="1327b-173">Aliases</span></span>                              | <span data-ttu-id="1327b-174">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-174">none</span></span>                                 |
| <span data-ttu-id="1327b-175">必須?</span><span class="sxs-lookup"><span data-stu-id="1327b-175">Required?</span></span>                            | <span data-ttu-id="1327b-176">false</span><span class="sxs-lookup"><span data-stu-id="1327b-176">false</span></span>                                |
| <span data-ttu-id="1327b-177">位置は?</span><span class="sxs-lookup"><span data-stu-id="1327b-177">Position?</span></span>                            | <span data-ttu-id="1327b-178">名前付き</span><span class="sxs-lookup"><span data-stu-id="1327b-178">named</span></span>                                |
| <span data-ttu-id="1327b-179">既定値</span><span class="sxs-lookup"><span data-stu-id="1327b-179">Default Value</span></span>                        | <span data-ttu-id="1327b-180">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-180">none</span></span>                                 |
| <span data-ttu-id="1327b-181">パイプライン入力を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1327b-182">false</span><span class="sxs-lookup"><span data-stu-id="1327b-182">false</span></span>                                |
| <span data-ttu-id="1327b-183">ワイルドカード文字を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1327b-184">false</span><span class="sxs-lookup"><span data-stu-id="1327b-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="1327b-185">-Force</span><span class="sxs-lookup"><span data-stu-id="1327b-185">-Force</span></span>

<span data-ttu-id="1327b-186">ユーザーに確認を求めずに、直ちにコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1327b-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="1327b-187">なお、単純な、または短いコンピューター名 (ドメイン名ではない名前、完全修飾されていない名前など) を入力した場合にも確認が求められます。</span><span class="sxs-lookup"><span data-stu-id="1327b-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="1327b-188">確認はセキュリティ上の理由で必要です。そのため、コンピューターがワークグループに参加している場合にのみ、コンピューターの追加に単純な名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1327b-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||  
|-|-|
| <span data-ttu-id="1327b-189">エイリアス</span><span class="sxs-lookup"><span data-stu-id="1327b-189">Aliases</span></span>                              | <span data-ttu-id="1327b-190">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-190">none</span></span>                                 |
| <span data-ttu-id="1327b-191">必須?</span><span class="sxs-lookup"><span data-stu-id="1327b-191">Required?</span></span>                            | <span data-ttu-id="1327b-192">false</span><span class="sxs-lookup"><span data-stu-id="1327b-192">false</span></span>                                |
| <span data-ttu-id="1327b-193">位置は?</span><span class="sxs-lookup"><span data-stu-id="1327b-193">Position?</span></span>                            | <span data-ttu-id="1327b-194">名前付き</span><span class="sxs-lookup"><span data-stu-id="1327b-194">named</span></span>                                |
| <span data-ttu-id="1327b-195">既定値</span><span class="sxs-lookup"><span data-stu-id="1327b-195">Default Value</span></span>                        | <span data-ttu-id="1327b-196">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-196">none</span></span>                                 |
| <span data-ttu-id="1327b-197">パイプライン入力を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1327b-198">false</span><span class="sxs-lookup"><span data-stu-id="1327b-198">false</span></span>                                |
| <span data-ttu-id="1327b-199">ワイルドカード文字を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1327b-200">false</span><span class="sxs-lookup"><span data-stu-id="1327b-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="1327b-201">-RuleName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="1327b-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="1327b-202">この規則のフレンドリ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="1327b-202">Specifies the friendly name for this rule.</span></span>

|||  
|-|-|
| <span data-ttu-id="1327b-203">エイリアス</span><span class="sxs-lookup"><span data-stu-id="1327b-203">Aliases</span></span>                              | <span data-ttu-id="1327b-204">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-204">none</span></span>                                 |
| <span data-ttu-id="1327b-205">必須?</span><span class="sxs-lookup"><span data-stu-id="1327b-205">Required?</span></span>                            | <span data-ttu-id="1327b-206">false</span><span class="sxs-lookup"><span data-stu-id="1327b-206">false</span></span>                                |
| <span data-ttu-id="1327b-207">位置は?</span><span class="sxs-lookup"><span data-stu-id="1327b-207">Position?</span></span>                            | <span data-ttu-id="1327b-208">名前付き</span><span class="sxs-lookup"><span data-stu-id="1327b-208">named</span></span>                                |
| <span data-ttu-id="1327b-209">既定値</span><span class="sxs-lookup"><span data-stu-id="1327b-209">Default Value</span></span>                        | <span data-ttu-id="1327b-210">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-210">none</span></span>                                 |
| <span data-ttu-id="1327b-211">パイプライン入力を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1327b-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1327b-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="1327b-213">ワイルドカード文字を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1327b-214">false</span><span class="sxs-lookup"><span data-stu-id="1327b-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="1327b-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="1327b-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="1327b-216">この規則がアクセス権を付与している AD DS またはローカル グループ内の 1 つまたは複数のユーザー グループ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="1327b-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="1327b-217">エイリアス</span><span class="sxs-lookup"><span data-stu-id="1327b-217">Aliases</span></span>                              | <span data-ttu-id="1327b-218">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-218">none</span></span>                                 |
| <span data-ttu-id="1327b-219">必須?</span><span class="sxs-lookup"><span data-stu-id="1327b-219">Required?</span></span>                            | <span data-ttu-id="1327b-220">true</span><span class="sxs-lookup"><span data-stu-id="1327b-220">true</span></span>                                 |
| <span data-ttu-id="1327b-221">位置は?</span><span class="sxs-lookup"><span data-stu-id="1327b-221">Position?</span></span>                            | <span data-ttu-id="1327b-222">名前付き</span><span class="sxs-lookup"><span data-stu-id="1327b-222">named</span></span>                                |
| <span data-ttu-id="1327b-223">既定値</span><span class="sxs-lookup"><span data-stu-id="1327b-223">Default Value</span></span>                        | <span data-ttu-id="1327b-224">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-224">none</span></span>                                 |
| <span data-ttu-id="1327b-225">パイプライン入力を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1327b-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1327b-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="1327b-227">ワイルドカード文字を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1327b-228">false</span><span class="sxs-lookup"><span data-stu-id="1327b-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="1327b-229">-UserName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="1327b-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="1327b-230">この規則がアクセス権を付与している 1 つまたは複数のコンピューター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="1327b-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="1327b-231">ユーザー名には、ゲートウェイ コンピューター上のローカル ユーザー アカウント、または AD DS のユーザーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1327b-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="1327b-232">形式は、`domain\user` または `computer\user` です。</span><span class="sxs-lookup"><span data-stu-id="1327b-232">The format is `domain\user` or `computer\user`.</span></span>

|||  
|-|-|
| <span data-ttu-id="1327b-233">エイリアス</span><span class="sxs-lookup"><span data-stu-id="1327b-233">Aliases</span></span>                              | <span data-ttu-id="1327b-234">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-234">none</span></span>                                 |
| <span data-ttu-id="1327b-235">必須?</span><span class="sxs-lookup"><span data-stu-id="1327b-235">Required?</span></span>                            | <span data-ttu-id="1327b-236">true</span><span class="sxs-lookup"><span data-stu-id="1327b-236">true</span></span>                                 |
| <span data-ttu-id="1327b-237">位置は?</span><span class="sxs-lookup"><span data-stu-id="1327b-237">Position?</span></span>                            | <span data-ttu-id="1327b-238">1 で保護されたプロセスとして起動されました</span><span class="sxs-lookup"><span data-stu-id="1327b-238">1</span></span>                                    |
| <span data-ttu-id="1327b-239">既定値</span><span class="sxs-lookup"><span data-stu-id="1327b-239">Default Value</span></span>                        | <span data-ttu-id="1327b-240">なし</span><span class="sxs-lookup"><span data-stu-id="1327b-240">none</span></span>                                 |
| <span data-ttu-id="1327b-241">パイプライン入力を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1327b-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1327b-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="1327b-243">ワイルドカード文字を許可する</span><span class="sxs-lookup"><span data-stu-id="1327b-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1327b-244">false</span><span class="sxs-lookup"><span data-stu-id="1327b-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="1327b-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="1327b-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="1327b-246">このコマンドレットは、-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer、および -OutVariable という共通パラメーターをサポートします。</span><span class="sxs-lookup"><span data-stu-id="1327b-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="1327b-247">詳細については、「[about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1327b-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="1327b-248">入力</span><span class="sxs-lookup"><span data-stu-id="1327b-248">INPUTS</span></span>

###  <a name="string"></a><span data-ttu-id="1327b-249">String</span><span class="sxs-lookup"><span data-stu-id="1327b-249">String</span></span>

<span data-ttu-id="1327b-250">このコマンドレットは、入力として文字列または文字列の配列を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="1327b-250">This cmdlet accepts a string or an array of strings as input.</span></span>

###  <a name="string"></a><span data-ttu-id="1327b-251">String\[\]</span><span class="sxs-lookup"><span data-stu-id="1327b-251">String\[\]</span></span>

<span data-ttu-id="1327b-252">このコマンドレットは、入力として文字列または文字列の配列を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="1327b-252">This cmdlet accepts a string or an array of strings as input.</span></span>

##  <a name="outputs"></a><span data-ttu-id="1327b-253">出力</span><span class="sxs-lookup"><span data-stu-id="1327b-253">Outputs</span></span>

###   <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="1327b-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1327b-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="1327b-255">このコマンドレットは、承認規則オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="1327b-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="1327b-256">例</span><span class="sxs-lookup"><span data-stu-id="1327b-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="1327b-257">例 1</span><span class="sxs-lookup"><span data-stu-id="1327b-257">EXAMPLE 1</span></span>

<span data-ttu-id="1327b-258">この例では、*srv2* 上の *SMAdmins* グループのユーザーについて、セッション構成に *PSWAEndpoint* (制限付き実行空間) のアクセス権を付与しています。</span><span class="sxs-lookup"><span data-stu-id="1327b-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="1327b-259">**注**: このコンピューター名は完全修飾ドメイン名 (FQDN) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1327b-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="1327b-260">管理者は制限付きセッション構成または実行空間を定義します。実行空間とは、エンド ユーザーが実行できるコマンドレットおよびタスクの制限された範囲です。</span><span class="sxs-lookup"><span data-stu-id="1327b-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="1327b-261">制限付き実行空間を定義すると、ユーザーは、許可されている Windows PowerShell® 実行空間内にない他のコンピューターにアクセスできなくなります。そのため、接続のセキュリティが強固になります。</span><span class="sxs-lookup"><span data-stu-id="1327b-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="1327b-262">セッション構成の詳細については、「[about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations)」または「[Windows PowerShell Web Access の展開](../install-and-use-windows-powershell-web-access.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1327b-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="1327b-263">例 2</span><span class="sxs-lookup"><span data-stu-id="1327b-263">EXAMPLE 2</span></span>

<span data-ttu-id="1327b-264">この例では、*srv2* 上のユーザーで、contoso\\user1、contoso\\user2、contoso\\user3 というユーザーについて、既定の Windows PowerShell セッション構成 `Microsoft.PowerShell` にアクセス権を付与します。</span><span class="sxs-lookup"><span data-stu-id="1327b-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="1327b-265">このコマンドレットは、3 つの規則を作成します (1 人 1 規則)。</span><span class="sxs-lookup"><span data-stu-id="1327b-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="1327b-266">例 3</span><span class="sxs-lookup"><span data-stu-id="1327b-266">EXAMPLE 3</span></span>

<span data-ttu-id="1327b-267">この例は、パイプラインを使用してユーザー名値を入力する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1327b-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="1327b-268">例 4</span><span class="sxs-lookup"><span data-stu-id="1327b-268">EXAMPLE 4</span></span>

<span data-ttu-id="1327b-269">この例は、プロパティ名を指定して、すべてのパラメーターがすべてのパイプラインの値を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1327b-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

\
###   <a name="section-subheading"></a><span data-ttu-id="1327b-270">{#section .subHeading}</span><span class="sxs-lookup"><span data-stu-id="1327b-270">{#section .subHeading}</span></span>

<div class="subSection">

<div id="code-snippet-5" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="1327b-271">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1327b-271">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="1327b-272">Copy</span><span class="sxs-lookup"><span data-stu-id="1327b-272">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f'); "Copy to clipboard.")

</div>

</div>

<div id="CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> $o = New-Object -TypeName PSObject | Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

</div>

</div>

</div>

</div>

</div>

###   <a name="section-1-subheading"></a><span data-ttu-id="1327b-273">{#section-1 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="1327b-273">{#section-1 .subHeading}</span></span>

<div class="subSection">

<div id="code-snippet-6" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="1327b-274">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1327b-274">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="1327b-275">Copy</span><span class="sxs-lookup"><span data-stu-id="1327b-275">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb'); "Copy to clipboard.")

</div>

</div>

<div id="CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> $o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell

</div>

</div>

</div>

</div>

</div>

</div>

### <a name="example-5-example-5-subheading"></a><span data-ttu-id="1327b-276">例 5 {#example-5 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="1327b-276">EXAMPLE 5 {#example-5 .subHeading}</span></span>

<div class="subSection">

<span data-ttu-id="1327b-277">この例は、*PswaServer\\ChrisLocal* というローカル ユーザーに、*srv1.contoso.com* というサーバーへのアクセス権を付与する規則を追加します。</span><span class="sxs-lookup"><span data-stu-id="1327b-277">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="1327b-278">この例は、ゲートウェイがワークグループ内にあり、対象コンピューターがドメイン内にあるシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="1327b-278">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="1327b-279">承認規則はゲートウェイ上のローカル ユーザーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="1327b-279">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="1327b-280">Windows PowerShell Web Access のサインイン ページで、正常に認証するには、ユーザーが **[オプションの接続設定]** 領域で、2 つ目の資格情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1327b-280">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="1327b-281">ゲートウェイ サーバーでは、複数セットの資格情報が使用され、*srv1.contoso.com* という対象コンピューターでユーザーの認証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1327b-281">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

\
<div id="code-snippet-7" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="1327b-282">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1327b-282">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="1327b-283">Copy</span><span class="sxs-lookup"><span data-stu-id="1327b-283">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3'); "Copy to clipboard.")

</div>

</div>

<div id="CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell

</div>

</div>

</div>

</div>

</div>

### <a name="example-6-example-6-subheading"></a><span data-ttu-id="1327b-284">例 6 {#example-6 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="1327b-284">EXAMPLE 6 {#example-6 .subHeading}</span></span>

<div class="subSection">

<span data-ttu-id="1327b-285">この例では、すべてのコンピューターですべてのエンドポイントに対するアクセス権をすべてのユーザーに許可します。</span><span class="sxs-lookup"><span data-stu-id="1327b-285">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="1327b-286">これで、基本的に承認規則がオフになります。</span><span class="sxs-lookup"><span data-stu-id="1327b-286">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="1327b-287">**注**: `*` ワイルド カード文字の使用は、セキュリティが重要な展開には推奨されません。また、テスト環境のみで使用するか、セキュリティを緩和できる展開でのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="1327b-287">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

\
<div id="code-snippet-8" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="1327b-288">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1327b-288">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="1327b-289">Copy</span><span class="sxs-lookup"><span data-stu-id="1327b-289">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076'); "Copy to clipboard.")

</div>

</div>

<div id="CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *

</div>

</div>

</div>

</div>

</div>

</div>

<a name="related-topics"></a><span data-ttu-id="1327b-290">関連トピック</span><span class="sxs-lookup"><span data-stu-id="1327b-290">Related topics</span></span> 
--------------


<span data-ttu-id="1327b-291">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="1327b-291">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="1327b-292">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="1327b-292">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="1327b-293">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="1327b-293">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="1327b-294">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="1327b-294">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="1327b-295">[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)\\</span><span class="sxs-lookup"><span data-stu-id="1327b-295">[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)\\</span></span>
\
<span data-ttu-id="1327b-296">[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)\\</span><span class="sxs-lookup"><span data-stu-id="1327b-296">[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)\\</span></span>
\
[<span data-ttu-id="1327b-297">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="1327b-297">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)