---
title: "適用於 Node.js 的 Azure Site Recovery 模組"
description: "適用於 Node.js 的 Azure Site Recovery 模組參考"
keywords: Azure,SDK,API,Site Recovery, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 3537503118a6fbe181c8cc4b26da545a4bdbd764
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-site-recovery-modules-for-nodejs"></a>適用於 Node.js 的 Azure Site Recovery 模組

## <a name="overview"></a>概觀

Site Recovery 可讓您自動執行區域、內部部署虛擬機器和實體伺服器之間至 Azure 的 Azure VM 複寫，以及自動執行內部部署機器至次要資料中心的複寫。

深入了解 [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure Site Recovery 服務 npm 模組

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a>範例

此範例會列出資源群組的 Site Recovery 服務。

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。