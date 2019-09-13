---
title: 命令和控件通知的处理程序
ms.date: 11/04/2016
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
ms.openlocfilehash: 43b6a517b680a5f6ff092337fbf3d90dd0115dd7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907969"
---
# <a name="handlers-for-commands-and-control-notifications"></a>命令和控件通知的处理程序

命令或控件通知消息没有默认的处理程序。 因此，您将仅受为这些消息类别命名处理程序的约定约束。 当您将命令或控件通知映射到处理程序时，[类向导](reference/mfc-class-wizard.md)将基于命令 ID 或控件通知代码建议一个名称。 您可以接受建议的名称、更改或替换该名称。

约定建议您按照处理程序表示的用户界面对象的两个类别为其命名。 因此，可能为“编辑”菜单上的“剪贴”命令对应的处理程序命名

[!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

由于 Cut 命令通常在应用程序中实现，因此框架会将 Cut 命令的命令 ID 预定义为**ID_EDIT_CUT**。 有关所有预定义命令 ID 的列表，请参阅 AFXRES.H 文件。 有关详细信息，请参阅[标准命令](../mfc/standard-commands.md)。

此外，约定建议从标记为 "我的按钮" 的按钮获取**BN_CLICKED**通知消息的处理程序。

[!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

你可以为此命令分配 ID **IDC_MY_BUTTON** ，因为它等效于特定于应用程序的用户界面对象。

所有消息类别不采用参数也不返回值。

## <a name="see-also"></a>请参阅

[声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)
