---
title: 命令和控件通知处理程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bda42393cd55b60ab787665b51957bb2f94c5df3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430051"
---
# <a name="handlers-for-commands-and-control-notifications"></a>命令和控件通知的处理程序

命令或控件通知消息没有默认的处理程序。 因此，您将仅受为这些消息类别命名处理程序的约定约束。 当您将命令或控件通知映射到处理程序时，“属性”窗口将基于命令 ID 或控件通知代码建议一个名称。 您可以接受建议的名称、更改或替换该名称。

约定建议您按照处理程序表示的用户界面对象的两个类别为其命名。 因此，可能为“编辑”菜单上的“剪贴”命令对应的处理程序命名

[!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

框架应用程序中，因此通常实现剪切命令，因为会作为剪切命令的命令 ID 预定义**ID_EDIT_CUT**。 有关所有预定义命令 ID 的列表，请参阅 AFXRES.H 文件。 有关详细信息，请参阅[标准命令](../mfc/standard-commands.md)。

此外，约定建议的处理程序**BN_CLICKED**可能名为通知消息从标签为"我的按钮"的按钮

[!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

您可能会将此命令的 ID **IDC_MY_BUTTON**因为等效于特定于应用程序的用户界面对象。

所有消息类别不采用自变量也不返回值。

## <a name="see-also"></a>请参阅

[声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)
