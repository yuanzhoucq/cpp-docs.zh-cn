---
title: "如何：为模板类创建消息映射 | Microsoft Docs"
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
  - "消息映射, 模板类"
  - "模板类, 创建消息映射"
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 如何：为模板类创建消息映射
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 中的信息映射提供了一种有效方法直接处理 Windows 消息为适当的 C\+\+ 对象实例。  MFC 消息映射目标示例包含应用程序类、文档和视图类，控件类等等。  
  
 传统 MFC 消息映射声明使用 [BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md) 宏声明消息映射的开头，它为每个消息处理程序类方法的宏输入，最后 [END\_MESSAGE\_MAP](../Topic/END_MESSAGE_MAP.md) 宏声明映射消息的结尾。  
  
 当该宏与包含模板参数的类一起使用时， [BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md) 宏的一个限制会出现。  在和模板类一起使用时，此宏会导致编译时错误由于在宏展开过程中缺少模板参数。  [BEGIN\_TEMPLATE\_MESSAGE\_MAP](../Topic/BEGIN_TEMPLATE_MESSAGE_MAP.md) 宏的设计允许类包含单个模板参数声明其消息映射。  
  
## 示例  
 考虑 MFC [CListBox](../mfc/reference/clistbox-class.md) 类扩展为提供与外部数据源同步的示例。  虚拟 **CSyncListBox** 类的声明如下：  
  
 [!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_1.h)]  
  
 **CSyncListBox** 类上描述将同步的数据源，为单一类型模板。  它还声明三种方法参与类的消息映射：**OnPaint**、**OnDestroy**和 **OnSynchronize**。  **OnSynchronize** 方法实现如下：  
  
 [!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_2.cpp)]  
  
 上述实现允许 **CSyncListBox** 类可以被任何实现 **GetCount** 方法的类类型指定，例如 **CArray**，**CList** 和 **CMap**。  **StringizeElement** 函数为模板函数原型如下：  
  
 [!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_3.cpp)]  
  
 通常，此类的消息映射将如下定义：  
  
 `BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)`  
  
 `ON_WM_PAINT()`  
  
 `ON_WM_DESTROY()`  
  
 `ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)`  
  
 `END_MESSAGE_MAP()`  
  
 **LBN\_SYNCHRONIZE** 为自定义用户消息的情况由应用程序定义，例如：  
  
 [!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_4.cpp)]  
  
 上面宏映射将不编译，因为在宏展开过程中 **CSyncListBox** 类的模板规范会丢失。  **BEGIN\_TEMPLATE\_MESSAGE\_MAP** 宏通过合并指定的模板参数到扩展的宏映射来解决此问题。  此类的消息映射将成为：  
  
 [!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_5.cpp)]  
  
 下面演示使用 **CStringList** 对象的 **CSyncListBox** 类的用法：  
  
 [!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_6.cpp)]  
  
 若要完成测试，**StringizeElement** 函数必须指定与 **CStringList** 类一起使用：  
  
 [!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_7.cpp)]  
  
## 请参阅  
 [BEGIN\_TEMPLATE\_MESSAGE\_MAP](../Topic/BEGIN_TEMPLATE_MESSAGE_MAP.md)   
 [消息处理和映射](../mfc/message-handling-and-mapping.md)