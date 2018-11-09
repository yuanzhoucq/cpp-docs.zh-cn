---
title: 事件处理程序向导
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
ms.openlocfilehash: e48d995aed0c59cc4ba7b645706448b5c3618b4a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654163"
---
# <a name="event-handler-wizard"></a>事件处理程序向导

此向导将对话框控件的事件处理程序添加到所选的类。 如果从[属性窗口](/visualstudio/ide/reference/properties-window)添加事件处理程序，可以仅将其添加到实现对话框的类。 请参阅[添加对话框控件的事件处理程序](../windows/adding-event-handlers-for-dialog-box-controls.md)，获取详细信息。

- **命令名**

   标识已添加事件处理程序的所选控件。 此框不可用。

- **消息类型**

   为所选控件显示当前可能的消息处理程序列表。

- **函数处理程序名称**

   显示已添加为处理事件的函数的名称。 在默认情况下，此名称基于消息类型和命令，前面加上“On”。 例如，对于名为 `IDC_BUTTON1` 的按钮，消息类型 `BN_CLICKED` 显示的函数处理程序名为 `OnBnClickedButton1`。

- **类列表**

   显示可将事件处理程序添加到其中的可用类。 所选对话框的类显示为红色。

- **处理程序说明**

   为在“消息类型”对话框中选中的项提供说明。 此框不可用。

- **添加和编辑**

   向所选的类或对象添加消息处理程序，然后为新函数打开文本编辑框，以便添加控件通知处理程序代码。

- **编辑代码**

   为所选的现有函数打开文本编辑框，以便可以添加或编辑控件通知处理程序代码。

## <a name="see-also"></a>请参阅

[添加事件处理程序](../ide/adding-an-event-handler-visual-cpp.md)