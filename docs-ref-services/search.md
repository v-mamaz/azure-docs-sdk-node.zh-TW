---
title: "適用於 Node.js 的 Azure 搜尋服務模組"
description: "適用於 Node.js 的 Azure 搜尋服務模組參考"
keywords: "Azure,SDK,API,搜尋, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: dc9d4c5128c99a9518bd059e191bb11e4de4b78f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-search-modules-for-nodejs"></a>適用於 Node.js 的 Azure 搜尋服務模組

## <a name="overview"></a>概觀

Azure 搜尋服務是一項雲端搜尋即服務解決方案，可將伺服器和基礎結構管理委託給 Microsoft，讓您利用立即可用的服務來填入搜尋資料，然後用來在您的應用程式中新增搜尋。

深入了解 [Azure 搜尋服務](https://docs.microsoft.com/azure/search/search-what-is-azure-search)。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure 搜尋服務 npm 模組

```bash
npm install azure-arm-search
```

### <a name="example"></a>範例

此範例會在 Azure 中建立新的搜尋服務，並列出其資源群組中的資源。

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。