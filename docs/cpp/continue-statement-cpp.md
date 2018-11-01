---
title: continue 语句 (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: 6fbc4af6a9a56f3406582ea9ba59f4d5759b88a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607475"
---
# <a name="continue-statement-c"></a>continue 语句 (C++)

强制转移到的控制表达式的最小封闭[做](../cpp/do-while-statement-cpp.md)，[有关](../cpp/for-statement-cpp.md)，或[而](../cpp/while-statement-cpp.md)循环。

## <a name="syntax"></a>语法

```
continue;
```

## <a name="remarks"></a>备注

将不会执行当前迭代中的所有剩余语句。 确定循环的下一次迭代，如下所示：

- 中**做**或**时**循环中下, 一个迭代首先会重新计算的控制表达式**执行**或**而**语句。

- 在中**有关**循环 (使用语法`for`(`init-expr`;`cond-expr`;`loop-expr`))，则`loop-expr`执行子句。 然后，重新计算 `cond-expr` 子句，并根据结果确定该循环结束还是进行另一个迭代。

下面的示例演示如何**继续**语句可用于跳过代码部分，并开始循环的下一个迭代。

## <a name="example"></a>示例

```cpp
// continue_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        i++;
        printf_s("before the continue\n");
        continue;
        printf("after the continue, should never print\n");
     } while (i < 3);

     printf_s("after the do loop\n");
}
```

```Output
before the continue
before the continue
before the continue
after the do loop
```

## <a name="see-also"></a>请参阅

[跳转语句](../cpp/jump-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)