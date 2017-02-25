---
title: "CMemoryState Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMemoryState"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMemoryState structure"
  - "检测内存泄漏"
  - "内存泄漏, 检测"
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CMemoryState Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

方便地检测到您的程序的内存泄漏。  
  
## 语法  
  
```  
struct CMemoryState  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMemoryState::CMemoryState](../Topic/CMemoryState::CMemoryState.md)|构造一个类似于选件类的结构该控件内存检查点。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMemoryState::Checkpoint](../Topic/CMemoryState::Checkpoint.md)|获取一个快照\(检查点\)当前内存状态。|  
|[CMemoryState::Difference](../Topic/CMemoryState::Difference.md)|计算类型之间 `CMemoryState`两个对象的差异。|  
|[CMemoryState::DumpAllObjectsSince](../Topic/CMemoryState::DumpAllObjectsSince.md)|转储所有当前分配的对象摘要从以前的检查点。|  
|[CMemoryState::DumpStatistics](../Topic/CMemoryState::DumpStatistics.md)|打印 `CMemoryState` 对象的内存分配统计信息。|  
  
## 备注  
 `CMemoryState` 是结构，并没有基类。  
  
 “内存泄漏”时，会发生对象的内存堆上分配的，但未释放时何时不再需要。  这类内存泄漏可能最终导致内存不足错误。  可通过多种方式分配和释放在程序的内存:  
  
-   使用功能 `malloc`\/**free** 系列从运行库的。  
  
-   使用Windows API内存管理函数，**LocalAlloc**\/**LocalFree** 和 **GlobalAlloc**\/**GlobalFree**。  
  
-   使用C\+\+ **new** 和 **delete** 运算符。  
  
 使用 **delete**时，那么，当使用 **new** 运算符分配的内存不会释放仅 `CMemoryState` 诊断帮助检测导致了内存泄漏。  内存管理函数的其他两组用于非C\+\+程序，并且，在同一程序的它们与 **new** 和 **delete** 不建议使用组合。  在需要文件和行号跟踪内存分配时，提供其他的宏，`DEBUG_NEW`替换 **new** 运算符。  使用`DEBUG_NEW` 时，通常会使用 **new** 运算符。  
  
 与其他诊断，`CMemoryState` 诊断才可用程序的调试版本。  调试版本必须定义。**\_DEBUG** 常数。  
  
 如果您怀疑您的程序的内存泄漏，您可以使用 `Checkpoint`，**Difference**，并且，查看内存状态\(分配的对象之间的差异的 `DumpStatistics` 函数\)在两个不同在程序执行点。  此信息有助于确定其分配的功能是否会清除所有对象。  
  
 如果知道在分配和释放的不平衡状态发生的位置不提供足够的信息，可以使用 `DumpAllObjectsSince` 函数转储分配的所有对象，由于以前的调用 `Checkpoint`。  该转储显示分配顺序、对象分配的源文件和行\(如果为发布使用 `DEBUG_NEW` \)和对象的派生，其地址及其大小。  `DumpAllObjectsSince` 还调用每个对象的 `Dump` 功能提供有关其当前状态的信息。  
  
 有关如何使用 `CMemoryState` 和其他诊断的更多信息，请参见 [调试MFC应用程序](../Topic/MFC%20Debugging%20Techniques.md)。  
  
> [!NOTE]
>  类型 `CMemoryState` 对象的声明和对应由 `#if defined(_DEBUG)/#endif`指令带功能的成员。  这将在您的程序调试版本会导致内存诊断仅包含。  
  
## 继承层次结构  
 `CMemoryState`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)