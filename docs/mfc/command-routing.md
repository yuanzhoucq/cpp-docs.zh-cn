---
title: 命令传送
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
ms.openlocfilehash: ae9741a66e944b60dc38c1366353e43977e1ee7a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278388"
---
# <a name="command-routing"></a>命令传送

你使用命令的职责限于在命令及其处理程序函数间建立消息映射连接，也是你使用“属性”窗口的任务。 还必须编写大部分命令处理程序。

Windows 消息通常发送到主框架窗口中，但命令消息则传送到其他对象。 框架通过命令目标对象的标准顺序传送命令，这些对象中应包含命令的处理程序。 每个命令目标对象检查其消息映射，看看是否能处理传入的消息。

不同的命令目标类检查其自身不同时间的消息映射。 通常情况下，类将命令传送到其他某些对象，让对象首次尝试处理命令。 如果没有对象处理该命令，原始类将检查其自己的消息映射。 然后，如果它自己无法提供处理程序，则可将命令传送到更多的命令目标。 下表 [标准命令传送](#_core_standard_command_route) 显示了每个类如何构成此顺序。 命令目标传送命令的一般顺序是：

1. 到其当前活动子命令目标对象。

1. 到自身。

1. 到其他命令目标。

如何为您的处理程序中响应命令的作用的路由机制比较是昂贵，路由的成本较低。 请记住，仅当用户与用户界面对象交互时，框架才生成命令。

### <a name="_core_standard_command_route"></a> 标准命令传送

|当此类型的对象收到命令时。 . .|它给自身和其他命令目标对象一个机会以此顺序处理命令：|
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
|MDI 框架窗口 (`CMDIFrameWnd`)|1.活动 `CMDIChildWnd`<br />2.此框架窗口<br />3.应用程序（`CWinApp` 对象）|
|文档框架窗口（`CFrameWnd`、 `CMDIChildWnd`）|1.活动视图<br />2.此框架窗口<br />3.应用程序（`CWinApp` 对象）|
|视图|1.此视图<br />2.附加到视图的文档|
|Document|1.此文档<br />2.附加到文档的文档模板|
|对话框|1.此对话框<br />2.拥有对话框的窗口<br />3.应用程序（`CWinApp` 对象）|

如果前述表第二列中带编号的项提到其他对象（例如文档），请参见第一列中相应的项。 例如，当你在第二列中看到视图将命令转发到其文档，则参阅第一列中的“文档”项了解进一步的传送。

## <a name="see-also"></a>请参阅

[框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)
