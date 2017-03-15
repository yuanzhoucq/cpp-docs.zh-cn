---
title: "针对 MFC 模块状态中的激活上下文的支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "激活上下文 [C++]"
  - "激活上下文 [C++], MFC 支持"
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 针对 MFC 模块状态中的激活上下文的支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 创建活动上下文使用用户模块提供的不同资源。  有关上下文如何激活创建的更多信息，请参见以下主题：  
  
-   [Activation Contexts](http://msdn.microsoft.com/library/aa374153)  
  
-   [Application Manifests](http://msdn.microsoft.com/library/aa374191)  
  
-   [Assembly Manifests](http://msdn.microsoft.com/library/aa374219)  
  
## 备注  
 在读取这些 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 主题时请注意，MFC 活动上下文机制与 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 激活上下文以外，MFC 不使用 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 激活上下文 API。  
  
 激活上下文在 MFC 应用程序、用户 DLL 和扩展 DLL 以下方式工作：  
  
-   MFC 应用程序用于为清单资源使用资源 ID 1。  在这种情况下，MFC 不创建自己的激活上下文，使用，但是默认应用程序上下文。  
  
-   MFC 用户 DLL 其清单资源的使用资源 ID 2。  在这里，MFC 创建每用户 DLL 中的激活上下文，这样，其他用户可使用同一 DLL 库 \(例如，公共控件库\) 的不同版本。  
  
-   MFC 扩展依赖这些 DLL 的承载应用程序或 DLL 用户建立这些的激活上下文。  
  
 尽管上下文状态激活可以修改使用过程所述。[Using the Activation Context API](http://msdn.microsoft.com/library/aa376620)下，MFC 使用激活上下文机制非常有用，在开发不是简单的基于 DLL 的插件体系结构 \(或无法\) 手动切换状态激活在单个外部调用前后插件。  
  
 激活上下文中创建 [AfxWinInit](../Topic/AfxWinInit.md)。  在 `AFX_MODULE_STATE` 析构函数被销毁。  激活上下文句柄在 `AFX_MODULE_STATE`中使用。`AFX_MODULE_STATE`中对此[AfxGetStaticModuleState](../Topic/AfxGetStaticModuleState.md)进行了介绍。  
  
 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) 宏激活和停用激活上下文。  `AFX_MANAGE_STATE` 为静态 MFC 库，以及 MFC DLL，DLL 启用，使 MFC 代码在 DLL 用户选择的正确激活上下文执行。  
  
## 请参阅  
 [Activation Contexts](http://msdn.microsoft.com/library/aa374153)   
 [Application Manifests](http://msdn.microsoft.com/library/aa374191)   
 [Assembly Manifests](http://msdn.microsoft.com/library/aa374219)   
 [AfxWinInit](../Topic/AfxWinInit.md)   
 [AfxGetStaticModuleState](../Topic/AfxGetStaticModuleState.md)   
 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md)