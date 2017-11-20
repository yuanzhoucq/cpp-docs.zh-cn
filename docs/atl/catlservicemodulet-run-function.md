---
title: "CAtlServiceModuleT::Run 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
dev_langs: C++
helpviewer_keywords: ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 383b054314982a0828d51083a904ccb2f7ddb5d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="catlservicemoduletrun-function"></a>CAtlServiceModuleT::Run 函数
**运行**包含对的调用`PreMessageLoop`， `RunMessageLoop`，和`PostMessageLoop`。 后调用，`PreMessageLoop`首先将存储服务的线程 id。 服务将使用此 ID 来关闭它自己通过发送**WM_QUIT**消息使用 Win32 API 函数， [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946)。  
  
 `PreMessageLoop`然后调用`InitializeSecurity`。 默认情况下，`InitializeSecurity`调用[CoInitializeSecurity](http://msdn.microsoft.com/library/windows/desktop/ms693736)以及设置为 NULL 的安全描述符，这意味着任何用户有权访问你的对象。  
  
 如果你不想要指定自己的安全性的服务，重写`PreMessageLoop`和不调用`InitializeSecurity`，COM 然后确定从注册表的安全设置。 配置注册表设置一种简便方式是使用[DCOMCNFG](../atl/dcomcnfg.md)此部分中讨论更高版本的实用工具。  
  
 后指定安全，以便新客户端可以连接到该程序是向 COM 注册对象。 最后，程序将告知服务控制管理器 (SCM)，它正在运行，并且程序将进入具有消息循环。 程序保持运行，直到它在服务关闭时将退出的消息发送。  
  
## <a name="see-also"></a>另请参阅  
 [服务](../atl/atl-services.md)   
 [CSecurityDesc 类](../atl/reference/csecuritydesc-class.md)   
 [CSid 类](../atl/reference/csid-class.md)   
 [CDacl 类](../atl/reference/cdacl-class.md)   
 [CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)

