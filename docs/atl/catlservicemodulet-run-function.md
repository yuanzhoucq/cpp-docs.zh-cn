---
title: 'CAtlServiceModuleT:: Run 函数'
ms.date: 11/04/2016
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: 0c35020996852731a8f22c15860d4cceb7a8bdb6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491523"
---
# <a name="catlservicemoduletrun-function"></a>CAtlServiceModuleT:: Run 函数

`Run`包含对`PreMessageLoop`、 `RunMessageLoop`和`PostMessageLoop`的调用。 调用后, `PreMessageLoop`先存储服务的线程 ID。 服务将使用此 ID 通过使用 Win32 API 函数[PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)发送 WM_QUIT 消息来关闭自身。

`PreMessageLoop`然后调用`InitializeSecurity`。 默认情况下`InitializeSecurity` , 调用[CoInitializeSecurity](/windows/win32/api/combaseapi/nf-combaseapi-coinitializesecurity)并将安全描述符设置为 NULL, 这意味着任何用户都有权访问您的对象。

如果你不希望服务指定其自身的安全性, 请重写`PreMessageLoop`并不要调用`InitializeSecurity`, 然后, COM 将从注册表中确定安全设置。 配置注册表设置的一种简便方法是使用本部分后面讨论的[dcomcnfg.exe](../atl/dcomcnfg.md)实用程序。

指定安全性后, 会向 COM 注册对象, 以便新客户端可以连接到该程序。 最后, 该程序会告诉服务控制管理器 (SCM) 它正在运行, 并且程序将进入一个消息循环。 在服务关闭后, 程序将一直保持运行状态, 直到它发布 quit 消息。

## <a name="see-also"></a>请参阅

[服务](../atl/atl-services.md)<br/>
[CSecurityDesc 类](../atl/reference/csecuritydesc-class.md)<br/>
[CSid 类](../atl/reference/csid-class.md)<br/>
[CDacl 类](../atl/reference/cdacl-class.md)<br/>
[CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)
