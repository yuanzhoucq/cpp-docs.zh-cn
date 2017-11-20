---
title: "中生成文件预处理表达式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 32de1d1eb3262e1fca0a00048a61d3129347cb19
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="expressions-in-makefile-preprocessing"></a>生成文件预处理中的表达式
**！如果**或**！ELSE IF** `constantexpression`组成 （采用十进制或 C 语言表示法） 的整数常量、 字符串常量或命令。 使用括号来为组表达式。 表达式使用 C 样式符号长整数算术;数字是在 32 位 2 的补数的形式范围在-2147483648 到 2147483647。  
  
 表达式可以使用在常数值、 命令、 字符串、 宏和文件系统路径的退出代码的运算符。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
 [生成文件预处理运算符](../build/makefile-preprocessing-operators.md)  
  
 [在预处理中执行程序](../build/executing-a-program-in-preprocessing.md)  
  
## <a name="see-also"></a>另请参阅  
 [生成文件预处理](../build/makefile-preprocessing.md)