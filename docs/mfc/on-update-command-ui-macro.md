---
title: ON_UPDATE_COMMAND_UI 宏
ms.date: 09/06/2019
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: ba5a48fabb9142c080e688e189e0983ad5ba2eda
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624052"
---
# <a name="on_update_command_ui-macro"></a>ON_UPDATE_COMMAND_UI 宏

若要将用户界面对象连接到命令目标对象中的命令更新处理程序，请打开**类视图**，然后右键单击要向其添加处理程序的类，然后选择 "**类向导**"。 在左侧列表中找到用户界面对象的 ID，然后在右窗格中选择 " **UPDATE_COMMAND_UI** "，然后单击 "**添加处理程序**"。 这会在类中创建处理程序函数并在消息映射中添加适当的条目。 有关详细信息，请参阅[将消息映射到函数](reference/mapping-messages-to-functions.md)。 可以在 "**消息**" 窗格中指定要处理的其他消息。

例如，若要在程序的 "编辑" 菜单中更新 "全部清除" 命令，请使用 "**类向导**" 在选定类中添加消息映射项，在类声明中添加调用的命令更新处理程序的函数声明 `OnUpdateEditClearAll` ，并在类的实现文件中添加空函数模板。 函数原型类似于这样：

[!code-cpp[NVC_MFCDocView#2](codesnippet/cpp/on-update-command-ui-macro_1.h)]

与所有处理程序一样，函数声明显示**afx_msg**关键字。 与所有更新处理程序一样，它采用一个自变量（一个指向 `CCmdUI` 对象的指针）。

## <a name="see-also"></a>另请参阅

[如何：更新用户界面对象](how-to-update-user-interface-objects.md)
