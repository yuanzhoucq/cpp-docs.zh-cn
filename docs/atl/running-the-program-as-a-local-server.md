---
title: 为本地服务器中运行程序 |Microsoft 文档
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
ms.openlocfilehash: c2b8a79978528493e02ac5a272dafe8da6fdc1d9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360438"
---
# <a name="running-the-program-as-a-local-server"></a>为本地服务器中运行程序
如果作为服务运行程序来说很不方便，可以暂时更改注册表，以便为普通的本地服务器运行该程序时。 简单地重命名`LocalService`下到你 AppID 值`_LocalService`并确保`LocalServer32`正确设置你的 CLSID 下的键。 (请注意，使用 DCOMCNFG 指定你的应用程序，应运行的其他计算机上重命名你`LocalServer32`键，以`_LocalServer32`。)运行程序，如本地服务器上启动需要几详细秒钟，因为调用**StartServiceCtrlDispatcher**中`CAtlServiceModuleT::Start`需要几秒钟就失败。  
  
## <a name="see-also"></a>请参阅  
 [调试提示](../atl/debugging-tips.md)

