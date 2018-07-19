---
title: 中生成文件预处理表达式 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04a53e5e6fe45c2c846cae3fb9e973fe1c712107
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367263"
---
# <a name="expressions-in-makefile-preprocessing"></a>生成文件预处理中的表达式
**！如果**或 **！ELSE IF** `constantexpression`组成 （采用十进制或 C 语言表示法） 的整数常量、 字符串常量或命令。 使用括号来为组表达式。 表达式使用 C 样式符号长整数算术;数字是在 32 位 2 的补数的形式范围在-2147483648 到 2147483647。  
  
 表达式可以使用在常数值、 命令、 字符串、 宏和文件系统路径的退出代码的运算符。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
 [生成文件预处理运算符](../build/makefile-preprocessing-operators.md)  
  
 [在预处理中执行程序](../build/executing-a-program-in-preprocessing.md)  
  
## <a name="see-also"></a>请参阅  
 [生成文件预处理](../build/makefile-preprocessing.md)