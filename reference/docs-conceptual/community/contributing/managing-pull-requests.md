---
title: プル要求を管理する方法
description: この記事では、PowerShell-Docs チームがプル要求を管理する方法について説明します。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b9b37816dfdf38e4d8b7c2d66799164d0e97d257
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060387"
---
# <a name="managing-pull-requests"></a>プル要求の管理

この記事では、PowerShell-Docs リポジトリでプル要求を管理する方法について説明します。 この記事は、PowerShell-Docs チームのメンバーの作業を支援することを目的としています。 一般の共同作成者に対してプロセスを透明化するために、ここで公開されています。

## <a name="best-practices"></a>ベスト プラクティス

- PR を送信するユーザーは、ピア レビューなしで PR をマージすることはできません。
- PR の送信時にピア レビュー担当者を割り当てます。 早期の割り当てにより、レビュー担当者はコメントを付けて速やかに対応できるようになります。
- コメントを使用して、変更の性質や依頼するレビューの種類を説明します。 レビュー担当者を必ず @mention してください。 たとえば、変更が軽微であり、完全な技術レビューを必要としない場合は、それをコメントで説明します。

## <a name="pr-process-steps"></a>PR プロセスの手順

1. 作成者: PR を作成する
   - PR で解決するイシューをリンクする
   - GitHub の[自動クローズ](https://help.github.com/en/articles/closing-issues-using-keywords)機能を使用してイシューを閉じる
1. 作成者: ピア レビュー担当者を割り当てる
1. レビュー担当者: 校正を行い、(必要に応じて) コメントを付ける
1. 作成者: レビューのフィードバックを組み込む
1. 両方: プレビュー表示を確認する
1. 両方: 検証レポートを確認する - 警告とエラーを修正
1. 作成者: サインオフ コメント (Acrolinx 情報を含む) を追加する
1. レビュー担当者: レビューを "承認済み" としてマークする
1. リポジトリ管理者: PR をマージする (条件については下記を参照)

## <a name="content-reviewer-checklist"></a>コンテンツ レビュー担当者チェックリスト

より包括的なリストについては、[編集チェックリスト](editorial-checklist.md)を参照してください。

- 文法、スタイル、簡潔さ、技術的正確さをチェックする
- 各例がターゲット バージョンに対応していることを確認する
- プレビュー表示を確認する
- メタデータを確認する - ms.date、ms.assetid の削除、必須フィールドの確認
- マークダウンの正確さを検証する
  - 特定のコンテンツの書式設定について、スタイル ガイドを参照する
- 次のように例を再構成する
  - 序文
  - コードと出力
  - コードの詳細な説明 (必要な場合)
- ハイパーリンクの正確性を確認する
  - TechNet/MSDN リンクを置換または削除する
  - ターゲットへのリダイレクトの最小数を確保する
  - HTTPS を確認する
  - リンクの種類を修正する
    - ローカル ファイルのファイル リンク
    - ドキュメント セットの外部のファイルの URL リンク
  - URL からロケールを削除する
  - `docs.microsoft.com` を参照する URL を簡略化する

## <a name="branch-merge-process"></a>ブランチ マージ プロセス

staging ブランチは、live にマージされる唯一のブランチです。 有効期間が短い (作業) ブランチからのマージはスカッシュする必要があります。

| *マージ元/マージ先*  | *release ブランチ* | *staging*        | *live*      |
| ---------------- |:----------------:|:----------------:|:-----------:|
| *作業ブランチ* | スカッシュしてマージ | スカッシュしてマージ | 禁止 |
| *release ブランチ* | &mdash;          | merge            | 禁止 |
| *staging*        | リベース           | &mdash;          | merge       |

### <a name="pr-merger-checklist"></a>PR マージ担当者チェックリスト

- コンテンツのレビューが完了している
- その変更の正しいターゲット ブランチである
- マージの競合がない
- 検証とビルド ステップがすべて成功している
  - 警告と推奨事項が修正されている (例外については、「[Notes](#notes)」を参照)
  - 壊れたリンクがない
- テーブルに従ってマージする

### <a name="notes"></a>Notes

次の警告は無視してかまいません。

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

PR がマージされると、ターゲット ブランチの HEAD が変更されます。 以前の HEAD に基づいたオープン PR は古くなっています。 古い PR は、GitHub でマージの警告をオーバーライドする管理者権限を使用してマージできます。 以前にマージされた PR で同じファイルを操作していない場合は、これを安全に実行できます。 ただし、 **[Update Branch]** ボタンをクリックするのが最も安全な方法です。 修正する必要がある未解決の競合が存在する可能性があります。

## <a name="publishing-to-live"></a>ライブへの公開

`staging` ブランチに蓄積された変更をライブ Web サイトに定期的に公開する必要があります。 そのためには、`staging` ブランチを `live` ブランチにマージする必要があります。

- 少なくとも週に 1 回は、`staging` ブランチを `live` ブランチにマージします。
- 重要な変更の後、`staging` ブランチを `live` にマージします。
  - 50 個以上のファイルを変更したとき
  - release ブランチをマージした後
  - リポジトリまたはドキュメント セットの構成 (docfx.json、OPS 構成、ビルド スクリプトなど) を変更したとき
  - リダイレクト ファイルを変更したとき
  - TOC を変更したとき
  - "プロジェクト" ブランチをマージした後 (コンテンツの再構成、一括更新など)