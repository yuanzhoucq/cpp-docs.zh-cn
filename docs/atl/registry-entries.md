---
title: "注册表项 (ATL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: faef0ca0c1c9c4c2986a039b8b1a26517641acd0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="registry-entries"></a>注册表项
DCOM 引入了应用程序 Id (Appid) 分组到一个集中的位置，注册表中的一个或多个 DCOM 对象配置选项的概念。 通过它在名为该对象的 CLSID 下值 AppID 的值，该值指示指定一个 AppID。  
  
 默认情况下，ATL 生成的服务使用其 CLSID 为其 AppID 的 guid。 下`HKEY_CLASSES_ROOT\AppID`，你可以指定 DCOM 特定项目。 最初，存在两个条目：  
  
-   `LocalService`与该服务的名称相同的值。 如果此值存在，则使用它而不是`LocalServer32`CLSID 下的键。  
  
-   `ServiceParameters`使用的值等于`-Service`。 此值指定它启动时传递给服务的参数。 请注意，这些参数传递给服务的`ServiceMain`函数，不`WinMain`。  
  
 任何 DCOM 服务还需要创建另一个项下的`HKEY_CLASSES_ROOT\AppID`。 此密钥等于该 exe 文件的名称，并充当交叉引用，因为它包含指回 AppID 条目的 AppID 值。  
  
## <a name="see-also"></a>请参阅  
 [服务](../atl/atl-services.md)

