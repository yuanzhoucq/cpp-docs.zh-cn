---
title: "从标准控件派生控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "公共控件 [C++], 派生自"
  - "控件 [MFC], 派生"
  - "派生控件"
  - "标准控件"
  - "标准控件, 派生控件自"
  - "Windows 公共控件 [C++], 派生自"
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 从标准控件派生控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

任何使用 [CWnd](../mfc/reference/cwnd-class.md)派生类，您可以从现有的控件类修改控制行为。  
  
### 创建一个派生的控件类  
  
1.  从现有的控件类派生类和可选择重写 **创建** 成员函数，以便提供必要的参数。**创建** 基类函数。  
  
2.  提供信息处理程序成员函数和消息映射项修改控制行为以响应特定窗口消息。  请参见[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。  
  
3.  提供新成员函数扩展控件的功能 \(可选\)。  
  
 在派生的控件需要额外的工作。  控件类型和位置。对话框随即在对话框模板资源通常指定。  如果创建一个派生的控件类，可以在对话框模板无法在中指定它，因为资源编译器不知道任何派生类。  
  
#### 放置派生的对话框控件。  
  
1.  在派生的对话框类的声明中嵌入控件派生的类的对象。  
  
2.  在对话框类中重写`OnInitDialog` 成员函数调用派生控件的 `SubclassDlgItem` 成员函数。  
  
 从对话框模板创建的`SubclassDlgItem`“动态子类”。  当控件为动态子类，则挂钩到窗口，处理内的某些消息自己的应用程序，然后将其余的消息到窗口中。  有关更多信息，请参见 `CWnd` 类的成员函数。[SubclassDlgItem](../Topic/CWnd::SubclassDlgItem.md) *MFC 参考*。  下面的示例显示您可以如何编写 `OnInitDialog` 重写调用 `SubclassDlgItem`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/CPP/deriving-controls-from-a-standard-control_1.cpp)]  
  
 由于派生的控件在对话框类嵌入，将构造该对话框构造，并且当销毁对话框将销毁它。  比较此代码为 [手动添加控件](../mfc/adding-controls-by-hand.md)的示例。  
  
## 请参阅  
 [创建和使用控件](../mfc/making-and-using-controls.md)   
 [控件](../mfc/controls-mfc.md)