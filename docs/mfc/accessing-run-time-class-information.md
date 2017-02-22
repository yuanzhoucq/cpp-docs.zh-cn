---
title: "访问运行时类信息 | Microsoft Docs"
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
  - "类 [C++], 运行时类信息"
  - "CObject 类, 访问运行时类信息"
  - "CObject 类, 和 RTTI"
  - "CObject 类, 使用 IsKindOf 方法"
  - "CObject 类, 使用 RUNTIME_CLASS 宏"
  - "IsKindOf 方法的方法"
  - "RTTI 编译器选项"
  - "运行时"
  - "运行时, 类信息"
  - "运行时类"
  - "运行时类, 访问信息"
  - "RUNTIME_CLASS 宏"
  - "RUNTIME_CLASS 宏, using"
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 访问运行时类信息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明运行时如何访问有关对象的类的信息。  
  
> [!NOTE]
>  MFC不使用 在 Visual C\+\+ 4.0 中引入的 [运行时类型信息](../cpp/run-time-type-information.md) \(RTTI\) 支持。  
  
 如果已从 [CObject](../mfc/reference/cobject-class.md) 中的文章 [从派生类 CObject](../mfc/deriving-a-class-from-cobject.md)派生的类并使用 **DECLARE**\_**DYNAMIC** 以及 `IMPLEMENT_DYNAMIC`、`DECLARE_DYNCREATE` 和 `IMPLEMENT_DYNCREATE`也说明了 `DECLARE_SERIAL` 和 `IMPLEMENT_SERIAL` 宏，`CObject` 类能够确定对象的具体类在运行时。  
  
 此功能当函数参数附加类型检查需要时非常有用，并且，当必须编写基于对象的专用类中的代码。  但是，此做法，因为它复制虚拟函数的功能，通常建议不要使用。  
  
 `CObject` 成员函数 `IsKindOf` 可用于确定特定对象是否属于指定它是特定的类或从类派生。   `IsKindOf` 的参数是一个 `CRuntimeClass` 对象，您可以获取使用的类名的 `RUNTIME_CLASS` 宏。  
  
### 使用 RUNTIME\_CLASS 宏  
  
1.  使用类名的 `RUNTIME_CLASS`，此处显示的 `CObject`类：  
  
     [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/CPP/accessing-run-time-class-information_1.cpp)]  
  
 基本上不需要直接访问运行时类对象。  更通常是传递给 `IsKindOf` 函数运行时类对象，如下面的过程所示。  `IsKindOf` 函数测试一个对象来确定它是否属于特定类。  
  
#### 使用 IsKindOf 函数  
  
1.  确定类具有运行时类支持。  即在文章 [从派生类 CObject](../mfc/deriving-a-class-from-cobject.md)必须直接或间接从 `CObject` 派生了类并使用 **DECLARE**\_**DYNAMIC** 以及 `IMPLEMENT_DYNAMIC`、`DECLARE_DYNCREATE` 和 `IMPLEMENT_DYNCREATE`、解释的 `DECLARE_SERIAL` 和 `IMPLEMENT_SERIAL` 宏。  
  
2.  调用该类对象的 `IsKindOf` 成员函数，则使用 `RUNTIME_CLASS` 宏生成 `CRuntimeClass` 参数，如下所示：  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/CPP/accessing-run-time-class-information_2.h)]  
  
     [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/CPP/accessing-run-time-class-information_3.cpp)]  
  
    > [!NOTE]
    >  如果对象是指定类的成员是从指定类派生的类，或 IsKindOf 返回 **TRUE**。  `IsKindOf` 不支持多或虚拟继承的基类版本，不过，可以对派生的 Microsoft 基础类 \(MFC\) 如果需要，使用多重继承。  
  
 使用运行时类信息的可在对象的动态创建。  此进程在文章 [动态对象创建](../mfc/dynamic-object-creation.md)中讨论。  
  
 有关序列化并运行 TIME 类信息的更详细信息，请参见和文章 [MFC 中的文件](../mfc/files-in-mfc.md) [序列化](../mfc/serialization-in-mfc.md)。  
  
## 请参阅  
 [使用 CObject](../mfc/using-cobject.md)