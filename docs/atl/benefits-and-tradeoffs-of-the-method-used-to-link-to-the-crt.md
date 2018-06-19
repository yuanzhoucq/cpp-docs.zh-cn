---
title: 优点和缺点用于对链接到 CRT 的方法 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2835e88da11b8d8332226080eb860afd41c0702
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355382"
---
# <a name="benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt"></a>优点和用于对链接到 CRT 的方法的缺点
动态或静态，可以将你的项目链接的 CRT。 下表概述了的优点和缺点参与选择要使用的方法。  
  
|方法|好处|权衡|  
|------------|-------------|--------------|  
|静态链接到 CRT 的内容<br /><br /> (**运行时库**设置为**单线程方式**)|图像将运行其中的系统上不需要 CRT DLL。|大约 25 K 的启动代码将添加到你的映像，其大小，显著增加。|  
|动态链接到 CRT 的内容<br /><br /> (**运行时库**设置为**多线程**)|你的映像不需要 CRT 启动代码，因此很小得多。|CRT DLL 必须在运行映像的系统上。|  
  
 主题[链接到 CRT 的内容在 ATL 项目中](../atl/linking-to-the-crt-in-your-atl-project.md)讨论如何选择要在其中链接到 CRT 的方式。  
  
## <a name="see-also"></a>请参阅  
 [使用 ATL 和 C 运行时代码编程](../atl/programming-with-atl-and-c-run-time-code.md)   
 [Dll 和 Visual c + + 运行库行为](../build/run-time-library-behavior.md)   
 [CRT 库功能](../c-runtime-library/crt-library-features.md)

