---
title: ON_UPDATE_COMMAND_UI 宏
ms.date: 11/04/2016
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: 986bc4f12223048a20f88da5d164b24dc1c08ace
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261175"
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI 宏

使用**属性**窗口连接到命令目标对象中的命令更新处理程序的用户界面对象。 它自动将连接到 ON_UPDATE_COMMAND_UI 宏的用户界面对象的 ID，并将处理更新的对象中创建一个处理程序。 请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)有关详细信息。

例如，若要更新程序的编辑菜单中的全部清除命令，使用**属性**窗口，以在所选的类的命令更新处理程序的函数声明中添加一个消息映射条目调用`OnUpdateEditClearAll`类中声明，以及类的实现文件中的空函数模板。 函数原型类似于这样：

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

像所有处理程序，该函数将显示**afx_msg**关键字。 与所有更新处理程序一样，它采用一个自变量（一个指向 `CCmdUI` 对象的指针）。

## <a name="see-also"></a>请参阅

[如何：更新用户界面对象](../mfc/how-to-update-user-interface-objects.md)
