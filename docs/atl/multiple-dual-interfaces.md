---
title: "Multiple Dual Interfaces | Microsoft Docs"
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
  - "COM_INTERFACE_ENTRY_IID macro"
  - "COM_INTERFACE_ENTRY2 macro"
  - "双重接口, exposing multiple"
  - "IDispatchImpl 类, multiple dual interfaces"
  - "multiple dual interfaces"
  - "multiple dual interfaces, exposing with ATL"
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Multiple Dual Interfaces
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可能希望合并双重接口\(因此即灵活性的优点vtable和后期绑定，使选件类可用的脚本语言和C\+\+\)与多重继承方法。  
  
 尽管可以显示在单个COM对象的多个双重接口是可能的，不建议使用。  如果有多个双重接口，必须只有了一 `IDispatch` 接口。  可用技术确保是这样的情况下罚如函数或增加的代码复杂性丢失。  考虑此方法的开发人员应仔细权衡的优点和缺点。  
  
## 显示单一IDispatch接口  
 通过派生显示在单个对象的多个双重接口是可以从 `IDispatchImpl`的两个或多个专用化。  但是，因此，如果允许客户端计算机的 `IDispatch` 接口查询，则需要使用 [COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md) 宏\(或 [COM\_INTERFACE\_ENTRY\_IID](../Topic/COM_INTERFACE_ENTRY_IID.md)\)指定要使用的基类。`IDispatch`的实现。  
  
 [!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/CPP/multiple-dual-interfaces_1.h)]  
  
 由于只能将一 `IDispatch` 接口示，通过 `IDispatch` 接口只能访问您的对象的客户端无法访问方法或属性在其他接口。  
  
## 将多个双重接口到IDispatch的单个实现中  
 ATL不提供任何为将多个双重接口支持。`IDispatch`的单个实现。  但是，有几个已知的方法来手动合并接口，如创建包含创建一个新的对象，执行 `QueryInterface` 函数或使用嵌套的对象一个基于typeinfo的实现的单独 `IDispatch` 接口来创建 `IDispatch` 接口的模板选件类。  
  
 这些方法都有潜在的命名空间冲突问题，以及代码复杂性和可维护性。  建议不要创建多个双绑定接口。  
  
## 请参阅  
 [Dual Interfaces and ATL](../atl/dual-interfaces-and-atl.md)