---
title: "设置热键 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9cd52fca8415196fc1393cc49fe7830f6ca2cfd1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="setting-a-hot-key"></a>设置热键
你的应用程序可以使用提供的热键的信息 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 中通过两种方式控件：  
  
-   设置用于通过发送激活非子窗口的全局热键[WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284)消息发送到窗口将激活。  
  
-   通过调用 Windows 函数设置线程特定的热键[RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控件](../mfc/controls-mfc.md)

