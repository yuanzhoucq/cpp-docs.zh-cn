---
title: 'Catlservicemodulet:: Run 函数'
ms.date: 11/04/2016
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: 91b6465dd975a1e3227d1416f2b78a8abbd441ad
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694317"
---
# <a name="catlservicemoduletrun-function"></a>Catlservicemodulet:: Run 函数

`Run` 包含对调用`PreMessageLoop`， `RunMessageLoop`，和`PostMessageLoop`。 被调用后`PreMessageLoop`首先将存储服务的线程 id。 该服务将使用此 ID 由发送 WM_QUIT 消息使用 Win32 API 函数来关闭自己[PostThreadMessage](/windows/desktop/api/winuser/nf-winuser-postthreadmessagea)。

`PreMessageLoop` 然后，调用`InitializeSecurity`。 默认情况下`InitializeSecurity`调用[CoInitializeSecurity](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializesecurity)与设置为 NULL 的安全描述符，这意味着任何用户有权访问您的对象。

如果不想要指定其自身的安全的服务，重写`PreMessageLoop`，并且不调用`InitializeSecurity`，COM 然后将确定注册表中的安全设置。 配置注册表设置的简便方法是使用[DCOMCNFG](../atl/dcomcnfg.md)稍后在本部分中讨论的实用程序。

一旦指定安全，以便新客户端可以连接到该程序是向 COM 注册对象。 最后，程序告知服务控制管理器 (SCM)，它正在运行，并且该程序将进入一个消息循环。 该程序保持运行，直到它在服务关闭时退出的消息。

## <a name="see-also"></a>请参阅

[服务](../atl/atl-services.md)<br/>
[CSecurityDesc 类](../atl/reference/csecuritydesc-class.md)<br/>
[CSid 类](../atl/reference/csid-class.md)<br/>
[CDacl 类](../atl/reference/cdacl-class.md)<br/>
[Catlservicemodulet:: Run](../atl/reference/catlservicemodulet-class.md#run)

