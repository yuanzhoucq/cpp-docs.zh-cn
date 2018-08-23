---
title: 显示断言 |Microsoft 文档
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
ms.openlocfilehash: f9133d2fadfa4158eef9755fff7e0d2a62478966
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354274"
---
# <a name="displaying-assertions"></a>显示断言
如果连接到你的服务的客户端似乎停止响应，服务可能有断言，并显示一个消息框，你不可以看到。 您可以通过使用 Visual c + + 的调试器来调试你的代码对此进行确认 (请参阅[使用任务管理器](../atl/using-task-manager.md)本部分前面的)。  
  
 如果你确定你的服务显示一个消息框，你无法看到，你可能想要设置**允许服务与桌面交互**之前再次使用该服务的选项。 此选项是启动参数，允许服务出现在桌面上显示任何消息框。 若要设置此选项，打开服务控制面板应用程序，选择的服务，单击**启动**，然后选择**允许服务与桌面交互**选项。  
  
## <a name="see-also"></a>请参阅  
 [调试提示](../atl/debugging-tips.md)

