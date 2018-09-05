---
title: 显示断言 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ff7b9b29808e310be2d5568add64a0294bc67e7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762377"
---
# <a name="displaying-assertions"></a>显示断言

如果客户端连接到你的服务似乎停止响应，服务可能已添加并显示一个消息框，您不能以查看。 你可以通过使用 Visual c + + 的调试器来调试代码确认这一点 (请参阅[使用任务管理器](../atl/using-task-manager.md)本部分前面)。

如果你确定你的服务显示一个消息框，您不能看到，您可能想要设置**允许服务与桌面交互**之前再次使用该服务的选项。 此选项是允许服务出现在桌面上显示的任何消息框的启动参数。 若要设置此选项，打开服务控制面板应用程序，选择服务，单击**启动**，然后选择**允许服务与桌面交互**选项。

## <a name="see-also"></a>请参阅

[调试提示](../atl/debugging-tips.md)

