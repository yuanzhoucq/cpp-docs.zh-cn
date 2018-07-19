---
title: 处理标题控件通知 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a0fe657089c33679cf8d18f95268a70335804c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348886"
---
# <a name="processing-header-control-notifications"></a>处理标题控件通知
在视图或对话框类中，使用属性窗口创建[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)通过 switch 语句的任何标头控件的处理程序函数 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 到所需的通知消息处理 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。 用户单击或双击标头项，项，依次类推之间的分隔符拖动时，将向父窗口发送通知。  
  
 中列出了与标头控件关联的通知消息[标头控件引用](http://msdn.microsoft.com/library/windows/desktop/bb775239)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控件](../mfc/controls-mfc.md)

