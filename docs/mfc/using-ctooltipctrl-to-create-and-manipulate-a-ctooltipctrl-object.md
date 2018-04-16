---
title: "使用 CToolTipCtrl 创建和操作 CToolTipCtrl 对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CToolTipCtrl
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da4c98e327d2d78050410e75869c894d73324281
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>使用 CToolTipCtrl 创建和操作 CToolTipCtrl 对象
下面是一个示例的[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)用法：  
  
### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>创建和操作 CToolTipCtrl  
  
1.  构造 `CToolTipCtrl` 对象。  
  
2.  调用[创建](../mfc/reference/ctooltipctrl-class.md#create)若要创建 Windows 工具提示公共控件并将其附加到`CToolTipCtrl`对象。  
  
3.  调用[AddTool](../mfc/reference/ctooltipctrl-class.md#addtool)与该工具提示控件注册工具，以便当光标位于工具上时显示工具提示中存储的信息。  
  
4.  调用[SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo)设置工具提示维护的工具的信息。  
  
5.  调用[SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect)设置工具的新边框。  
  
6.  调用[HitTest](../mfc/reference/ctooltipctrl-class.md#hittest)测试点以确定它是否位于给定工具的边框内，如果是这样，则检索有关工具的信息。  
  
7.  调用[GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount)检索的工具计数向工具提示控件注册。  
  
## <a name="see-also"></a>请参阅  
 [使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控件](../mfc/controls-mfc.md)

