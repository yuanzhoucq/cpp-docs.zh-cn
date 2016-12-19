---
title: "CFixedStringT: Example of a Custom String Manager | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFixedStringT class, using a custom string manager"
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFixedStringT: Example of a Custom String Manager
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL库实现选件类使用的自定义字符串管理器的示例 [CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md)，调用 **CFixedStringMgr**。  `CFixedStringT` 从 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 派生并实现将其字符数据作为对象 `CFixedStringT` 一部分的字符串，只要该字符串的 `CFixedStringT`的 **t\_nChars** 模板参数指定的长度是的少。  此方法，除非该字符串的长度在固定缓冲区之外，的大小增大该字符串根本不需要堆。  由于 `CFixedStringT` 并不总是使用堆分配其字符串数据，不能将 **CAtlStringMgr** 作为字符串管理器。  它使用自定义字符串管理器\(**CFixedStringMgr**\)，[IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) 实现接口。  此接口。[自定义字符串管理器\(高级方法的实现](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)讨论。  
  
 **CFixedStringMgr** 的构造函数采用三个参数:  
  
-   对于内置的 `CStringData` 结构的**pData:** 指针是使用。  
  
-   **nChars:** `CStringData` 结构可以容纳的最大字符数。  
  
-   为“备份字符串管理器的 `IAtlStringMgr` 接口的**pMgr:** 指针”。  
  
 构造函数在其各自的成员变量存储 `pData` 和 **pMgr** 的值\(`m_pData` 和 **m\_pMgr**\)。  然后设置缓冲区的长度为零，了可用的长度等于内置的缓冲区的最大大小和引用计数为– 1。  引用绑定值指示缓冲区已锁定和使用 **CFixedStringMgr** 此实例作为字符串管理器。  
  
 标记缓冲区为锁定阻止其他 `CStringT` 实例保存共享对缓冲区。  如果其他 `CStringT` 实例允许共享缓冲区为 `CFixedStringT` 包含的缓冲区可能需要删除，当其他字符串仍使用缓冲区时。  
  
 **CFixedStringMgr** 是 `IAtlStringMgr` 接口的完全实现。  每个方法的实现分开讨论。  
  
## CFixedStringMgr::Allocate的实现  
 **CFixedStringMgr::Allocate** 的实现首先检查该字符串的请求范围是否小于或等于内置的缓冲区的大小\(存储在 `m_pData` 成员\)。  如果内置的缓冲区足够大，**CFixedStringMgr** 锁定与零长度的内置的缓冲区。  只要字符串长度不在固定缓冲区范围外的增大，`CStringT` 不必重新分配缓冲区。  
  
 如果该字符串的请求的大小大于内置的缓冲区 **CFixedStringMgr** 要备份的请求向前字符串管理器。  备份字符串管理器将假定从堆分配缓冲区。  但是，在返回此缓冲区 **CFixedStringMgr** 锁之前缓冲区和使用指针替换缓冲区的字符串管理器指向 **CFixedStringMgr** 对象。  这样可以确保尝试通过 `CStringT` 重新分配或释放缓冲区将调入 **CFixedStringMgr**。  
  
## CFixedStringMgr::ReAllocate的实现  
 **CFixedStringMgr::ReAllocate** 的实现类似于其 **Allocate**的实现。  
  
 如果重新分配的缓冲区是内置的缓冲区，并请求的缓冲区大小小于内置的缓冲区，发布未完成。  但是，因此，如果缓冲区重新分配的不是内置的缓冲区，它必须是缓冲区随该备份管理器。  在这种情况备份管理器用于重新分配缓冲区。  
  
 如果重新分配的缓冲区是固定的缓冲区，并且新的缓冲区大小太大而无法在固定缓冲区之内，使用该备份管理器，**CFixedStringMgr** 分配新的缓冲区。  内置的缓冲区的内容然后将其复制到新的缓冲区。  
  
## CFixedStringMgr::Free的实现  
 **CFixedStringMgr::Free** 的实现遵循与 **Allocate** 和 `ReAllocate`相同。  如果已释放的缓冲区是固定的缓冲区，方法将其设置为零的锁定的缓冲区。  如果已释放的缓冲区分配了该备份管理器，**CFixedStringMgr** 使用该备份管理器来释放。  
  
## CFixedStringMgr::Clone的实现  
 **CFixedStringMgr::Clone** 的实现始终返回指向该备份管理器而不是 **CFixedStringMgr**。  因为 **CFixedStringMgr** 每个实例只能与 `CStringT`，一个实例发生此错误。  尝试 `CStringT` 任何其他的实例克隆管理器如果捕获该备份管理器。  这是因为，该备份管理器支持共享。  
  
## CFixedStringMgr::GetNilString的实现  
 **CFixedStringMgr::GetNilString** 实现返回内置的缓冲区。  由于 **CFixedStringMgr** 和 `CStringT`一对一的通信，`CStringT` 特定实例每次从不使用多个缓冲区。  因此，null字符串和实际字符串缓冲区同时不需要。  
  
 每当内置的缓冲区中正在使用中，**CFixedStringMgr** 确保它初始化零。  这使它用作零字符串。  为添加的附加属性，内置的缓冲区的 `nAllocLength` 成员始终设置为内置的缓冲区的完整大小。  即使为null字符串意味着 `CStringT` 可能存在该字符串，而不调用，[IAtlStringMgr::Reallocate](../Topic/IAtlStringMgr::Reallocate.md)。  
  
## 要求  
 **Header:** cstringt.h  
  
## 请参阅  
 [Memory Management with CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)