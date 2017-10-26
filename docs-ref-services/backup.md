---
title: "適用於 Node.js 的 Azure 備份模組"
description: "適用於 Node.js 的 Azure 備份模組參考"
keywords: "Azure,SDK,API,備份, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 3ff9bff16a520bca461198531fd4c02139d2b293
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-backup-modules-for-nodejs"></a>適用於 Node.js 的 Azure 備份模組

## <a name="overview"></a>概觀

Azure 備份是您可用來備份 (或保護) 和還原 Microsoft Cloud 資料的 Azure 服務。 Azure 備份將以一個可靠、安全及具成本競爭力的雲端架構解決方案，取代您現有的內部部署或異地備份解決方案。 Azure 備份提供多個元件，您可以下載並部署在適當的電腦、伺服器或雲端中。 您部署的元件或代理程式，取決於您想要保護的項目。 所有 Azure 備份的元件 (無論您要保護的是內部部署或雲端資料) 都可以將資料備份至 Azure 中的復原服務保存庫。 

## <a name="management-package"></a>管理套件

### <a name="install-the-modules-with-npm"></a>使用 npm 安裝模組

使用 npm 來安裝適用於 Node.js 的 Azure 備份模組

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a>範例

此範例會列出指定之保存庫與資源群組的復原作業。

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。