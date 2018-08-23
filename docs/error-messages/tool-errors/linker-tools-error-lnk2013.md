---
title: 链接器工具错误 LNK2013 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9320b9ead0276b6fb5e1b9773260049a01520e12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299846"
---
# <a name="linker-tools-error-lnk2013"></a>链接器工具错误 LNK2013
修正类型修正溢出。 目标 symbol name 不在范围内  
  
 链接器无法使必要的地址或偏移量适合给定的指令，因为目标符号太远距离指令的位置。  
  
 你可以解决此问题，通过创建多个映像，或使用[/order](../../build/reference/order-put-functions-in-order.md)选项使指令和目标靠近。  
  
 用户定义的符号 （而不是编译器生成的符号） 的符号名称时，你还可以尝试以下操作来解决该错误：  
  
-   更改为非静态的静态函数。  
  
-   重命名包含静态的函数，以便调用方相同的代码部分。  
  
 使用`DUMPBIN /SYMBOLS`、 函数是否为静态。