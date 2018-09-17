---
title: 使用函数名称没有 （） 会不生成任何代码 |Microsoft Docs
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
ms.openlocfilehash: 13ca43386c9ef46f526538781a91fd1a81ade537
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710575"
---
# <a name="using-function-name-without--produces-no-code"></a>使用没有 () 的函数名不产生代码

当使用在程序中声明的函数名称时不带括号时，编译器不生成代码。 此时不考虑该函数使用参数，因为编译器计算的函数地址;但是，由于函数调用运算符"（）"不存在，因此没有进行调用。 此结果是类似于下面：

```
// compile with /Wall to generate a warning
int a;
a;      // no code generated here either
```

在 Visual c + +，甚至使用警告等级 4 不生成诊断输出。 会不发出任何警告;不生成任何代码。

下面的示例代码编译 （有一条警告） 和正确链接未出现错误，但是产生与代码`funcn( )`。 为此才能正常工作，添加函数调用运算符"（）"。

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