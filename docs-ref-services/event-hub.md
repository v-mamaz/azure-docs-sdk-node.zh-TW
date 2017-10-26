---
title: "適用於 Node.js 的 Azure 事件中樞模組"
description: "適用於 Node.js 的 Azure 事件中樞模組參考"
keywords: Azure,SDK,API,Event Hub, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: 5ac6fc3f86419602756c354393078b399a6cba23
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-event-hub-modules-for-nodejs"></a>適用於 Node.js 的 Azure 事件中樞模組

## <a name="overview"></a>概觀
Azure 事件中樞是可高度調整的資料串流平台，以及每秒能夠接收和處理數百萬個事件的事件內嵌服務。 事件中樞可以處理及儲存分散式軟體和裝置所產生的事件、資料或遙測。 傳送至事件中樞的資料可以透過任何即時分析提供者或批次/儲存體配接器來轉換和儲存。 藉由提供大規模的低延遲發佈訂閱功能，事件中樞能成為引進巨量資料的途徑。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組 

使用 npm 來安裝適用於 Node.js 的 Azure 事件中樞模組

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a>範例

此範例會擷取現有事件中樞的相關資訊。

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。