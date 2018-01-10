---
title: "ATL 服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CServiceModule
dev_langs: C++
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d13eebbe96ba57c82e3bf1c360b0cb471a6bd975
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="atl-services"></a>ATL 服务
若要创建 ATL COM 对象，以便它在服务中运行，只需从 ATL 项目向导中的服务器选项列表中选择服务 (EXE)。 然后，向导将创建派生自的类`CAtlServiceModuleT`若要实现服务。  
  
 ATL COM 对象生成时作为一种服务，它仅注册为本地服务器，并它将不会出现在控制面板中的服务列表。 这是因为它是更轻松地调试作为服务的本地服务器的服务。 若要安装它作为一种服务，在命令提示符处运行以下命令：  
  
 `YourEXE` `.exe /Service`  
  
 若要卸载它，请运行以下命令：  
  
 `YourEXE` `.exe /UnregServer`  
  
 本部分中的前四个主题讨论在执行过程中发生的操作`CAtlServiceModuleT`成员函数。 通常调用函数，这些主题将显示的顺序。 若要提高你了解这些主题，它是一个好办法使用 ATL 项目向导，作为引用生成的源代码。 包括以下这些前四个主题：  
  

-   [CAtlServiceModuleT::Start 函数](../atl/reference/catlservicemodulet-class.md#start)  
  
-   [CAtlServiceModuleT::ServiceMain 函数](../atl/reference/catlservicemodulet-class.md#servicemain)  
  
-   [CAtlServiceModuleT::Run 函数](../atl/reference/catlservicemodulet-class.md#run)  
  
-   [CAtlServiceModuleT::Handler 函数](../atl/reference/catlservicemodulet-class.md#handler)  
  
 最后三个主题讨论与相关的开发服务概念：  
  
-   [注册表项](../atl/registry-entries.md)ATL 服务  
  
-   [DCOMCNFG](../atl/dcomcnfg.md)  
  
-   [调试提示](../atl/debugging-tips.md)ATL 服务  
  
## <a name="see-also"></a>请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)

