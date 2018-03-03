---
title: "链接器工具错误 LNK2013 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8cf88f768f05eee06ae8ffaa66f8de5a9c443f82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2013"></a>链接器工具错误 LNK2013
修正类型修正溢出。 目标 symbol name 不在范围内  
  
 链接器无法使必要的地址或偏移量适合给定的指令，因为目标符号太远距离指令的位置。  
  
 你可以解决此问题，通过创建多个映像，或使用[/order](../../build/reference/order-put-functions-in-order.md)选项使指令和目标靠近。  
  
 用户定义的符号 （而不是编译器生成的符号） 的符号名称时，你还可以尝试以下操作来解决该错误：  
  
-   更改为非静态的静态函数。  
  
-   重命名包含静态的函数，以便调用方相同的代码部分。  
  
 使用`DUMPBIN /SYMBOLS`、 函数是否为静态。