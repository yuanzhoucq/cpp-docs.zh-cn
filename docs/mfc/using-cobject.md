---
title: "使用 CObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "CObject 类"
  - "派生类, 从 CObject"
  - "示例 [MFC], CObject"
  - "MFC, 基类"
  - "MFC 的根基类"
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 使用 CObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CObject](../mfc/reference/cobject-class.md) 是大多数的根基类 Microsoft 基础类库 \(MFC\)。  `CObject` 类包含自己可以合并到对象的程序中，包括序列化支持，运行时和对象类信息，诊断输出的许多有用的功能。  如果从 `CObject`类派生 `CObject` 类，可以使用这些功能。  
  
## 你希望做什么？  
  
-   [从 CObject 派生类](../mfc/deriving-a-class-from-cobject.md)  
  
-   [添加支持。运行时信息类、动态创建并序列化。我的派生类](../mfc/specifying-levels-of-functionality.md)  
  
-   [访问运行时信息类](../mfc/accessing-run-time-class-information.md)  
  
-   [动态创建对象](../mfc/dynamic-object-creation.md)  
  
-   [转储对象数据诊断目的](http://msdn.microsoft.com/zh-cn/727855b1-5a83-44bd-9fe3-f1d535584b59)  
  
-   验证对象内部状态 \(请参见 [MFC ASSERT\_VALID 和 CObject::AssertValid](http://msdn.microsoft.com/zh-cn/7654fb75-9e9a-499a-8165-0a96faf2d5e6)\)  
  
-   [使类序列化到永久存储。](../mfc/serialization-in-mfc.md)  
  
-   参见 [CObject 常见问题](../mfc/cobject-class-frequently-asked-questions.md)列表  
  
## 请参阅  
 [概念](../mfc/mfc-concepts.md)   
 [常规 MFC 主题](../mfc/general-mfc-topics.md)   
 [CRuntimeClass Structure](../mfc/reference/cruntimeclass-structure.md)   
 [文件](../mfc/files-in-mfc.md)   
 [序列化](../mfc/serialization-in-mfc.md)