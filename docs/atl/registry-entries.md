---
title: "Registry Entries | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "注册表, application IDs"
  - "注册表, ATL services entries"
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Registry Entries
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DCOM引入应用程序ID \(AppIDs\)的概念，组一个或多个DCOM对象的配置选项到注册表中的中心位置中。  通过指示其值指定AppID在AppID名为值在对象的CLSID下。  
  
 默认情况下，一ATL生成的服务使用其CLSID为GUID。其AppID。  在 `HKEY_CLASSES_ROOT\AppID`下，可以指定DCOM特定项。  最初，两项存在:  
  
-   `LocalService`，即值等于服务的名称。  如果此值存在，则使用而不是在CLSID下的 `LocalServer32` 键。  
  
-   `ServiceParameters`，即值等于 `–Service`。  此值指定要传递给服务的参数，在启动时。  注意这些参数传递给服务的 `ServiceMain` 函数，而不是 `WinMain`。  
  
 所有DCOM服务还需要创建另一个项。`HKEY_CLASSES_ROOT\AppID`下。  因为它包含指回AppID项，将会AppID值此键与EXE的名称相等并且作为交叉引用。  
  
## 请参阅  
 [服务](../atl/atl-services.md)