---
title: "自动化服务器：对象生存期问题 | Microsoft Docs"
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
  - "自动化服务器, 对象生存期"
  - "生存期, 自动化服务器"
  - "对象 [C++], 生存期"
  - "服务器, 最大化的生存期"
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 自动化服务器：对象生存期问题
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当自动化客户或激活一个 OLE 项时，服务器将客户指向该对象。  客户端通过调用OLE 函数 [IUnknown::AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)来建立对对象的引用。  该引用直到客户调用 [以为 IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317)一直有效。\(客户端应用程序编写使用 Microsoft 基础类库类的 OLE 不需要执行这些调用；此框架如此。\)OLE 系统和服务器可能建立对对象的引用。  只要对对象的外部引用仍然有效，服务器不应销毁对象。  
  
 框架维护引用的生成计数到 [CCmdTarget](../mfc/reference/ccmdtarget-class.md)派生的所有服务器对象。  当一个自动化客户端或其他实体增加或释放一个对象的引用，此计数被更新。  
  
 当引用计数变为 0 时，框架调用虚函数[CCmdTarget::OnFinalRelease](../Topic/CCmdTarget::OnFinalRelease.md) 此函数的默认实现调用**删除** 运算符来删除此对象 。  
  
 当外部客户端具有对应用程序的对象引用时，Microsoft 基础类库提供用于控制应用程序行为的附加功能。  除了为每个对象维护一计数的引用之外，服务器维持全局计数活动对象。  全局函数 [AfxOleLockApp](../Topic/AfxOleLockApp.md)和 [AfxOleUnlockApp](../Topic/AfxOleUnlockApp.md) 更新应用程序的活动对象。  如果此计算为非零，应用程序不会终止，当用户从系统菜单选择关闭或退出从"文件"菜单。  相反，应用程序的主窗口隐藏 \(但不销毁\)，直到所有等待客户端请求完成。  通常，`AfxOleLockApp` 和 `AfxOleUnlockApp`在构造函数和析构函数中调用，相应地，分别支持自动化类。  
  
 有时，情况迫使服务器终止，而客户端仍具有对对象的引用。  例如，服务器依赖的资源变得不可用，这会导致服务器时遇到错误。  用户也可能关闭包含其他应用程序都引用的对象的服务器文档。  
  
 在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 请参见 `IUnknown::AddRef`和`IUnknown::Release`。  
  
## 请参阅  
 [自动化服务器](../mfc/automation-servers.md)   
 [AfxOleCanExitApp](../Topic/AfxOleCanExitApp.md)