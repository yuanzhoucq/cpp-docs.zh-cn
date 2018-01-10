---
title: "设置工具提示控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 406e35b6ab694ca972d4cd6add0dcca7586e5005
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="settings-for-the-tool-tip-control"></a>工具提示控件的设置
可以将工具提示控件 ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) 设置为活动或非活动。 如果将其设置为活动状态，当光标位于工具上时，将显示工具提示控件。 如果将其设置为非活动状态，即使光标位于工具上时，也不会显示工具提示控件。 调用 [Activate](../mfc/reference/ctooltipctrl-class.md#activate) 以激活或停用工具提示控件。  
  
 无论工具提示控件的所有者窗口处于活动还是非活动状态，均可以在光标位于工具上时，通过使用 **TTS_ALWAYSTIP** 样式来将活动的工具提示设置为显示工作提示。 如果不使用此样式，工具提示控件将在工具的所有者窗口处于活动状态时显示，当其处于非活动状态时则不显示。  
  
 大多数应用程序均有工具栏，工具栏中的工具与菜单命令对应。 对于此类工具，工具提示控件可以方便地显示与相应菜单项相同的文本。 系统自动去除的所有字符串传递给工具提示控件，与号 (&) 加速器字符，除非控件具有**TTS_NOPREFIX**样式。  
  
## <a name="see-also"></a>请参阅  
 [使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控件](../mfc/controls-mfc.md)

