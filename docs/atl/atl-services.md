---
title: "ATL 服务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CServiceModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 服务"
  - "COM 对象, ATL"
  - "CServiceModule 类"
  - "服务, ATL"
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 服务
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要创建自己的ATL COM对象，以便在服务中运行，选择服务\(exe\)从服务器选项列表。ATL项目向导的。  向导随后将创建从 `CAtlServiceModuleT` 派生的选件类实现服务。  
  
 当ATL COM对象生成作为服务，它才会注册为本地服务器，并且，在控制面板不会出现在服务列表。  这是因为，调试服务作为本地服务器上作为服务更为方便。  若要安装它作为服务，请运行以下命令提示:  
  
 `YourEXE` `.exe /Service`  
  
 若要卸载该文件，请运行以下操作:  
  
 `YourEXE` `.exe /UnregServer`  
  
 本节中的前四个主题讨论在 `CAtlServiceModuleT` 成员函数的执行过程中发生的事件。  这些主题显示与函数通常会调用的序列。  若要提高这些主题的理解，最好使用ATL项目向导生成的源代码作为引用。  这些前四个主题是:  
  
-   [CAtlServiceModuleT::Start功能](../atl/catlservicemodulet-start-function.md)  
  
-   [CAtlServiceModuleT::ServiceMain功能](../atl/catlservicemodulet-servicemain-function.md)  
  
-   [CAtlServiceModuleT::Run功能](../atl/catlservicemodulet-run-function.md)  
  
-   [CAtlServiceModuleT::Handler功能](../atl/catlservicemodulet-handler-function.md)  
  
 前三个主题讨论概念与开发服务相关:  
  
-   ATL服务的[注册表项](../atl/registry-entries.md)  
  
-   [DCOMCNFG](../atl/dcomcnfg.md)  
  
-   ATL服务的[调试提示](../atl/debugging-tips.md)  
  
## 请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)