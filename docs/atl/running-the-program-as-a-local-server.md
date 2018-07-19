---
title: 为本地服务器中运行程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae2e44ba51a878d293ad5b497a1638cc9d7dc76
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848478"
---
# <a name="running-the-program-as-a-local-server"></a>为本地服务器中运行程序
如果作为服务运行该程序是不方便，可以暂时更改注册表，以便以普通的本地服务器运行该程序。 只需重命名`LocalService`下为你 AppID 值`_LocalService`，并确保`LocalServer32`正确设置您的 CLSID 下的键。 (请注意，使用 DCOMCNFG 指定，应另一台计算机上运行你的应用程序将重命名你`LocalServer32`关键`_LocalServer32`。)运行程序，如本地服务器上启动占用几秒钟时间，因为在调用`StartServiceCtrlDispatcher`中`CAtlServiceModuleT::Start`需要几秒钟就失败。  
  
## <a name="see-also"></a>请参阅  
 [调试提示](../atl/debugging-tips.md)

