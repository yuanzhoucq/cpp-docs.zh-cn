---
title: 处理标题控件通知
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
ms.openlocfilehash: f60a0c918476702881984f976b220130727cf4b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507948"
---
# <a name="processing-header-control-notifications"></a>处理标题控件通知

在视图或对话框类中, 使用属性窗口为要处理的任何标头控件 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 通知消息创建[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)处理程序函数和 switch 语句 (请参阅[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)). 当用户单击或双击标题项、拖动项之间的分隔符, 等等时, 通知将发送到父窗口。

Windows SDK 中的[标头控件引用](/windows/win32/controls/header-control-reference)中列出了与标头控件关联的通知消息。

## <a name="see-also"></a>请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
