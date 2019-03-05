---
title: 显示断言
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
ms.openlocfilehash: bb06b8f124180ed566ecf2c761deb359444fb019
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289983"
---
# <a name="displaying-assertions"></a>显示断言

如果客户端连接到你的服务似乎停止响应，服务可能已添加并显示一个消息框，您不能以查看。 你可以通过使用 Visual c + + 的调试器来调试代码确认这一点 (请参阅[使用任务管理器](../atl/using-task-manager.md)本部分前面)。

如果你确定你的服务显示一个消息框，您不能看到，您可能想要设置**允许服务与桌面交互**之前再次使用该服务的选项。 此选项是允许服务出现在桌面上显示的任何消息框的启动参数。 若要设置此选项，打开服务控制面板应用程序，选择服务，单击**启动**，然后选择**允许服务与桌面交互**选项。

## <a name="see-also"></a>请参阅

[调试提示](../atl/debugging-tips.md)
