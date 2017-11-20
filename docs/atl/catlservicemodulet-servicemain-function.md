---
title: "CAtlServiceModuleT::ServiceMain 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ServiceMain
- CServiceModule::ServiceMain
- CServiceModule.ServiceMain
dev_langs: C++
helpviewer_keywords: ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6abb297f6873c654cf359a63638338f288f45613
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT::ServiceMain 函数
服务控制管理器 (SCM) 调用`ServiceMain`当打开服务控制面板应用程序，请选择该服务，然后单击**启动**。  
  
 SCM 后调用`ServiceMain`，服务必须为 SCM 指定处理程序函数。 此函数可获取服务的状态并传递特定的指令 （如暂停或停止） 的 SCM。 SCM 获取此函数在该服务传递时**_Handler** Win32 API 函数时，到[RegisterServiceCtrlHandler](http://msdn.microsoft.com/library/windows/desktop/ms685054)。 (**_Handler**是调用非静态成员函数的静态成员函数[处理程序](../atl/reference/catlservicemodulet-class.md#handler)。)  
  
 在启动时，服务还应通知的 SCM 其当前状态。 这是通过传递**SERVICE_START_PENDING** Win32 API 函数时，到[SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241)。  
  
 `ServiceMain`然后调用`CAtlExeModuleT::InitializeCom`，从而调用 Win32 API 函数[CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)。 默认情况下，`InitializeCom`传递**COINIT_MULTITHREADED**函数的标志。 此标志指示该程序将是自由线程的服务器。  
  
 现在，`CAtlServiceModuleT::Run`调用以执行服务的主要工作。 **运行**继续执行，直到该服务已停止。  
  
## <a name="see-also"></a>另请参阅  
 [服务](../atl/atl-services.md)   
 [CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)

