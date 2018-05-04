---
title: 使用调试版本检查内存改写 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c89242a63484eaccd0330eddac28c4e543ec61b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>使用调试版本检查内存改写
若要使用调试版本检查内存改写，首先必须重新生成用于调试的项目。 然后，请转到你的应用程序一开始`InitInstance`函数，并添加以下行：  
  
```  
afxMemDF |= checkAlwaysMemDF;  
```  
  
 调试内存分配器放置解决所有内存分配的保护字节。 但是，这些保护字节不对没有任何好处，除非你检查它们是否具有已更改 （这将指示内存覆盖）。 否则，它们只是提供事实上，可能会使您得以逃避内存覆盖缓冲区。  
  
 通过打开`checkAlwaysMemDF`，将强制 MFC 调用`AfxCheckMemory`函数每次调用**新**或**删除**进行。 如果检测到内存改写，它将生成类似于以下跟踪消息：  
  
```  
Damage Occurred! Block=0x5533  
```  
  
 如果你看到以下消息之一，你需要单步执行代码以确定发生损坏的位置。 若要隔离内存改写发生位置更确切地说，你可以显式调用`AfxCheckMemory`自己。 例如：  
  
```  
ASSERT(AfxCheckMemory());  
    DoABunchOfStuff();  
    ASSERT(AfxCheckMemory());  
```  
  
 如果第一个 ASSERT 成功，而第二个失败，它表示内存改写必须发生之间的两个调用的函数中。  
  
 根据你的应用程序的性质，可能会发现`afxMemDF`导致你的程序运行得太慢甚至测试。 `afxMemDF`变量会导致`AfxCheckMemory`为到新的每个调用调用和删除。 在这种情况下，你应散点图对你自己调用`AfxCheckMemory`（），如上所示，然后重试隔离内存覆盖这种方式。  
  
## <a name="see-also"></a>请参阅  
 [修复发行版本问题](../../build/reference/fixing-release-build-problems.md)