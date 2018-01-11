---
title: "测试 Internet 应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0cc214eb98b8aa9e927fd471ba313e4cade426a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="testing-internet-applications"></a>测试 Internet 应用程序
Internet 上有一些独特的测试难题，特别是在 Web 服务器上运行的应用程序。 您的初始测试可能通过使用至测试服务器的单一用户客户端连接来完成。 这对调试代码很有用。  
  
 您还需要在实际条件下测试：通过高速连接以及低速串行线路连接了多个客户端，包括调制解调器连接。 模拟实际条件很难，但肯定值得花时间设计可能的方案和执行它们。 如有可能，您还需要使用工具执行容量和压力测试。 某些 Bug 的类（如计时 Bug）很难查找和重现。  
  
 Internet 编程难题之一是其可见性。 对站点的大量访问可能降低服务器的速度。 您希望服务器温和地降级。 如果应用程序失败（例如，数据在写入注册表时或在客户端上写入 Cookie 时损坏），则您需要防止任何可能破坏用户计算机的内容。  
  
## <a name="see-also"></a>请参阅  
 [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)   
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)

