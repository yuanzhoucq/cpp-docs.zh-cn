---
title: 处理选项卡控件通知消息 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce59bfe298798d4574bf158998e989c4a6af62c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="processing-tab-control-notification-messages"></a>处理选项卡控件通知消息
根据用户单击选项卡或按钮、 选项卡控件 ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) 将通知消息发送到其父窗口。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户单击选项卡，你可能想要预设之前显示页上的控件数据。  
  
 进程**WM_NOTIFY**从选项卡控件视图或对话框类中的消息。 使用属性窗口创建[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)通过 switch 语句的处理程序函数基于正在处理的通知消息。 选项卡控件可以向其父窗口发送通知的列表，请参阅**通知**部分[选项卡控件引用](http://msdn.microsoft.com/library/windows/desktop/bb760548)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控件](../mfc/controls-mfc.md)

