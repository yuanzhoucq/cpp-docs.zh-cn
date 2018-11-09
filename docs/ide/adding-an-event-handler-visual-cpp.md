---
title: 添加事件处理程序 (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
ms.openlocfilehash: d9256fca75b6980d87382bbeb794fa90b89f37c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512432"
---
# <a name="adding-an-event-handler-visual-c"></a>添加事件处理程序 (Visual C++)

从资源编辑器中，可以使用[事件处理程序向导](../ide/event-handler-wizard.md)，为对话框控件添加新的事件处理程序或编辑现有的事件处理程序。

可以使用[属性窗口](/visualstudio/ide/reference/properties-window)向实现对话框的类添加事件。 如果想将事件添加到除对话框类以外的类，请使用事件处理程序向导。

### <a name="to-add-an-event-handler-to-a-dialog-box-control"></a>向对话框控件添加事件处理程序

1. 双击[资源视图](../windows/resource-view-window.md)中的对话框资源，打开包含[对话框编辑器](../windows/dialog-editor.md)中的控件的对话框资源。

1. 右键双击想要为其处理通知事件的控件。

1. 在快捷菜单上，单击“添加事件处理程序”，显示事件处理程序向导。

1. 选择“消息类型”框中的事件，以添加到在“类列表”框中选中的类。

1. 接受“函数处理程序名称”框中的默认名称或提供你所选的名称。

1. 单击“添加并编辑”，将事件处理程序添加到项目，并在新函数处打开文本编辑框，添加适当的事件处理程序代码。

   如果所选的消息类型已有所选类的事件处理程序，则“添加并编辑”不可用，而“编辑代码”可用。 单击“编辑代码”，在现有函数处打开文本编辑框。

或者，可以从[属性窗口](/visualstudio/ide/reference/properties-window)添加事件处理程序。 请参阅[添加对话框控件的事件处理程序](../windows/adding-event-handlers-for-dialog-box-controls.md)，获取详细信息。

## <a name="see-also"></a>请参阅

[用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[添加类](../ide/adding-a-class-visual-cpp.md)<br>
[添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)<br>
[添加成员函数](../ide/adding-a-member-function-visual-cpp.md)<br>
[MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[导航类结构](../ide/navigating-the-class-structure-visual-cpp.md)