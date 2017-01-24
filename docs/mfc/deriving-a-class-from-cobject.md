---
title: "从 CObject 派生类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject 类, 派生自"
  - "CObject 类, 派生可序列化类"
  - "DECLARE_DYNAMIC 宏"
  - "DECLARE_DYNCREATE 宏"
  - "DECLARE_SERIAL 宏"
  - "派生类, 从 CObject"
  - "宏 [C++], 序列化"
  - "序列化 [C++], 宏"
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 从 CObject 派生类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这篇文章描述必须的最小的步骤来从[CObject](../mfc/reference/cobject-class.md)中继承类。  其他 `CObject` 类文章介绍的必要步骤来利用特定 `CObject` 功能，如序列化诊断和调试支持。  
  
 在开展 `CObject`的讨论中，术语“连接”文件，并且经常受到使用。“实现文件”。  接口文件 \(通常称为头文件。H 文件\) 包含必要的类声明和其他信息使用类。  实现文件 \(.cpp 或文件\) 包含类定义并实现类成员函数的代码。  例如，对于，类名为 `CPerson`，通常会创建一个名为 PERSON.H 的接口文件和实现文件名为 PERSON.CPP。  但是，对于不会在应用程序中共享这些小的类，将接口和实现到单个 .cpp 文件有时是更容易。  
  
 可以从四层功能选择，当从 `CObject`派生类：  
  
-   基本功能：支持的运行时类信息或序列化，但不包括诊断内存管理。  
  
-   基本功能和支持的运行时类信息。  
  
-   基本功能和支持的运行时类信息和动态创建。  
  
-   基本功能和支持的运行时类信息和动态创建。  
  
 为后将用作基类\) 的重用的类 \(这些应至少包含运行时和类支持序列化支持，因此，如果任何将来的序列化需要预期。  
  
 您选择级别功能通过在您从 `CObject`派生该类的声明和实现的特定宏声明和实现。  
  
 下表显示了使用的宏。中的关系。支持序列化和运行时信息。  
  
### 用于序列化和运行时信息的宏  
  
|使用的宏。|CObject::IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator\>\><br /><br /> CArchive::operator\<\<|  
|-----------|-----------------------|--------------------------------------|-------------------------------------------------------|  
|基本的 `CObject` 功能|否|否|否|  
|`DECLARE_DYNAMIC`|是|否|否|  
|`DECLARE_DYNCREATE`|是|是|否|  
|`DECLARE_SERIAL`|是|是|是|  
  
#### 使用基本的 CObject 功能  
  
1.  使用常规 C\+\+ 语法从 `CObject` 派生类 \(或从 `CObject`派生的类\)。  
  
     下面的示例显示最简单的情况，一个从 `CObject`派生的类：  
  
     [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/CPP/deriving-a-class-from-cobject_1.h)]  
  
 通常，但是，您也可能想重写某些 `CObject` 成员函数来处理新类的特定。  例如，您通常可能要重写 `CObject` 的 `Dump` 函数。类的内容提供调试输出。  有关如何重写 `Dump`的详细信息，请参见 [诊断：转储对象内容](http://msdn.microsoft.com/zh-cn/727855b1-5a83-44bd-9fe3-f1d535584b59)文章。  可能还要重写 `CObject` 的 `AssertValid` 函数提供自定义的测试验证类对象数据成员的一致性。  有关阐释如何重写 `AssertValid`，请参见 [MFC ASSERT\_VALID 和 CObject::AssertValid](http://msdn.microsoft.com/zh-cn/7654fb75-9e9a-499a-8165-0a96faf2d5e6)。  
  
 文章 [指定级别功能](../mfc/specifying-levels-of-functionality.md) 介绍如何指定其他级别功能，包括运行时信息类、动态对象创建并序列化。  
  
## 请参阅  
 [使用 CObject](../mfc/using-cobject.md)