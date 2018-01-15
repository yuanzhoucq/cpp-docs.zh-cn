---
title: "处理工具提示通知 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b7668420b849dc08215a4fc309edf86e9171462
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="handling-tool-tip-notifications"></a>处理工具提示通知
当指定`TBSTYLE_TOOLTIPS`样式，工具栏创建和管理工具提示控件。 工具提示是文本的一个小型弹出窗口，其中包含描述工具栏按钮行。 隐藏的工具提示，仅当用户将光标放在工具栏按钮上并停留约半秒钟时才显示出来。 在光标附近将显示工具提示。  
  
 显示的工具提示之前， **TTN_NEEDTEXT**通知消息发送到工具栏的所有者窗口，以检索按钮的描述性文本。 如果工具栏的所有者窗口处于`CFrameWnd`窗口中，工具提示显示而无需任何额外工作，因为`CFrameWnd`具有默认处理程序**TTN_NEEDTEXT**通知。 如果工具栏的所有者窗口不派生自`CFrameWnd`，如对话框框中或窗体视图，你必须将条目添加到所有者窗口的消息映射并提供消息映射中的通知处理程序。 到所有者窗口的消息映射条目如下所示：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]  
  
## <a name="remarks"></a>备注  
 `memberFxn`  
 文本需要此按钮时调用的成员函数。  
  
 请注意，工具提示的 id 始终为 0。  
  
 除了**TTN_NEEDTEXT**通知，工具提示控件可以发送以下通知，向 toolbar 控件：  
  
|通知|含义|  
|------------------|-------------|  
|**TTN_NEEDTEXTA**|工具提示控件需要 ASCII 文本 (仅适用于 Windows 95)|  
|**TTN_NEEDTEXTW**|工具提示控件需要 UNICODE 文本 (仅适用于 Windows NT)|  
|**TBN_HOTITEMCHANGE**|指示热 （突出显示） 的项已更改。|  
|**NM_RCLICK**|指示用户已右击一个按钮。|  
|**TBN_DRAGOUT**|指示用户已单击按钮并拖动指针离开按钮。 它允许应用程序实现拖动和删除从工具栏按钮。 在接收时此通知，应用程序将开始拖动和删除操作。|  
|**TBN_DROPDOWN**|指示用户已单击一个按钮，使用**TBSTYLE_DROPDOWN**样式。|  
|**TBN_GETOBJECT**|指示用户通过使用一个按钮移动指针**TBSTYLE_DROPPABLE**样式。|  
  
 示例处理程序函数和有关启用工具提示的详细信息，请参阅[工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

