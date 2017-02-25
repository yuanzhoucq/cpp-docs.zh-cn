---
title: "Running the Program as a Local Server | Microsoft Docs"
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
  - "ATL 服务, running as local servers"
  - "调试 [ATL], running services as local server"
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Running the Program as a Local Server
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果运行程序作为服务不是很方便，可以临时更改注册表，以便程序运行当作普通的本地服务器。  对 `LocalService` 值重命名在您的AppID下为 `_LocalService` 并确保在您的CLSID下的 `LocalServer32` 键正确地设置。  （重命名使用DCOMCNFG指定的说明在您的 `LocalServer32` 键的 `_LocalServer32`。\)中不同计算机上应运行应用程序运行您的程序作为本地服务器需要一些在启动的更多秒，因为对 **StartServiceCtrlDispatcher** 的调用 `CAtlServiceModuleT::Start` 需要几秒钟，以便在失败以前。  
  
## 请参阅  
 [Debugging Tips](../atl/debugging-tips.md)