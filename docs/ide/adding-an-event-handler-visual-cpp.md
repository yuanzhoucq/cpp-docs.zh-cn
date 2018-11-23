---
title: 添加事件处理程序
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.eventhandler.overview
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
- event handler wizard [C++]
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
ms.openlocfilehash: 8e6b2511b00b7f949718e5b0d9fd793ac53d0d8b
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694512"
---
# <a name="add-an-event-handler"></a>添加事件处理程序

从资源编辑器中，可以使用[事件处理程序向导](#event-handler-wizard)，为对话框控件添加新的事件处理程序或编辑现有的事件处理程序。

可以使用[属性窗口](/visualstudio/ide/reference/properties-window)向实现对话框的类添加事件。 要将事件添加到除对话框类以外的类，请使用事件处理程序向导。

**向对话框控件添加事件处理程序：**

1. 双击[资源视图](../windows/resource-view-window.md)中的对话框资源，打开包含[对话框编辑器](../windows/dialog-editor.md)中的控件的对话框资源。

1. 右键双击想要为其处理通知事件的控件。

1. 在快捷菜单上，选择“添加事件处理程序”，显示事件处理程序向导。

1. 选择“消息类型”框中的事件，以添加到在“类列表”框中选中的类。

1. 接受“函数处理程序名称”框中的默认名称或提供你所选的名称。

1. 选择“添加并编辑”，将事件处理程序添加到项目，并在新函数处打开文本编辑器，添加适当的事件处理程序代码。

   如果所选的消息类型已有所选类的事件处理程序，则“添加并编辑”不可用，而“编辑代码”可用。 选择“编辑代码”，在现有函数处打开文本编辑器。

或者，可以从[属性窗口](/visualstudio/ide/reference/properties-window)添加事件处理程序。 有关详细信息，请参阅[为对话框控件添加事件处理程序](../windows/adding-event-handlers-for-dialog-box-controls.md)。

## <a name="in-this-section"></a>本节内容

- [事件处理程序向导](#event-handler-wizard)

## <a name="event-handler-wizard"></a>事件处理程序向导

此向导将对话框控件的事件处理程序添加到所选的类。 如果从[属性窗口](/visualstudio/ide/reference/properties-window)添加事件处理程序，可以仅将其添加到实现对话框的类。 有关详细信息，请参阅[为对话框控件添加事件处理程序](../windows/adding-event-handlers-for-dialog-box-controls.md)。

- **命令名**

  标识已添加事件处理程序的所选控件。 此框不可用。

- **消息类型**

  为所选控件显示当前可能的消息处理程序列表。

- **函数处理程序名称**

  显示已添加用于处理事件的函数的名称。 默认情况下，该名称基于消息类型和命令，前缀为 `On`。 例如，对于名为 `IDC_BUTTON1` 的按钮，消息类型 `BN_CLICKED` 显示的函数处理程序名为 `OnBnClickedButton1`。

- **类列表**

  显示可将事件处理程序添加到其中的可用类。 所选对话框的类显示为红色。

- **处理程序说明**

  为在“消息类型”对话框中选中的项提供说明。 此框不可用。

- **添加和编辑**

  将消息处理程序添加到选定的类或对象。 它还会为新函数打开文本编辑器，以便可以为控件通知添加处理程序代码。

- **编辑代码**

  为所选的现有函数打开文本编辑框，以便可以添加或编辑控件通知处理程序代码。
