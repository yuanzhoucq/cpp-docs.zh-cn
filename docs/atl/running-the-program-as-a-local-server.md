---
title: "为本地服务器中运行程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e398bfed0174e4ec2a262ea03076ed17881f900
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="running-the-program-as-a-local-server"></a>为本地服务器中运行程序
如果作为服务运行程序来说很不方便，可以暂时更改注册表，以便为普通的本地服务器运行该程序时。 简单地重命名`LocalService`下到你 AppID 值`_LocalService`并确保`LocalServer32`正确设置你的 CLSID 下的键。 (请注意，使用 DCOMCNFG 指定你的应用程序，应运行的其他计算机上重命名你`LocalServer32`键，以`_LocalServer32`。)运行程序，如本地服务器上启动需要几详细秒钟，因为调用**StartServiceCtrlDispatcher**中`CAtlServiceModuleT::Start`需要几秒钟就失败。  
  
## <a name="see-also"></a>请参阅  
 [调试提示](../atl/debugging-tips.md)

