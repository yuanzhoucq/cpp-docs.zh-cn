---
title: "Creating an Aggregated Object | Microsoft Docs"
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
  - "aggregate objects [C++], 创建"
  - "aggregation [C++], creating aggregated objects"
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Creating an Aggregated Object
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

摘要委托 **IUnknown** 调用，并提供指向外部对象的 **IUnknown** 对内部对象。  
  
### 创建聚合的对象  
  
1.  添加一 **IUnknown** 指向您的选件类对象并将其初始化为在构造函数中 **NULL**。  
  
2.  重写创建聚合的 [FinalConstruct](../Topic/CComObjectRootEx::FinalConstruct.md)。  
  
3.  使用 **IUnknown** 指针，定义在步骤1中，作为第二个参数指定 [COM\_INTERFACE\_ENTRY\_AGGREGATE](../Topic/COM_INTERFACE_ENTRY_AGGREGATE.md) 宏。  
  
4.  重写释放 **IUnknown** 指针的 [FinalRelease](../Topic/CComObjectRootEx::FinalRelease.md)。  
  
> [!NOTE]
>  在 `FinalConstruct`期间，如果要从聚合的对象使用和释放一个接口，应将 [DECLARE\_PROTECT\_FINAL\_CONSTRUCT](../Topic/DECLARE_PROTECT_FINAL_CONSTRUCT.md) 宏到您的选件类对象的定义。  
  
## 请参阅  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)