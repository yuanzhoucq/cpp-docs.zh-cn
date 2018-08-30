---
title: 线程特定的热键 |Microsoft Docs
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
ms.openlocfilehash: f480b293e9c57e7fa189c6427ab39147681cfdaf
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206855"
---
# <a name="thread-specific-hot-keys"></a>线程特定的热键
应用程序设置特定于线程的热键 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 通过使用 Windows`RegisterHotKey`函数。 当用户按特定于线程的热键时，Windows 将发布[WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey)到特定线程的消息队列的开头的消息。 WM_HOTKEY 消息包含虚拟键代码、 位移状态和用户定义的按下了特定的热键的 ID。 标准虚拟键代码的列表，请参见 Winuser.h。 此方法的详细信息，请参阅[RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
 请注意，位移状态标志对调用中使用`RegisterHotKey`不是返回的相同[GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)成员函数; 您必须转换之前，调用这些标志`RegisterHotKey`。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控件](../mfc/controls-mfc.md)

