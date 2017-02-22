---
title: "指定功能级别 | Microsoft Docs"
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
  - "CObject 类, 向派生类添加功能"
  - "动态创建支持"
  - "级别 [C++]"
  - "级别 [C++], CObject 中的功能"
  - "运行时 [C++], 类信息"
  - "运行时类, 信息支持"
  - "序列化 [C++], Cobject"
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 指定功能级别
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文介绍如何添加以下级别功能以 [CObject](../mfc/reference/cobject-class.md)派生类：  
  
-   [运行时类的信息](#_core_to_add_run.2d.time_class_information)  
  
-   [动态创建支持](#_core_to_add_dynamic_creation_support)  
  
-   [序列化支持](#_core_to_add_serialization_support)  
  
 有关 `CObject` 函数的概述，请参阅文章 [从派生类 CObject](../mfc/deriving-a-class-from-cobject.md)。  
  
#### 添加运行时类信息  
  
1.  从 `CObject`派生类，如 [从派生类 CObject](../mfc/deriving-a-class-from-cobject.md) 文章所述。  
  
2.  类声明使用 `DECLARE_DYNAMIC` 宏，如下所示：  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/CPP/specifying-levels-of-functionality_1.h)]  
  
3.  实现文件 \(.cpp\) 类使用 `IMPLEMENT_DYNAMIC` 宏。  此宏将用作参数类及其基类的名称，如下所示：  
  
     [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/CPP/specifying-levels-of-functionality_2.cpp)]  
  
> [!NOTE]
>  为类请始终将 `IMPLEMENT_DYNAMIC` 放在一实现文件 \(.cpp\)。  应一次仅在编译时计算 `IMPLEMENT_DYNAMIC` 宏，因此不应使用在多个文件有可能覆盖的接口文件\(.H\)。  
  
#### 添加动态创建支持  
  
1.  从 `CObject` 派生你的类。  
  
2.  类声明使用 `DECLARE_DYNCREATE` 宏。  
  
3.  定义无参构造函数（默认的构造函数）。  
  
4.  类实现文件使用 `IMPLEMENT_DYNCREATE` 宏。  
  
#### 添加序列化支持  
  
1.  从 `CObject` 派生你的类。  
  
2.  重写 `Serialize` 成员函数。  
  
    > [!NOTE]
    >  如果直接调用 `Serialize` ，不希望通过多态指针序列化对象，省略步骤 3 到 5。.  
  
3.  类声明使用 `DECLARE_SERIAL` 宏。  
  
4.  定义无参构造函数（默认的构造函数）。  
  
5.  类实现文件使用 `IMPLEMENT_SERIAL` 宏。  
  
> [!NOTE]
>  “多态指针”指向一个类（成为A）对象或从 A 派生的任何类对象 \(假设，B\)。  通过多态指针序列化，框架必须确定它序列化 \(B\) 对象的运行时类，因为它可能是与一些基类\(A\)派生的任何类对象。  
  
 有关当从 `CObject`派生类时如何启用序列化的详细信息，请参阅文章 [MFC 中的文件](../mfc/files-in-mfc.md) [序列化](../mfc/serialization-in-mfc.md)。  
  
## 请参阅  
 [从 CObject 派生类](../mfc/deriving-a-class-from-cobject.md)