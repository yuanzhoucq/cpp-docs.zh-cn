---
title: 注册表项 (ATL) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac8e202fc2fc3d58e2d57a9fbfa15264d9fd310e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359724"
---
# <a name="registry-entries"></a>注册表项
DCOM 引入了应用程序 Id (Appid) 分组到一个集中的位置，注册表中的一个或多个 DCOM 对象配置选项的概念。 通过它在名为该对象的 CLSID 下值 AppID 的值，该值指示指定一个 AppID。  
  
 默认情况下，ATL 生成的服务使用其 CLSID 为其 AppID 的 guid。 下`HKEY_CLASSES_ROOT\AppID`，你可以指定 DCOM 特定项目。 最初，存在两个条目：  
  
-   `LocalService`与该服务的名称相同的值。 如果此值存在，则使用它而不是`LocalServer32`CLSID 下的键。  
  
-   `ServiceParameters`使用的值等于`-Service`。 此值指定它启动时传递给服务的参数。 请注意，这些参数传递给服务的`ServiceMain`函数，不`WinMain`。  
  
 任何 DCOM 服务还需要创建另一个项下的`HKEY_CLASSES_ROOT\AppID`。 此密钥等于该 exe 文件的名称，并充当交叉引用，因为它包含指回 AppID 条目的 AppID 值。  
  
## <a name="see-also"></a>请参阅  
 [服务](../atl/atl-services.md)

