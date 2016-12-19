---
title: "ATL Module 类 | Microsoft Docs"
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
  - "ATL, module 类"
  - "CComModule 类, 更改了什么"
  - "module 类"
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Module 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题讨论的新增ATL 7.0的模块选件类。  
  
## CComModule替换选件类  
 ATL的早期版本使用的 `CComModule`。  在ATL 7.0，`CComModule` 函数中几选件类替换为:  
  
-   [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) 包含使用ATL的大多数应用程序需要的信息。  包含模块和资源例程的HINSTANCE。  
  
-   [CAtlComModule](../atl/reference/catlcommodule-class.md) 在ATL包含COM选件类需要的信息。  
  
-   [CAtlWinModule](../atl/reference/catlwinmodule-class.md) 在ATL包含多窗口选件类需要的信息。  
  
-   [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) 包含为接口调试支持。  
  
-   [CAtlModule](../atl/reference/catlmodule-class.md) 下面 `CAtlModule`派生类自定义在特定应用程序类型包含所需的信息。  这些选件类的大多数成员可以重写:  
  
    -   [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) 在DLL应用程序使用了。  用于标准导出的代码。  
  
    -   [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) 是EXE应用程序使用了。  提供在EXE所需的代码。  
  
    -   [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) 提供支持创建Windows NT和Windows 2000 service。  
  
 `CComModule` 备向后兼容可用。  
  
## 分配CComModule功能的原因  
 `CComModule` 的函数分配到下列原因的若干新的选件类:  
  
-   使 `CComModule` 的功能更新。  
  
     用于COM，多窗口，接口调试支持，因此，应用程序特定的\(DLL或EXE\)功能现在是单独选件类。  
  
-   将自动声明这些模块中的每一的全局实例个。  
  
     必需的模块选件类的全局实例链接到项目中。  
  
-   移除调用Init和术语方法必要性。  
  
     Init和术语方法将构造函数和析构函数模块选件类的;不再需要调用Init和术语。  
  
## 请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [Class Overview](../atl/atl-class-overview.md)