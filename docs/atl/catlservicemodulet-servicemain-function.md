---
title: 'Catlservicemodulet:: Servicemain 函数'
ms.date: 11/04/2016
f1_keywords:
- ServiceMain
- CServiceModule::ServiceMain
- CServiceModule.ServiceMain
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: 3aad67d58ccd4d1d35572542d899c17e0f42902b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471209"
---
# <a name="catlservicemoduletservicemain-function"></a>Catlservicemodulet:: Servicemain 函数

服务控制管理器 (SCM) 调用`ServiceMain`时打开服务控制面板应用程序，请选择该服务，然后单击**启动**。

SCM 后，将调用`ServiceMain`，服务必须为 SCM 提供处理程序函数。 此函数允许 SCM 获得服务的状态并传递 （例如暂停或停止） 的具体说明。 SCM 获取此函数在该服务通过`_Handler`Win32 API 函数[RegisterServiceCtrlHandler](/windows/desktop/api/winsvc/nf-winsvc-registerservicectrlhandlera)。 (`_Handler`是调用非静态成员函数的静态成员函数[处理程序](../atl/reference/catlservicemodulet-class.md#handler)。)

在启动时，服务还应该通知 SCM 及其当前状态。 这是通过传递给 Win32 API 函数 SERVICE_START_PENDING [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)。

`ServiceMain` 然后调用`CAtlExeModuleT::InitializeCom`，它调用 Win32 API 函数[CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex)。 默认情况下， `InitializeCom` COINIT_MULTITHREADED 标志传递给函数。 此标志指示该程序将是自由线程服务器。

现在，`CAtlServiceModuleT::Run`调用来执行该服务的主要工作。 `Run` 继续执行，直到该服务已停止。

## <a name="see-also"></a>请参阅

[服务](../atl/atl-services.md)<br/>
[Catlservicemodulet:: Servicemain](../atl/reference/catlservicemodulet-class.md#servicemain)

