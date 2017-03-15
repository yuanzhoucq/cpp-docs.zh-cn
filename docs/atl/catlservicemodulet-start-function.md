---
title: "CAtlServiceModuleT::Start Function | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CServiceModule.Start"
  - "CServiceModule::Start"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Start 方法"
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# CAtlServiceModuleT::Start Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在服务控制时，**\_tWinMain** 调用 **CAtlServiceModuleT::WinMain**，然后调用 `CAtlServiceModuleT::Start`。  
  
 `CAtlServiceModuleT::Start` 设置数组映射每个服务将其启动功能的 **SERVICE\_TABLE\_ENTRY** 结构。  此数组随后传递给Win32 API函数，[StartServiceCtrlDispatcher](http://msdn.microsoft.com/library/windows/desktop/ms686324)。  理论上，一EXE可以处理多项服务，并且该数组可以具有多个 **SERVICE\_TABLE\_ENTRY** 结构。  目前，但是，ATL生成的服务只支持EXE每一服务。  因此，该数组包含服务名和 **\_ServiceMain** 作为启动功能的条目。  **\_ServiceMain** 是调用非静态成员函数 `CAtlServiceModuleT`，`ServiceMain`的静态成员函数。  
  
> [!NOTE]
>  **StartServiceCtrlDispatcher** 的未连接到服务控制管理器\(SCM\)可能意味着程序不作为服务运行。  这种情况下，过程直接调用 `CAtlServiceModuleT::Run`，以便程序可以运行作为本地服务器。  有关运行程序的更多信息作为本地服务器，请参见 [调试提示](../atl/debugging-tips.md)。  
  
## 请参阅  
 [服务](../atl/atl-services.md)   
 [CAtlServiceModuleT::Start](../Topic/CAtlServiceModuleT::Start.md)