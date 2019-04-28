---
title: 处理文档中的命令
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
ms.openlocfilehash: f3cce539d52bd04e97a6b5f84cbd833b05afb5bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240569"
---
# <a name="handling-commands-in-the-document"></a>处理文档中的命令

您的文档类也可能处理菜单项、 工具栏按钮或快捷键生成的某些命令。 默认情况下，`CDocument`处理保存并另存为命令文件菜单中，使用序列化。 也可能由文档的成员函数处理会影响的数据的其他命令。 例如，在随意画图程序中，类`CScribDoc`编辑清除所有命令，将删除所有当前存储在文档中的数据提供一个处理程序。 文档可以具有消息映射，但与不同的视图，文档不能处理标准 Windows 消息 — 仅**WM_COMMAND**消息或"命令"。

## <a name="see-also"></a>请参阅

[使用文档](../mfc/using-documents.md)
