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
ms.openlocfilehash: c313382b8be7538ba5bb465c6ba383955e414662
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619794"
---
# <a name="processing-header-control-notifications"></a>处理标题控件通知

在视图或对话框类中，使用[类向导](reference/mfc-class-wizard.md)为要处理的任何标头控件（[CHeaderCtrl](reference/cheaderctrl-class.md)）通知消息创建带有 switch 语句的[OnChildNotify](reference/cwnd-class.md#onchildnotify)处理程序函数（请参阅[将消息映射到函数](reference/mapping-messages-to-functions.md)）。 当用户单击或双击标题项、拖动项之间的分隔符，等等时，通知将发送到父窗口。

Windows SDK 中的[标头控件引用](/windows/win32/controls/header-control-reference)中列出了与标头控件关联的通知消息。

## <a name="see-also"></a>另请参阅

[使用 CHeaderCtrl](using-cheaderctrl.md)<br/>
[控件](controls-mfc.md)
