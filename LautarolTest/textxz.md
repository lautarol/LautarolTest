---
title: Create and deploy a Windows Defender Application Guard policy
titleSuffix: Configuration Manager
description: Create and deploy Windows Defender Application Guard policy.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 33a6c1d9-4dd8-411c-a748-693a5bd2ea5a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
---


## <a name="create-azure-storage-account"></a>Azure ストレージ アカウントを作成する

1. Azure portal で、[+ リソースの作成] を選択し、[Marketplace の検索] ボックスに「ストレージ アカウント」と入力して、その結果から [ストレージ アカウント - Blob、File、Table、Queue] を選択し、[作成] を選択します。

![ストレージ アカウントの追加オプションが強調表示されている Azure portal のスクリーン ショット](../media/add-resource.png)

1. [ストレージ アカウントの作成] ブレードで、次のように入力します。

   - [サブスクリプション\]: このモジュールで使用しているサブスクリプションを選択します。
   - _[リソース グループ]_: モジュール リソース グループを選びます。
   - _[ストレージ アカウント名]_: 一意の名前を入力します (緑のチェックボックスが表示されます)。
   - _[場所]_: このモジュールでリソースとして使用する場所を選択します。
   - _[パフォーマンス]_: [Standard] を選択します。
   - _[アカウントの種類]_: [ストレージ (汎用 v1)] を選択します。
   - _[レプリケーション]_: [ローカル冗長ストレージ (LRS)] を選択します。

![[ストレージ アカウントの作成] 画面のスクリーンショット](../media/create-storage-account.png)

1. [次へ: **詳細 >]** を選択します。
1. [詳細] タブで、次のように選択します。

    - _[安全な転送が必須]_: [無効] を選択します。
    - _[仮想ネットワーク]_: [なし] を選択します。

![[ストレージ アカウントの作成] の [詳細] タブのスクリーンショット](../media/create-storage-account-advanced.png)

1. **[確認および作成]** を選択します。
1. 確認のタブで、**[作成]** を選択します。

## <a name="acquire-account-name-and-key"></a>アカウントの名前とキーを取得する

1. プロビジョニングされたら、そのストレージ アカウントに移動します。
1. 左側のメニューから **[アクセス キー]** を選択し、後で使用するときのために、ストレージ アカウントの名前と key1 のキー値をメモ帳などのテキスト エディターにコピーします。

![ストレージ アカウントの [アクセス キー] ページのスクリーンショット](../media/access-keys.png)

## <a name="create-the-dwtemp-container"></a>dwtemp コンテナーを作成する

1. 左側のメニューから [BLOB] を選択し、**[+ コンテナー]** を選択して新しいコンテナーを作成します。
1. コンテナー名として「_dwtemp_」を入力します。
1. パブリック アクセス レベルは、_[プライベート]_ を選択したままにします。
1. **[OK]** を選択します。

![コンテナーの追加ページのスクリーン ショット](../media/add-container.png)

## <a name="create-azure-data-factory"></a>Azure データ ファクトリを作成する

1. [Azure portal](https://portal.azure.com) に移動します。
1. **[+ リソースの作成]** を選択し、検索バーに「データ ファクトリ」と入力して、その結果から [データ ファクトリ] を選び、**[作成]** を選択します。

![新しい Azure データ ファクトリを追加するオプションが強調表示された Azure portal のスクリーンショット](../media/add-resource-data-factory.png)

1. データ ファクトリの作成フォームでは、次の構成を設定します。

    - _[名前]_: グローバルに一意な名前を入力します (緑のチェックマークが表示されます)。
    - _[サブスクリプション]_: このワークショップで使用しているサブスクリプションを選択します。
    - _[リソース グループ]_: [既存のものを選択] を選び、このワークショップで使用しているリソース グループを選択します。
    - _[バージョン]_: V2
    - _[場所]_: リージョンを選択します。

![[新しいデータ ファクトリ] ページのスクリーンショット](../media/add-new-data-factory.png)

1. **[作成]** を選択して ADF v2 をプロビジョニングします。
