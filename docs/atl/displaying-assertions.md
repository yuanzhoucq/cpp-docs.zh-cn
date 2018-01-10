---
title: "显示断言 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bff1ab29841ff2dd9973d538bb763d1fc1126a8f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="displaying-assertions"></a>显示断言
如果连接到你的服务的客户端似乎停止响应，服务可能有断言，并显示一个消息框，你不可以看到。 您可以通过使用 Visual c + + 的调试器来调试你的代码对此进行确认 (请参阅[使用任务管理器](../atl/using-task-manager.md)本部分前面的)。  
  
 如果你确定你的服务显示一个消息框，你无法看到，你可能想要设置**允许服务与桌面交互**之前再次使用该服务的选项。 此选项是启动参数，允许服务出现在桌面上显示任何消息框。 若要设置此选项，打开服务控制面板应用程序，选择的服务，单击**启动**，然后选择**允许服务与桌面交互**选项。  
  
## <a name="see-also"></a>请参阅  
 [调试提示](../atl/debugging-tips.md)

