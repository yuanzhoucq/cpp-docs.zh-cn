---
title: Rebar 控件使用对话栏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- WM_EX_TRANSPARENT
dev_langs:
- C++
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47894c14e3b3d694847f94e7f981c9397383e598
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>对 Rebar 控件使用对话栏
中所述[Rebar 控件和带区](../mfc/rebar-controls-and-bands.md)，每个带区可以包含只有一个子窗口 （或控件）。 如果你想要具有多个每个带区的子窗口，这可能是一个限制。 方便的解决方法是具有多个控件创建对话框栏资源，然后将 rebar 带区 （包含对话栏） 添加到 rebar 控件。  
  
 通常情况下，如果你想要显示为透明的对话框栏带区，则将设置**WS_EX_TRANSPARENT**扩展对话栏对象的样式。 但是，因为**WS_EX_TRANSPARENT**具有正确绘制对话栏的背景存在一些问题，你将需要执行一些额外的操作，以实现所需的效果。  
  
 以下过程详细介绍实现而不使用透明度所必需的步骤**WS_EX_TRANSPARENT**扩展样式。  
  
### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>若要在 rebar 带区中实现透明对话栏  
  
1.  使用[添加类对话框](../mfc/reference/adding-an-mfc-class.md)，添加一个新类 (例如， `CMyDlgBar`) 实现你对话栏对象。  
  
2.  添加的处理程序`WM_ERASEBKGND`消息。  
  
3.  在新的处理程序，修改现有的代码，以匹配以下示例：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]  
  
4.  添加的处理程序`WM_MOVE`消息。  
  
5.  在新的处理程序，修改现有的代码，以匹配以下示例：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]  
  
 新的处理程序被转发模拟对话栏的透明度`WM_ERASEBKGND`向父窗口发送消息以及强制重新绘制，每次移动对话栏对象。  
  
## <a name="see-also"></a>请参阅  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控件](../mfc/controls-mfc.md)

