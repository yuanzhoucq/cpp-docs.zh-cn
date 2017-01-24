---
title: "CReBar 与 CReBarCtrl | Microsoft Docs"
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
  - "CReBar"
  - "CReBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReBar 类, 与 CReBarCtrl"
  - "GetReBarCtrl 类"
  - "rebar 控件, CReBarCtrl 类"
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CReBar 与 CReBarCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供了两类创建 rebar:\(打包 Windows 公共控件 API\) 的 [CReBar](../mfc/reference/crebar-class.md) 和 [CReBarCtrl](../mfc/reference/crebarctrl-class.md)。  **CReBar** 提供所有 rebar 公共控件的功能，因此，在处理很多必需的公共控件设置和结构中的。  
  
 如果不打算将 MFC rebar 结构，`CReBarCtrl` 是 Win32 rebar 控件的包装类，并可能较为容易实现。  如果计划使用 `CReBarCtrl` 和集成 MFC rebar结构，必须小心注意其他的传达rebar控件处理到 MFC。  此通信不非常困难；但是，它是不必要的额外工作，使用 **CReBar**。  
  
 Visual C\+\+ 提供两种rebar使用公共控件。  
  
-   使用 **CReBar**，rebar 创建，然后调用 [CReBar::GetReBarCtrl](../Topic/CReBar::GetReBarCtrl.md) 获取对 `CReBarCtrl` 成员函数的访问权限。  
  
    > [!NOTE]
    >  `CReBar::GetReBarCtrl` 是要转换 rebar 对象的 **this** 指针成员函数的内联。  这意味着，在运行时，将调用函数没有开销。  
  
-   使用 [CReBarCtrl](../mfc/reference/crebarctrl-class.md)，rebar 构造函数创建。  
  
 任一方法允许您为rebar控件的成员函数的访问。  当您调用 `CReBar::GetReBarCtrl`时，它返回对 `CReBarCtrl` 对象的引用，以便可以使用为设置成员函数。  使用 **CReBar**，请参见 [CReBar](../mfc/reference/crebar-class.md) 有关构造和 rebar 创建的信息。  
  
## 请参阅  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控件](../mfc/controls-mfc.md)