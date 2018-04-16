---
title: "对话栏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d9d7319f23741f683e31cfd683a8ebd6d25acdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-bars"></a>对话栏
对话栏是一个工具栏，一种类型的[控件条](../mfc/control-bars.md)可以包含任何类型的控件。 因为它具有无模式对话框的特征[CDialogBar](../mfc/reference/cdialogbar-class.md)对象提供更强大的工具栏。  
  
 工具栏和 `CDialogBar` 对象之间有一些主要差异。 `CDialogBar` 对象是从可以借助 Visual C++ 对话框编辑器创建的、可包含各种 Windows 控件的对话框模板资源创建的。 用户可以在控件之间进行切换。 您可以指定对齐样式，以将对话栏与父框架窗口的任何部分对齐，甚至可以在调整父窗口大小时将其留在原来的位置。 下图演示了带有各种控件的对话栏。  
  
 ![VC 对话栏](../mfc/media/vc378t1.gif "vc378t1")  
对话栏  
  
 在其他方面，使用 `CDialogBar` 对象与使用无模式对话框类似。 使用对话框编辑器来设计和创建对话框资源。  
  
 对话栏的优点之一是，它们可以包括除按钮之外的控件。  
  
 虽然从 `CDialog` 派生您自己的对话框类很正常，但您通常不会为对话栏派生您自己的类。 对话栏是扩展到一个主窗口以及任何对话栏控件通知消息，如**BN_CLICKED**或**EN_CHANGE**，将发送到对话栏的主窗口的父级。  
  
## <a name="see-also"></a>请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)   
 [示例](../visual-cpp-samples.md)

