---
title: 处理文档中的命令 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a1e848827b46d40c1ec39f2af4788e6957932c5
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929107"
---
# <a name="handling-commands-in-the-document"></a>处理文档中的命令
您的文档类可能还会处理菜单项、 工具栏按钮或快捷键生成的某些命令。 默认情况下，`CDocument`处理保存和另存为命令上的文件菜单中，使用序列化。 也可能由成员函数的文档处理的其他命令的影响的数据。 例如，在 Scribble 程序中，类`CScribDoc`对于编辑清除所有命令，将删除所有当前存储在文档中的数据提供一个处理程序。 文档可以具有消息映射，但不同视图，文档无法处理标准 Windows 消息 — 仅**WM_COMMAND**消息或"命令。"  
  
## <a name="see-also"></a>请参阅  
 [使用文档](../mfc/using-documents.md)

