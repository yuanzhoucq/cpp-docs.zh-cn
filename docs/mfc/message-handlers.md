---
title: 消息处理程序
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
ms.openlocfilehash: 25805187f88c5423ea41cd7cbe346e44e7d7d36a
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907462"
---
# <a name="message-handlers"></a>消息处理程序

在 MFC 中，专用*处理程序*函数处理每个单独的消息。 消息处理程序函数是类的成员函数。 本文档使用术语*消息处理程序成员函数*、*消息处理程序函数*、*消息处理*程序和*处理程序*。 某些类型的消息处理程序也称为“命令处理程序”。

编写消息处理程序时，您的大部分精力都将耗在编写框架应用程序上。 本文章系列介绍消息处理机制的工作方式。

消息的处理程序执行的操作会执行您想要执行的任何操作来响应该消息。 您可以使用类的[类向导](reference/mfc-class-wizard.md)创建处理程序，然后使用源代码编辑器填写处理程序的代码。

您可以使用 Microsoft Visual C++ 和 MFC 的所有工具编写处理程序。 有关所有类的列表，请参阅*MFC 参考*中的类库[概述](../mfc/class-library-overview.md)。

## <a name="see-also"></a>请参阅

[框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)
