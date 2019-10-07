---
title: 处理扩展组合框控件中的通知消息
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 044cef644f746f7cb70944805882bd8e2f2806b4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908099"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>处理扩展组合框控件中的通知消息

当用户与扩展组合框进行交互时，控件 (`CComboBoxEx`) 会将通知消息发送到其父窗口（通常是一个视图或对话框对象）。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户激活下拉列表或单击该控件的编辑框时，将发送 CBEN_BEGINEDIT 通知。

使用[类向导](reference/mfc-class-wizard.md)将通知处理程序添加到要实现的那些消息的父类。

下表介绍了由扩展组合框控件发送的各种通知。

- CBEN_BEGINEDIT 用户激活下拉列表或单击控件的编辑框时发送。

- CBEN_DELETEITEM 在删除项时发送。

- CBEN_DRAGBEGIN 当用户开始拖动控件编辑部分中显示的项的图像时发送。

- 当用户结束编辑框中的某个操作或从控件的下拉列表中选择某项时，CBEN_ENDEDIT 发送。

- CBEN_GETDISPINFO 发送以检索有关回调项的显示信息。

- CBEN_INSERTITEM 在控件中插入新项时发送。

## <a name="see-also"></a>请参阅

[使用 CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[控件](../mfc/controls-mfc.md)
