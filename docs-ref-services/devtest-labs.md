---
title: "適用於 Node.js 的 Azure DevTest Labs 模組"
description: "適用於 Node.js 的 Azure DevTest Labs 模組參考"
keywords: Azure,SDK,API,DevTest Labs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 933ce8971e02c2898d296112282169b8c7dca1c7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a>適用於 Node.js 的 Azure DevTest Labs 模組

## <a name="overview"></a>概觀

Azure DevTest Labs 是一項服務，可協助開發人員和測試人員在 Azure 中建立快速環境，同時將浪費降至最低並控制成本。 您可以利用可重複使用的範本和構件快速佈建 Windows 和 Linux 環境，來測試最新版的應用程式。 將您的部署管線與研發/測試實驗室輕鬆整合，來佈建隨選環境。 藉由佈建多個測試代理程式來相應增加您的負載測試，並建立預先佈建的環境來進行訓練和示範。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure DevTest Labs npm 模組

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a>範例

此範例會取得並列印實驗室的詳細資料。

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。