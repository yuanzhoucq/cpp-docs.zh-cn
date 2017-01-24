---
title: "ATL 和自由线程封送拆收器 | Microsoft Docs"
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
  - "ATL, 自由线程封送拆收器"
  - "自由线程封送拆收器"
  - "ATL 中的 FTM"
  - "线程处理 [ATL], 自由线程封送拆收器"
  - "线程处理 [C++], ATL 中的封送拆收器"
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 和自由线程封送拆收器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL简单对象向导的属性页提供了使您的选件类复合自由线程封送拆收器\(FTM\)选项卡。  
  
 向导在 `FinalConstruct` 在 `FinalRelease`生成代码创建的自由线程封送拆收器的实例和释放该实例。  `COM_INTERFACE_ENTRY_AGGREGATE` 宏自动添加到COM映射确保 `QueryInterface` 请求 [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707) 由自由线程的封送拆收器。  
  
 自由线程封送拆收器允许直接访问在对象的接口从在同一的所有线程处理，加速跨单元调用。  此选项适用于使用两个线程处理模型的选件类使用。  
  
 在使用此选项时，选件类都必须对其数据线程安全的责任。  此外，复合自由线程封送拆收器和需要使用其他对象获取的接口指针的对象必须执行附加步骤以确保接口正确封送。  通常，每次使用，则与存储接口指针在全局接口表\(GIT\)中并获取指针从GIT它。  ATL提供选件类 [CComGITPtr](../atl/reference/ccomgitptr-class.md) 帮助您在GIT存储的接口指针。  
  
## 请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [CoCreateFreeThreadedMarshaler](http://msdn.microsoft.com/library/windows/desktop/ms694500)   
 [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707)   
 [When to Use the Global Interface Table](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [In\-Process Server Threading Issues](http://msdn.microsoft.com/library/windows/desktop/ms687205)