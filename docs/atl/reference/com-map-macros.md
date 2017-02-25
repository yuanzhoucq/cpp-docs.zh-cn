---
title: "COM Map Macros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM 接口, COM map macros"
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# COM Map Macros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些宏定义COM接口映射。  
  
|||  
|-|-|  
|[BEGIN\_COM\_MAP](../Topic/BEGIN_COM_MAP.md)|标记COM接口映射项的开头。|  
|[COM\_INTERFACE\_ENTRY](../Topic/COM_INTERFACE_ENTRY%20Macros.md)|输入接口COM接口映射。|  
|[COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md)|使用此宏消除继承两个分支。|  
|[COM\_INTERFACE\_ENTRY\_IID](../Topic/COM_INTERFACE_ENTRY_IID.md)|使用此宏输入COM接口映射并指定其IID。|  
|[COM\_INTERFACE\_ENTRY2\_IID](../Topic/COM_INTERFACE_ENTRY2_IID.md)|和 [COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md)相同，不同之处在于，可以指定不同的IID。|  
|[COM\_INTERFACE\_ENTRY\_AGGREGATE](../Topic/COM_INTERFACE_ENTRY_AGGREGATE.md)|当 `iid` 确定的接口。查询，该 `COM_INTERFACE_ENTRY_AGGREGATE` 到 `punk`。|  
|[COM\_INTERFACE\_ENTRY\_AGGREGATE\_BLIND](../Topic/COM_INTERFACE_ENTRY_AGGREGATE_BLIND.md)|和 [COM\_INTERFACE\_ENTRY\_AGGREGATE](../Topic/COM_INTERFACE_ENTRY_AGGREGATE.md)，除此之外，查询在向前查询的任何IID的结果与对 `punk`。|  
|[COM\_INTERFACE\_ENTRY\_AUTOAGGREGATE](../Topic/COM_INTERFACE_ENTRY_AUTOAGGREGATE.md)|和 [COM\_INTERFACE\_ENTRY\_AGGREGATE](../Topic/COM_INTERFACE_ENTRY_AGGREGATE.md)相同，只不过，如果 `punk` 是 **NULL**，它自动创建 `clsid`描述的聚合。|  
|[COM\_INTERFACE\_ENTRY\_AUTOAGGREGATE\_BLIND](../Topic/COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND.md)|和 [COM\_INTERFACE\_ENTRY\_AUTOAGGREGATE](../Topic/COM_INTERFACE_ENTRY_AUTOAGGREGATE.md)，除此之外，查询任何IID相同的生成向前查询对 `punk`，并且，如果 `punk` 是 **NULL**，会自动创建 `clsid`描述的聚合。|  
|[COM\_INTERFACE\_ENTRY\_BREAK](../Topic/COM_INTERFACE_ENTRY_BREAK.md)|当指定接口。查询时，使您的程序调用 [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297)。|  
|[COM\_INTERFACE\_ENTRY\_CACHED\_TEAR\_OFF](../Topic/COM_INTERFACE_ENTRY_CACHED_TEAR_OFF.md)|保存接口特殊化的数据每个实例。|  
|[COM\_INTERFACE\_ENTRY\_TEAR\_OFF](../Topic/COM_INTERFACE_ENTRY_TEAR_OFF.md)|显示您撕掉接口。|  
|[COM\_INTERFACE\_ENTRY\_CHAIN](../Topic/COM_INTERFACE_ENTRY_CHAIN.md)|当处理到COM映射时，的此项处理基类中的COM映射。|  
|[COM\_INTERFACE\_ENTRY\_FUNC](../Topic/COM_INTERFACE_ENTRY_FUNC.md)|的挂钩到ATL的 `QueryInterface` 逻辑泛型结构。|  
|[COM\_INTERFACE\_ENTRY\_FUNC\_BLIND](../Topic/COM_INTERFACE_ENTRY_FUNC_BLIND.md)|和 [COM\_INTERFACE\_ENTRY\_FUNC](../Topic/COM_INTERFACE_ENTRY_FUNC.md)，除此之外，查询中调用的任何IID的结果与对 `func`。|  
|[COM\_INTERFACE\_ENTRY\_NOINTERFACE](../Topic/COM_INTERFACE_ENTRY_NOINTERFACE.md)|当指定接口。查询时，返回 **E\_NOINTERFACE** 和停止处理COM的映射。|  
|[END\_COM\_MAP](../Topic/END_COM_MAP.md)|标记COM接口映射项的结束。|  
  
## 请参阅  
 [Macros](../../atl/reference/atl-macros.md)   
 [COM Map Global Functions](../../atl/reference/com-map-global-functions.md)