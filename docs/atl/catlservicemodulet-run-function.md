---
title: 'Catlservicemodulet:: Run 函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
dev_langs:
- C++
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e509ad88a744f6ebaaca41ecd0d6455d68c2585c
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850649"
---
# <a name="catlservicemoduletrun-function"></a>Catlservicemodulet:: Run 函数
`Run` 包含对调用`PreMessageLoop`， `RunMessageLoop`，和`PostMessageLoop`。 被调用后`PreMessageLoop`首先将存储服务的线程 id。 该服务将使用此 ID 由发送 WM_QUIT 消息使用 Win32 API 函数来关闭自己[PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946)。  
  
 `PreMessageLoop` 然后，调用`InitializeSecurity`。 默认情况下`InitializeSecurity`调用[CoInitializeSecurity](http://msdn.microsoft.com/library/windows/desktop/ms693736)与设置为 NULL 的安全描述符，这意味着任何用户有权访问您的对象。  
  
 如果不想要指定其自身的安全的服务，重写`PreMessageLoop`，并且不调用`InitializeSecurity`，COM 然后将确定注册表中的安全设置。 配置注册表设置的简便方法是使用[DCOMCNFG](../atl/dcomcnfg.md)稍后在本部分中讨论的实用程序。  
  
 一旦指定安全，以便新客户端可以连接到该程序是向 COM 注册对象。 最后，程序告知服务控制管理器 (SCM)，它正在运行，并且该程序将进入一个消息循环。 该程序保持运行，直到它在服务关闭时退出的消息。  
  
## <a name="see-also"></a>请参阅  
 [服务](../atl/atl-services.md)   
 [CSecurityDesc 类](../atl/reference/csecuritydesc-class.md)   
 [CSid 类](../atl/reference/csid-class.md)   
 [CDacl 类](../atl/reference/cdacl-class.md)   
 [Catlservicemodulet:: Run](../atl/reference/catlservicemodulet-class.md#run)

