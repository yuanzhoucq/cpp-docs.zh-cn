---
title: "转储延迟加载的导入 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3800d4863bc1aa3e3c847ff0cea886be2fede985
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dumping-delay-loaded-imports"></a>转储延迟加载的导入
可使用转储延迟加载的导入[dumpbin /imports](../../build/reference/imports-dumpbin.md)和显示与略有不同的信息不是标准导入。 它们被隔离到它们自己的 /imports 转储的部分，并显式标记为延迟加载的导入。 如果卸载映像中存在的信息，该记录。 如果存在的绑定信息，以及导入的绑定地址记录的目标 DLL 的时间/日期戳。  
  
## <a name="see-also"></a>请参阅  
 [延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)