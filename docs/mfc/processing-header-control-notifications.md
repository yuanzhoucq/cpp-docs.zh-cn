---
title: 处理标题控件通知 |Microsoft Docs
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
ms.openlocfilehash: fd7c6fa8a85aee06aca3b1bf804a06df428e82cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387752"
---
# <a name="processing-header-control-notifications"></a>处理标题控件通知

在视图或对话框类中，使用属性窗口创建[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)处理程序函数与 switch 语句的任何标头控件 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 到所需的通知消息处理 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。 当用户单击或双击一个标头项，项，依次类推之间的分隔符的拖动时，将向父窗口发送通知。

与标头控件关联的通知消息中列出[标头控件引用](https://msdn.microsoft.com/library/windows/desktop/bb775239)Windows SDK 中。

## <a name="see-also"></a>请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

