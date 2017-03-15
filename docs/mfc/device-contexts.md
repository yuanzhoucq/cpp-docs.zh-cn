---
title: "设备上下文 | Microsoft Docs"
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
  - "BeginPaint 方法, CPaintDC"
  - "CClientDC 类, 和 GetDC 方法"
  - "CClientDC 类, 和 ReleaseDC 方法"
  - "CDC 类, 对象"
  - "客户端区域"
  - "客户端区域, 和设备上下文"
  - "CMetaFileDC 类, 和 OnPrepareDC 方法"
  - "CPaintDC 类, 用于绘制的设备上下文"
  - "设备上下文 [C++]"
  - "设备上下文 [C++], 关于设备上下文"
  - "设备上下文 [C++], CDC 类"
  - "与设备无关的绘制"
  - "绘图, 设备上下文"
  - "绘图, 直接到窗口中"
  - "绘图, 在鼠标和设备上下文中"
  - "EndPaint 方法"
  - "框架窗口 [C++], 设备上下文"
  - "GDI 对象 [C++], 设备上下文"
  - "GetDC 方法和 CClientDC 类"
  - "图形对象, 设备上下文"
  - "图元文件和设备上下文"
  - "鼠标 [C++], 绘制和设备上下文"
  - "OnPrepareDC 方法"
  - "绘制和设备上下文"
  - "打印机 [C++], 设备上下文"
  - "ReleaseDC 方法"
  - "用户界面 [C++], 设备上下文"
  - "窗口 [C++], 和设备上下文"
  - "窗口 [C++], 直接绘制到"
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 设备上下文
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

设备上下文是包含有关一个设备的绘图特性的 Windows 数据结构信息 \(如显示或打印机。  所有绘制调用通过设备上下文对象调用，封装用于绘制直线、形状和文本 Windows API。  设备上下文允许窗口中设备无关的图形。  设备上下文可用于绘制到屏幕，打印机，或者为元文件。  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md) 对象在设备上下文封装，调用 `BeginPaint` 函数，然后绘制，然后调用 `EndPaint` 函数的"公共思路。  `CPaintDC` 构造函数调用 `BeginPaint`，而且，析构函数调用 `EndPaint`。  简化的进程是 [CDC](../mfc/reference/cdc-class.md) 创建对象，然后绘制，销毁 `CDC` 对象。  在框架中，即使此进程中自动化。  具体而言，`OnDraw` 函数传递 `CPaintDC` 已经准备 \(通过 `OnPrepareDC`\)，因此，对它。  框架销毁它，并且基础设备上下文释放到若返回的窗口可以从调用 `OnDraw` 函数。  
  
 [CClientDC](../mfc/reference/cclientdc-class.md) 对象封装与表示窗口的某些工作区的设备上下文配合使用。  `CClientDC` 构造函数调用 `GetDC` 函数和析构函数调用 `ReleaseDC` 函数。  [CWindowDC](../mfc/reference/cwindowdc-class.md) 对象封装表示整个窗口的与设备上下文，包括其帧。  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md) 对象封装了绘制到 Windows 元文件。  与 `CPaintDC` 相反传递到 `OnDraw`，您必须在调用 [OnPrepareDC](../Topic/CView::OnPrepareDC.md)。  
  
## 鼠标绘制  
 框架中的大多数 \(因此大多数设备上下文计划绘制工作 \- 视图中的 `OnDraw` 成员函数。  但是，可以用于其他目的仍使用设备上下文对象。  例如，为视图的鼠标移动提供跟踪反馈，需要直接介绍视图，而无需等待调用 `OnDraw`。  
  
 在这种情况下，可以使用 [CClientDC](../mfc/reference/cclientdc-class.md) 设备上下文对象引入直接视图。  
  
### 您想进一步了解什么？  
  
-   [\<caps:sentence id\="tgt22" sentenceid\="a12b51e88715aef1e34dc9b8f4447117" class\="tgtSentence"\>设备上下文 \(定义\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd183553)  
  
-   [在视图](../mfc/drawing-in-a-view.md)  
  
-   [通过视图解释用户输入](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [\<caps:sentence id\="tgt25" sentenceid\="f3dbb554cb14503827bf0ebda53953d7" class\="tgtSentence"\>直线和曲线。\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd145028)  
  
-   [\<caps:sentence id\="tgt26" sentenceid\="365f749101c5eabc8b3be48de1dc3d6b" class\="tgtSentence"\>实心形状\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd162714)  
  
-   [\<caps:sentence id\="tgt27" sentenceid\="dc86a6302992c2d9f64d0fc6a8cfef75" class\="tgtSentence"\>字体和文本\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd144819)  
  
-   [\<caps:sentence id\="tgt28" sentenceid\="62848e3ce5804aa985513a7922ff87b2" class\="tgtSentence"\>Colors\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd183450)  
  
-   [\<caps:sentence id\="tgt29" sentenceid\="ee85800dfcba9a5bdf11f101e1bbadeb" class\="tgtSentence"\>坐标系和转换\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd183475)  
  
## 请参阅  
 [窗口对象](../mfc/window-objects.md)