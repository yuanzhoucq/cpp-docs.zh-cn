---
title: SIMD 扩展
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 52402aa553c6d68d3073aba26ecac7b784522ee9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363266"
---
# <a name="simd-extension"></a>SIMD 扩展

VisualC++当前支持 OpenMP 2.0 标准，不过，由于 Visual Studio 2019 现在还提供了单指令多数据功能。

> [!NOTE]
> 若要使用单指令多数据，使用编译`-openmp:experimental`使其他 OpenMP 功能不可用时使用的交换机`-openmp`切换。
>
> `-openmp:experimental`交换机 subsumes `-openmp`，这意味着它的使用中包括所有 OpenMP 2.0 功能。

有关详细信息，请参阅[SIMD 扩展到C++Visual Studio 中的 OpenMP](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/)。

## <a name="openmp-simd-in-visual-c"></a>视觉对象中的 OpenMP 单指令多数据C++

OpenMP SIMD，4.0 中引入了 OpenMP 标准，使向量友好循环的目标。 通过使用`simd`指令循环前，编译器可以忽略的向量依赖项、 使循环为向量，并采用具有同时执行多个循环迭代的用户的意图。

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

VisualC++提供了类似的非 OpenMP 循环杂注喜欢`#pragma vector`并`#pragma ivdep`，但使用 OpenMP 单指令多数据，则编译器可以执行的详细信息，如：

- 始终允许忽略存在的向量依赖项。
- `/fp:fast` 已启用在循环中。
- 外环和循环与函数调用都是矢量友好。
- 可以合并到一个循环并进行矢量友好嵌套的循环。
- 使用混合加速`#pragma omp for simd`启用粗粒度的多线程处理和精细向量。  

对于向量友好的圆圈，编译器保持无提示，除非使用向量支持 log 开关：

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

对于非向量友好的圆圈，则编译器会发出每一条消息：

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>子句

OpenMP SIMD 指令还可以采用以下子句来增强向量支持：

|指令|描述|
|---|---|
|`simdlen(length)`|指定向量的通道数。|
|`safelen(length)`|指定的向量依赖项距离。|
|`linear(list[ : linear-step]`)|数组订阅到循环归纳变量的线性映射。|
|`aligned(list[ : alignment])`|数据的对齐方式。|
|`private(list)`|指定数据私有化。|
|`lastprivate(list)`|指定数据私有化最后一次迭代中的最后一个值。|
|`reduction(reduction-identifier:list)`|指定自定义的缩减操作。|
|`collapse(n)`|合并循环嵌套。|

> [!NOTE]
> 非有效 SIMD 子句可以分析和由编译器使用警告被忽略。
>
> 警告例如，使用以下代码问题：
>
> ```c
>    #pragma omp simd simdlen(8)
>    for (i = 0; i < count; i++)
>    {
>        a[i] = a[i-1] + 1;
>        b[i] = *c + 1;
>        bar(i);
>    }
> ```
>
> ```Output
>    warning C4849: OpenMP 'simdlen' clause ignored in 'simd' directive
> ```

### <a name="example"></a>示例
  
OpenMP SIMD 指令为用户提供了一种方法来指示编译器的品牌循环向量友好。 添加批注与 OpenMP SIMD 指令的循环，用户会有多个同时执行的循环迭代。

例如，下面的循环将批注 OpenMP SIMD 指令。 存在，不能完美并行循环迭代中的，因为没有向后依赖项从 [i] 到 [i-1]，但由于仍允许编译器以打包为一个矢量指令的第一个语句的连续迭代并运行的 SIMD 指令这些并行。

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

因此，以下循环的转换后的向量形式是**法律**因为编译器会每个原始的循环迭代的顺序行为。 换而言之，`a[i]`后，执行`a[-1]`，`b[i]`晚`a[i]`，并向调用`bar`居。

```c
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        b[i:i+3] = *c + 1;
        bar(i);
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

它具有**不合法**移动内存引用`*c`跳出循环，如果使用别名可能`a[i]`或`b[i]`。 是还不合法的对一个原始迭代中的语句进行重新排序，如果这会破坏顺序依赖关系。 例如，以下转换的循环不是合法的：

```c
    c = b;
    t = *c;
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        bar(i);            // illegal to reorder if bar[i] depends on b[i]
        b[i:i+3] = t + 1;  // illegal to move *c out of the loop
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

## <a name="see-also"></a>请参阅

[/openmp（启用 OpenMP 2.0 支持）](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>
