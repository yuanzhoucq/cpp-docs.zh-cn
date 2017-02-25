---
title: "运行时对象模型服务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "运行时对象模型服务宏"
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# 运行时对象模型服务
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CObject [](../../mfc/reference/cobject-class.md "CObject Class") 和 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 类封装若干对象服务，包括到运行时类信息、序列化及动态对象创建的访问权限。  从 `CObject` 派生的所有类都继承此功能。  
  
 对运行时类信息的访问可确定有关运行时对象类的信息。  在运行时能够确定对象的类，在需要函数参数的额外类型检查时很有用，并且，当必须编写基于对象的类的专用代码时很有用。  运行时类信息不是直接由 C\+\+ 语言支持。  
  
 序列化是从文件写入或读取对象内容的过程。  在应用程序退出后，可以使用序列化存储对象的内容。  当应用程序启动时，对象可从文件中读取。  这些数据对象被称为“持久化”。  
  
 动态对象创建允许您在运行时创建一指定类的对象。  例如，文档、视图和帧对象必须支持动态创建，因为框架需要动态创建这些。  
  
 下表列出了支持运行时的类信息、序列化及动态创建的 MFC 宏。  
  
 有关这些运行时对象服务和序列化的更多信息，请参见文章 [CObject 类：访问运行时类信息](../../mfc/accessing-run-time-class-information.md)。  
  
### 运行时对象模型服务宏  
  
|||  
|-|-|  
|[DECLARE\_DYNAMIC](../Topic/DECLARE_DYNAMIC.md)|允许对运行时类信息的访问 \(必须在类中声明\)。|  
|[DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md)|运行动态创建和访问运行时类信息 \(必须在类中声明\)。|  
|[DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md)|允许序列化和访问运行时类信息 \(必须在类中声明\)。|  
|[IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md)|允许对运行时类信息的访问 \(必须在类中实现\)。|  
|[IMPLEMENT\_DYNCREATE](../Topic/IMPLEMENT_DYNCREATE.md)|允许动态创建和访问运行时类信息 \(必须在类中实现\)。|  
|[IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md)|允许序列化和访问运行时类信息 \(必须在类中实现\)。|  
|[RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md)|返回相应于命名类的 `CRuntimeClass` 结构。|  
  
 OLE 通常要求在运行时动态创建对象。  例如，OLE 服务器应用程序必须可动态创建 OLE 项来响应来自客户端的请求。  同样，自动化服务器必须能够创建项响应自动化客户端的请求。  
  
 Microsoft 基础类 \(MFC\) 库提供两个特定的宏到 OLE。  
  
### OLE 对象的动态创建  
  
|||  
|-|-|  
|[DECLARE\_OLECREATE](../Topic/DECLARE_OLECREATE.md)|运行通过 OLE 自动化创建对象。|  
|[IMPLEMENT\_OLECREATE](../Topic/IMPLEMENT_OLECREATE.md)|允许 OLE 系统创建对象。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)