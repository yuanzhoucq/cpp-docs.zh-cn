---
title: "CAtlServiceModuleT::ServiceMain Function | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ServiceMain"
  - "CServiceModule::ServiceMain"
  - "CServiceModule.ServiceMain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ServiceMain method"
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlServiceModuleT::ServiceMain Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当您打开服务控制面板应用程序，选择服务，然后单击 **启动**时，该服务控制管理器\(SCM\)调用 `ServiceMain`。  
  
 在SCM调用 `ServiceMain`后，服务必须为SCM处理程序函数。  此功能允许SCM获取服务的状态和传递特定命令\(例如暂停或停止）。  SCM获取此功能，当服务通过 **\_Handler** 对Win32 API函数时，[RegisterServiceCtrlHandler](http://msdn.microsoft.com/library/windows/desktop/ms685054)。  （**\_Handler** 是调用非静态成员函数 [处理程序](../atl/catlservicemodulet-handler-function.md)。\)的静态成员函数  
  
 在启动服务，还应通知SCM其当前状态。  它通过将 **SERVICE\_START\_PENDING** 这样做Win32 API函数，[SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241)。  
  
 `ServiceMain` 然后调用 `CAtlExeModuleT::InitializeCom`，调用Win32 API函数 [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)。  默认情况下，`InitializeCom` 通过 **COINIT\_MULTITHREADED** 标志传递给函数。  此标志指示程序是一个自由线程服务器。  
  
 现在，`CAtlServiceModuleT::Run` 调用服务执行的主要任务。  **Run** 继续执行，直到服务停止。  
  
## 请参阅  
 [服务](../atl/atl-services.md)   
 [CAtlServiceModuleT::ServiceMain](../Topic/CAtlServiceModuleT::ServiceMain.md)