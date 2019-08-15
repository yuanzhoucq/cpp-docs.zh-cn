---
title: 'CAtlServiceModuleT:: ServiceMain 函数'
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: b79767d4c1696174f90a325ea152ccc7939ed9fe
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491714"
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT:: ServiceMain 函数

服务控制管理器 (SCM) 在`ServiceMain`您打开 "服务" 控制面板应用程序时调用, 选择该服务, 然后单击 "**启动**"。

在 SCM 调用`ServiceMain`后, 服务必须为 SCM 指定处理程序函数。 此函数允许 SCM 获取服务的状态并传递特定说明 (如暂停或停止)。 当服务传递`_Handler`到 Win32 API 函数[RegisterServiceCtrlHandler](/windows/win32/api/winsvc/nf-winsvc-registerservicectrlhandlerw)时, SCM 获取此函数。 (`_Handler`是调用非静态成员函数[处理程序](../atl/reference/catlservicemodulet-class.md#handler)的静态成员函数。)

在启动时, 服务还应通知 SCM 其当前状态。 它通过将 SERVICE_START_PENDING 传递到 Win32 API 函数[SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus)来实现此功能。

`ServiceMain`然后调用`CAtlExeModuleT::InitializeCom`, 它调用 Win32 API 函数[CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex)。 默认情况下`InitializeCom` , 会将 COINIT_MULTITHREADED 标志传递给函数。 此标志指示该程序是一个自由线程服务器。

现在, `CAtlServiceModuleT::Run`调用以执行服务的主要工作。 `Run`继续执行, 直到服务停止。

## <a name="see-also"></a>请参阅

[服务](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
