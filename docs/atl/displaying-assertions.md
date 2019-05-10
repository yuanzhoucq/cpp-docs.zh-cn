---
title: 显示断言
ms.date: 05/05/2019
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
ms.openlocfilehash: 962a33a7d5d922f7f1655e22b2c9d0acdcf8925c
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221261"
---
# <a name="displaying-assertions"></a>显示断言

如果客户端连接到你的服务似乎停止响应，服务可能已添加并显示一个消息框，您不能以查看。 你可以通过使用 Visual Studio 调试器来调试代码确认这一点 (请参阅[使用任务管理器](../atl/using-task-manager.md)本部分前面)。

如果你确定你的服务显示一个消息框，您不能看到，您可能想要设置**允许服务与桌面交互**之前再次使用该服务的选项。 此选项是允许服务出现在桌面上显示的任何消息框的启动参数。 若要设置此选项，打开服务控制面板应用程序，选择服务，单击**启动**，然后选择**允许服务与桌面交互**选项。

## <a name="see-also"></a>请参阅

[调试提示](../atl/debugging-tips.md)
