---
title: 将消息映射到函数
ms.date: 09/06/2019
f1_keywords:
- vc.codewiz.mapping.msg.function
helpviewer_keywords:
- Windows messages [MFC], adding message handlers
- message maps [MFC], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
ms.openlocfilehash: 4a76e28bddda0ad3385ab2110e201d652c0623df
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907865"
---
# <a name="mapping-messages-to-functions"></a>将消息映射到函数

使用[类向导](mfc-class-wizard.md)可以将消息处理程序（MFC 用户界面类的成员函数）绑定到应用程序资源生成的消息。 它们使用[MFC 消息映射](../../mfc/messages-and-commands-in-the-framework.md)来创建绑定。

当你使用类视图创建从一个框架类派生的新类时，它会自动在你指定的标头（.h）和实现（.cpp）文件中放置一个完整的功能类。

> [!NOTE]
>  若要添加不处理消息的新类，请在文本编辑器中直接创建类。

### <a name="to-define-or-remove-a-message-handler-using-the-class-wizard"></a>使用类向导定义或移除消息处理程序

1. 在**类视图**中，右键单击类。

1. 在上下文菜单中，选择 "[类向导](mfc-class-wizard.md)"。

## <a name="see-also"></a>请参阅

[MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[添加类](../../ide/adding-a-class-visual-cpp.md)<br/>
[添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[导航类结构](../../ide/navigate-code-cpp.md)
