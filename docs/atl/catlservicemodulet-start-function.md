---
title: 'Catlservicemodulet:: Start 函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule.Start
- CServiceModule::Start
dev_langs:
- C++
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e1b367dd02506678af8c147dc93bb8725ca3c83
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762705"
---
# <a name="catlservicemoduletstart-function"></a>Catlservicemodulet:: Start 函数

当运行该服务时，`_tWinMain`调用`CAtlServiceModuleT::WinMain`，从而又会调用`CAtlServiceModuleT::Start`。

`CAtlServiceModuleT::Start` 设置一个数组`SERVICE_TABLE_ENTRY`将每个服务映射到其启动函数的结构。 然后将此数组传递给 Win32 API 函数[StartServiceCtrlDispatcher](/windows/desktop/api/winsvc/nf-winsvc-startservicectrldispatchera)。 从理论上讲，一个 EXE 可以处理多个服务，并且数组可能具有多个`SERVICE_TABLE_ENTRY`结构。 目前，但是，ATL 生成的服务支持每个 EXE 只有一个服务。 因此，数组有单个条目，其中包含服务名称和`_ServiceMain`作为启动函数。 `_ServiceMain` 是的静态成员函数`CAtlServiceModuleT`调用非静态成员函数， `ServiceMain`。

> [!NOTE]
>  失败的`StartServiceCtrlDispatcher`连接到服务控制管理器 (SCM) 可能表示未将作为服务运行，该程序。 在这种情况下，在程序调用`CAtlServiceModuleT::Run`直接，以便程序可以运行与本地服务器。 有关为本地服务器运行该程序的详细信息，请参阅[进行调试的提示](../atl/debugging-tips.md)。

## <a name="see-also"></a>请参阅

[服务](../atl/atl-services.md)   
[Catlservicemodulet:: Start](../atl/reference/catlservicemodulet-class.md#start)

