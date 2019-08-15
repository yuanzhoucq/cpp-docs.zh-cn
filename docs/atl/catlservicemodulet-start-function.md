---
title: 'CAtlServiceModuleT:: Start 函数'
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: e6de15f40e89bfffba504db04ee7a16b2a68cac9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491669"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT:: Start 函数

当服务运行时, `_tWinMain`将调用`CAtlServiceModuleT::WinMain`, 后者又会调用。 `CAtlServiceModuleT::Start`

`CAtlServiceModuleT::Start`设置将每个服务`SERVICE_TABLE_ENTRY`映射到其启动函数的结构的数组。 然后, 将此数组传递到 Win32 API 函数[StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw)。 理论上, 一个 EXE 可以处理多个服务, 而数组可以有`SERVICE_TABLE_ENTRY`多个结构。 但目前, ATL 生成的服务仅支持每个 EXE 一个服务。 因此, 该数组包含单个项, 其中包含服务名称和`_ServiceMain`启动函数。 `_ServiceMain`是调用非静态成员`CAtlServiceModuleT` `ServiceMain`函数的的静态成员函数。

> [!NOTE]
>  `StartServiceCtrlDispatcher`如果无法连接到服务控制管理器 (SCM), 这可能意味着该程序不是以服务的形式运行。 在这种情况下, 程序`CAtlServiceModuleT::Run`将直接调用, 以便程序可以作为本地服务器运行。 有关将程序作为本地服务器运行的详细信息, 请参阅[调试提示](../atl/debugging-tips.md)。

## <a name="see-also"></a>请参阅

[服务](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
