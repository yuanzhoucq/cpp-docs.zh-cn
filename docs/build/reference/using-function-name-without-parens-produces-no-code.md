---
title: 使用函数名称，没有 （） 不产生代码 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40aed3969ae0707b07f0912d7247b49886d0319d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="using-function-name-without--produces-no-code"></a>使用没有 () 的函数名不产生代码
当使用在程序中声明的函数名称时不带括号时，编译器不生成代码。 无论该函数使用参数，因为编译器将计算的函数地址; 将发生这种情况但是，因为不存在的函数调用运算符"（）"，则不进行调用。 此结果是类似于以下：  
  
```  
// compile with /Wall to generate a warning  
int a;  
a;      // no code generated here either  
```  
  
 在 Visual c + +，甚至使用警告等级 4 不生成诊断输出。 会不发出任何警告;会不生成任何代码。  
  
 下面的示例代码 （伴有警告） 编译和链接正确且没有错误，但是没有产生代码引用到`funcn( )`。 为此正常工作，添加函数调用运算符"（）"。  
  
```  
#include <stdio.h>  
void funcn();  
  
int main() {  
   funcn;      /* missing function call operator;   
                  call will fail.  Use funcn() */  
   }  
  
void funcn() {  
   printf("\nHello World\n");  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [优化代码](../../build/reference/optimizing-your-code.md)