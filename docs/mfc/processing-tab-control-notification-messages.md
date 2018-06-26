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
ms.openlocfilehash: 462d9177b1f6300eb356d052cbdfff3b85db86a1
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928057"
---
# <a name="processing-tab-control-notification-messages"></a>处理选项卡控件通知消息
根据用户单击选项卡或按钮、 选项卡控件 ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) 将通知消息发送到其父窗口。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户单击选项卡，你可能想要预设之前显示页上的控件数据。  
  
 从选项卡控件视图或对话框类中的进程 WM_NOTIFY 消息。 使用属性窗口创建[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)通过 switch 语句的处理程序函数基于正在处理的通知消息。 选项卡控件可以向其父窗口发送通知的列表，请参阅**通知**部分[选项卡控件引用](http://msdn.microsoft.com/library/windows/desktop/bb760548)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控件](../mfc/controls-mfc.md)

