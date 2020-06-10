---
title: 重写标准命令传送
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 680b185f8d68a834862bc0fe14bf6e7984effd65
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617727"
---
# <a name="overriding-the-standard-command-routing"></a>重写标准命令传送

在您必须实现标准框架路由的某个变体的罕见情况下，您可重写它。 意图是通过重写这些类中的 `OnCmdMsg` 来更改一个或多个类的路由。 如此做：

- 在打乱到非默认对象的传递顺序的类中。

- 在新的非默认对象或它可能依次将命令传递到的命令目标中。

如果您将某个新的对象插入路由，则其类必须是命令目标类。 在 `OnCmdMsg` 的重写版本中，请确保调用您要重写的版本。 有关示例，请参阅 MFC 参考中的类的[OnCmdMsg](reference/ccmdtarget-class.md#oncmdmsg)成员函数 `CCmdTarget` ，以及此类类中的*MFC Reference* `CView` 和和 `CDocument` 中提供的版本。

## <a name="see-also"></a>另请参阅

[框架如何调用处理程序](how-the-framework-calls-a-handler.md)
