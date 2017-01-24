---
title: "扩展 DLL：概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFXDLL 库"
  - "DLL [C++], 扩展"
  - "扩展 DLL [C++], 关于扩展 DLL"
  - "MFC DLL [C++], 扩展 DLL"
  - "共享的 DLL 版本 [C++]"
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 扩展 DLL：概述
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 扩展 DLL 是通常实现从现有 Microsoft 基础类库类派生的可重用类的 DLL。  扩展 DLL 是使用 MFC 动态链接库版本（也称作共享 MFC 版本）生成的。  只有用共享 MFC 版本生成的 MFC 可执行文件（应用程序或规则 DLL）才能使用扩展 DLL。  使用扩展 DLL，可以从 MFC 派生新的自定义类，然后将此“扩展”版本的 MFC 提供给调用 DLL 的应用程序。  
  
 扩展 DLL 也可用于在应用程序和 DLL 之间传递 MFC 派生的对象。  与已传递的对象关联的成员函数存在于创建对象所在的模块中。  由于在使用 MFC 的共享 DLL 版本时正确导出了这些函数，因此可以在应用程序和它加载的扩展 DLL 之间随意传递 MFC 或 MFC 派生的对象指针。  
  
 有关满足扩展 DLL 基本要求的 DLL 示例，请参见 MFC 示例 [DLLHUSK](http://msdn.microsoft.com/zh-cn/dfcaa6ff-b8e2-4efd-8100-ee3650071f90)。  特别要查看 Testdll1.cpp 和 Testdll2.cpp 文件。  
  
 请注意，Visual C\+\+ 文档中不再使用 AFXDLL 一词。  扩展 DLL 具有与原来的 AFXDLL 相同的特性。  
  
## 你希望做什么？  
  
-   [初始化扩展 DLL](../build/initializing-extension-dlls.md)  
  
## 您想进一步了解什么？  
  
-   [扩展 DLL](../build/extension-dlls.md)  
  
-   [在规则 DLL 中使用数据库、OLE 和套接字扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [非 MFC DLL：概述](../build/non-mfc-dlls-overview.md)  
  
-   [静态链接到 MFC 的规则 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [动态链接到 MFC 的规则 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [创建 MFC DLL](../mfc/reference/mfc-dll-wizard.md)  
  
## 请参阅  
 [DLL 类型](../build/kinds-of-dlls.md)