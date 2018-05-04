---
title: CAtlServiceModuleT::Start 函数 |Microsoft 文档
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
ms.openlocfilehash: da8d7358c634416941a551c93c6a2772549a3fd2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT::Start 函数
当运行时服务时， **_tWinMain**调用**CAtlServiceModuleT::WinMain**，从而又会调用`CAtlServiceModuleT::Start`。  
  
 `CAtlServiceModuleT::Start` 设置的数组**SERVICE_TABLE_ENTRY**映射到其启动函数的每个服务的结构。 此数组然后传递给 Win32 API 函数， [StartServiceCtrlDispatcher](http://msdn.microsoft.com/library/windows/desktop/ms686324)。 从理论上讲，一个 EXE 可处理多个服务和该数组可能具有多个**SERVICE_TABLE_ENTRY**结构。 目前，但是，ATL 生成的服务支持每个 EXE 仅一个服务。 因此，数组具有单个条目，其中包含服务名称和 **_ServiceMain**作为启动函数。 **_ServiceMain**是静态成员函数的`CAtlServiceModuleT`调用非静态成员函数， `ServiceMain`。  
  
> [!NOTE]
>  失败的**StartServiceCtrlDispatcher**连接到服务控制管理器 (SCM) 可能意味着不作为服务运行程序。 在这种情况下，在程序调用`CAtlServiceModuleT::Run`直接以便为本地服务器可以运行该程序。 有关为本地服务器中运行程序的详细信息，请参阅[进行调试的提示](../atl/debugging-tips.md)。  
  
## <a name="see-also"></a>请参阅  
 [服务](../atl/atl-services.md)   
 [CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)

