---
title: 设置热键 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3987ddee98ae35e02a181e38cd71f181801aeb61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="setting-a-hot-key"></a>设置热键
你的应用程序可以使用提供的热键的信息 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 中通过两种方式控件：  
  
-   设置用于通过发送激活非子窗口的全局热键[WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284)消息发送到窗口将激活。  
  
-   通过调用 Windows 函数设置线程特定的热键[RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控件](../mfc/controls-mfc.md)

