---
title: "设置 CStatusBarCtrl 对象的模式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CStatusBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBarCtrl 类, 简单和非简单模式"
  - "IsSimple 方法, using"
  - "非简单模式和状态栏控件"
  - "SetSimple 方法"
  - "简单模式和状态栏控件"
  - "状态栏控件, 简单和非简单模式"
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 设置 CStatusBarCtrl 对象的模式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CStatusBarCtrl` 对象有两种：简单和 nonsimple。  可能在大部分情况下，控件状态栏以及文本和图标或图标。将一个或多个部件。  这称为 nonsimple 模式。  有关该模式的更多信息，请参见 [初始化 CStatusBarCtrl 对象的部分](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md)。  
  
 但是，您只需显示单行文本的情况。  在这种情况下，" Simple 模式对于需要即可。  若要更改 `CStatusBarCtrl` 对象的模式。简单，请调用成员函数。[SetSimple](../Topic/CStatusBarCtrl::SetSimple.md) 后状态栏在简单控件模式中，通过调用 **SetText** 成员函数设置文本，将 255 作为 **nPane** 参数的值。  
  
 可以使用 [IsSimple](../Topic/CStatusBarCtrl::IsSimple.md) 函数确定模式 `CStatusBarCtrl` 对象中。  
  
> [!NOTE]
>  如果状态栏对象从 nonsimple 更改为简单反之亦然，窗口立即重新绘制，并且，如果适用，将所有已定义部分的自动还原。  
  
## 请参阅  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控件](../mfc/controls-mfc.md)