---
title: 线程特定的热键 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdd6cf2f2bb76c30f4cc00d75eb55d7d2c01fa7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380414"
---
# <a name="thread-specific-hot-keys"></a>线程特定的热键
应用程序设置线程特定的热键 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 通过使用 Windows **RegisterHotKey**函数。 当用户按线程特定的热键时，Windows 文章[WM_HOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646279)到特定线程的消息队列的开头的消息。 **WM_HOTKEY**消息包含的虚拟键代码、 位移状态和用户定义的特定的热键按下的 ID。 有关标准虚拟键代码的列表，请参见 Winuser.h。 此方法的详细信息，请参阅[RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
 请注意，位移状态标志的调用中使用**RegisterHotKey**不是由返回相同[GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)成员函数; 你将需要调用之前，转换这些标志**RegisterHotKey**。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控件](../mfc/controls-mfc.md)

