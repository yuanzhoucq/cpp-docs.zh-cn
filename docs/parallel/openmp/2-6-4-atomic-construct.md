---
title: 2.6.4 atomic 构造
ms.date: 11/04/2016
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
ms.openlocfilehash: 1f477a59ef475fda9bd0daeeb4edac18a3eeedb9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677651"
---
# <a name="264-atomic-construct"></a>2.6.4 atomic 构造

`atomic`指令可确保特定的内存位置，而不是将其公开都会向可能的多个以原子方式，更新同时编写线程。 语法`atomic`指令是按如下所示：

```
#pragma omp atomic new-lineexpression-stmt
```

表达式语句必须具有以下形式之一：

*x binop*= *expr*

x + +

+ + x

x-

--x

在前面的表达式：

- *x*是具有标量类型的左值表达式。

- *expr*是与标量类型的表达式，它不引用指定的对象*x*。

- `binop` 重载的运算符并不是 +、 \*、-、 /、 &、 ^， &#124;，<\<，或 >>。

尽管它是实现定义的实现是否替换所有`atomic`指令与**关键**指令必须具有相同唯一*名称*，则`atomic`指令允许更好的优化。 提供了硬件说明通常可以执行系统开销最少的原子更新。

负载和指定的对象的应用商店*x*是原子; 的计算*expr*不是原子的。 若要避免出现争用情况，并行中的位置的所有更新应都保护与`atomic`指令，除了那些已知可免费的争用条件。

限制`atomic`指令如下所示：

- 对在整个程序的存储位置 x 的所有原子引用需要具有兼容的类型。

## <a name="examples"></a>示例：

```
extern float a[], *p = a, b;
/* Protect against races among multiple updates. */
#pragma omp atomic
a[index[i]] += b;
/* Protect against races with updates through a. */
#pragma omp atomic
p[i] -= 1.0f;

extern union {int n; float x;} u;
/* ERROR - References through incompatible types. */
#pragma omp atomic
u.n++;
#pragma omp atomic
u.x -= 1.0f;
```