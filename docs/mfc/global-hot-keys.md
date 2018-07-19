---
title: 全局热键 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd597271d949770ec1a5871cad3ea7be0004e288
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344225"
---
# <a name="global-hot-keys"></a>全局热键
全局热键是与特定的非子窗口相关联。 它允许用户激活系统的任何部分中的窗口。 应用程序通过发送设置特定窗口的全局热键[WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284)消息发送到该窗口。 例如，如果`m_HotKeyCtrl`是[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)对象和`pMainWnd`是一个指针，到窗口，以在按下热键时被激活，可以使用下面的代码，以将热键控件中指定相关联指向窗口`pMainWnd`。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]  
  
 每当用户按下的全局热键，指定的窗口接收[WM_SYSCOMMAND](http://msdn.microsoft.com/library/windows/desktop/ms646360)指定的消息**SC_HOTKEY**作为命令的类型。 此消息还会激活接收的窗口。 由于此消息不包括已按下的确切键上的任何信息，使用此方法不允许区分可能附加到相同的窗口的不同热键。 热键之前发送的应用程序就保持有效**WM_SETHOTKEY**退出。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控件](../mfc/controls-mfc.md)

