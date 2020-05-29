---
title: CAtlServiceModuleT：：启动功能
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: 50054bbb34bcc31a1d11dd8bfab797f98e4e82f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317280"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT：：启动功能

运行服务时，`_tWinMain`调用`CAtlServiceModuleT::WinMain`调用 ，然后调用`CAtlServiceModuleT::Start`。

`CAtlServiceModuleT::Start`设置一个`SERVICE_TABLE_ENTRY`结构数组，将每个服务映射到其启动函数。 然后，此数组将传递给 Win32 API 函数[StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw)。 理论上，一个 EXE 可以处理多个服务，并且阵列可以`SERVICE_TABLE_ENTRY`有多个结构。 但是，目前 ATL 生成的服务仅支持每个 EXE 的一个服务。 因此，数组具有一个包含服务名称并作为`_ServiceMain`启动函数的条目。 `_ServiceMain`是调用非静态成员函数`CAtlServiceModuleT`的静态成员函数`ServiceMain`。

> [!NOTE]
> `StartServiceCtrlDispatcher`无法连接到服务控制管理器 （SCM） 可能意味着程序未作为服务运行。 在这种情况下，程序直接调用`CAtlServiceModuleT::Run`，以便程序可以作为本地服务器运行。 有关将程序作为本地服务器运行的详细信息，请参阅[调试提示](../atl/debugging-tips.md)。

## <a name="see-also"></a>另请参阅

[服务](../atl/atl-services.md)<br/>
[CAtlService 模块T：：开始](../atl/reference/catlservicemodulet-class.md#start)
