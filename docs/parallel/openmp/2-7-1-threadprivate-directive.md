---
title: 2.7.1 threadprivate 指令 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31c9c70940b558d0b4cc3f77677665235417694d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398139"
---
# <a name="271-threadprivate-directive"></a>2.7.1 threadprivate 指令

`threadprivate`指令使命名的文件范围、 命名空间范围或块范围静态变量中指定*变量列表*线程私有的。 *变量列表*是不具有不完整类型的变量的以逗号分隔列表。 语法`threadprivate`指令是按如下所示：

```
#pragma omp threadprivate(variable-list) new-line
```

每个副本`threadprivate`变量初始化一次，未指定点在程序之前对该副本的第一个引用并按常规方式 （即，因为主控副本会在串行执行程序中初始化）。 请注意，如果在显式初始值设定项的引用对象的`threadprivate`在变量的副本的第一个引用之前修改变量和对象的值，则行为是未指定。

因为与任何私有变量，一个线程不能引用另一个线程份`threadprivate`对象。 在序列区域和程序的主区域中，引用将会为对象的主线程的副本。

执行的第一个并行区域中的数据后`threadprivate`对象保证能够持久保留只有如果动态线程机制已被禁用，并且线程数保持不变的所有并行区域。

对限制`threadprivate`指令如下所示：

- 一个`threadprivate`文件范围或命名空间范围变量的指令必须出现之外的任何定义或声明中，并且必须从词法上位于其列表中之前对任何变量的所有引用。

- 在每个变量*变量列表*的`threadprivate`在词法上位于该指令的文件或命名空间范围内的变量声明必须引用在文件或命名空间范围内的指令。

- 一个`threadprivate`静态块范围变量的指令必须出现在变量的作用域并不在嵌套作用域。 指令从词法上必须位于所有引用的任何变量都之前在其列表中。

- 在每个变量*变量列表*的`threadprivate`块范围中的指令必须引用在词法上位于该指令之前的相同作用域中的变量声明。 变量声明必须使用静态存储类说明符。

- 如果在指定的变量`threadprivate`指令在一个翻译单元中，它必须以指定`threadprivate`指令在其中声明每个翻译单元中。

- 一个`threadprivate`变量必须出现在除任何子句`copyin`， `copyprivate`， `schedule`， `num_threads`，或**如果**子句。

- 地址`threadprivate`变量不是地址常量。

- 一个`threadprivate`变量不能是不完整类型或引用类型。

- 一个`threadprivate`与非 POD 类类型的变量必须具有可访问的、 明确的复制构造函数，如果它用显式初始值设定项声明。

下面的示例演示如何修改显示在初始值设定项中的变量可能会导致未指定的行为，以及如何通过使用一个辅助对象和复制构造函数来避免此问题。

```
int x = 1;
T a(x);
const T b_aux(x); /* Capture value of x = 1 */
T b(b_aux);
#pragma omp threadprivate(a, b)

void f(int n) {
   x++;
   #pragma omp parallel for
   /* In each thread:
   * Object a is constructed from x (with value 1 or 2?)
   * Object b is copy-constructed from b_aux
   */
   for (int i=0; i<n; i++) {
      g(a, b); /* Value of a is unspecified. */
   }
}
```

## <a name="cross-references"></a>交叉引用：

- 动态线程，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)第 39 页上。

- `OMP_DYNAMIC` 环境变量，请参阅[4.3 节](../../parallel/openmp/4-3-omp-dynamic.md)49 页上。