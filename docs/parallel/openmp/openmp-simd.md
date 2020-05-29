---
title: SIMD 扩展
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 0a7f1142a3a432628795341f4885b76a5c144990
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366451"
---
# <a name="simd-extension"></a>SIMD 扩展

Visual C++目前支持 OpenMP 2.0 标准，但 Visual Studio 2019 现在还提供 SIMD 功能。

> [!NOTE]
> 要使用 SIMD，请使用`-openmp:experimental`交换机进行编译，该开关启用使用`-openmp`交换机时不可用的其他 OpenMP 功能。
>
> `-openmp:experimental`开关的底入`-openmp`，这意味着所有OpenMP 2.0功能都包含在它的使用中。

有关详细信息，请参阅[在可视化工作室中C++ OpenMP 的 SIMD 扩展](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/)。

## <a name="openmp-simd-in-visual-c"></a>视觉C++中的 OPENMP SIMD

OpenMP SIMD，在 OpenMP 4.0 标准中引入，目标是使矢量友好环路。 通过使用循环前的`simd`指令，编译器可以忽略矢量依赖项，使循环尽可能友好矢量，并尊重用户同时执行多个循环迭代的意图。

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

可视C++提供类似的非 OpenMP 循环杂注，`#pragma vector`例如`#pragma ivdep`和 ，但是使用 OpenMP SIMD，编译器可以执行更多操作，例如：

- 始终允许忽略当前矢量依赖项。
- `/fp:fast`在循环中启用。
- 具有函数调用的外部循环和循环是矢量友好的。
- 嵌套循环可以合并到一个循环中，使矢量友好。
- 混合加速度`#pragma omp for simd`，实现粗粒度多线程和细粒度矢量。  

对于矢量友好型循环，编译器将保持静音状态，除非您使用矢量支持日志开关：

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

对于非矢量友好循环，编译器会为每个循环发出一条消息：

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>子句

OpenMP SIMD 指令还可以采用以下子句来增强矢量支持：

|指令|说明|
|---|---|
|`simdlen(length)`|指定矢量通道数。|
|`safelen(length)`|指定矢量依赖项距离。|
|`linear(list[ : linear-step]`)|从环路感应变量到阵列订阅的线性映射。|
|`aligned(list[ : alignment])`|数据的对齐方式。|
|`private(list)`|指定数据私有化。|
|`lastprivate(list)`|使用上次迭代中的最终值指定数据私有化。|
|`reduction(reduction-identifier:list)`|指定自定义的缩减操作。|
|`collapse(n)`|合并循环嵌套。|

> [!NOTE]
> 无效的 SIMD 子句由编译器使用警告进行解析和忽略。
>
> 例如，使用以下代码会发出警告：
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
  
OpenMP SIMD 指令为用户提供了一种指令编译器使循环矢量友好的方法。 通过使用 OpenMP SIMD 指令对循环进行加号，用户打算同时执行多个循环迭代。

例如，以下循环使用 OpenMP SIMD 指令进行带号表示。 循环迭代之间没有完美的并行性，因为从 a_i] 到 {i-1} 存在向后依赖关系，但由于 SIMD 指令，编译器仍允许将第一个语句的连续迭代打包到一个矢量指令中并并行运行它们。

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

因此，循环的以下转换向量形式**是合法的**，因为编译器保留每个原始循环迭代的顺序行为。 换句话`a[i]`说，在 之后执行`a[-1]`，`b[i]``a[i]`调用`bar`后发生最后。

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

如果内存引用可能与`a[i]`或`b[i]`进行别名，`*c`则将内存引用移出循环**是不合法的**。 如果语句打破了顺序依赖项，则在原始迭代中重新排序语句也不合法。 例如，以下转换的循环不合法：

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

## <a name="see-also"></a>另请参阅

[/openmp （启用 OpenMP 2.0 支持）](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>
