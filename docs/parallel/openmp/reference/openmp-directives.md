---
title: OpenMP 指令
ms.date: 10/22/2018
f1_keywords:
- OpenMP directives
- atomic
- barrier
- critical
- flush
- for
- master
- ordered
- parallel
- section
- SECTIONS
- single
- threadprivate
helpviewer_keywords:
- OpenMP directives
- atomic OpenMP directive
- barrier OpenMP directive
- critical OpenMP directive
- flush OpenMP directive
- for OpenMP directive
- master OpenMP directive
- ordered OpenMP directive
- parallel OpenMP directive
- sections OpenMP directive
- single OpenMP directive
- threadprivate OpenMP directive
ms.assetid: 0562c263-344c-466d-843e-de830d918940
ms.openlocfilehash: a61e74bda4e508bac3c4afd183fa2ab204c629d1
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51333236"
---
# <a name="openmp-directives"></a>OpenMP 指令

提供指向 OpenMP API 中使用的指令。

Visual c + + 支持以下 OpenMP 指令：

|指令|描述|
|---------|-----------|
|[atomic](#atomic)|指定将以原子方式更新的内存位置。|
|[barrier](#barrier)|同步团队; 中的所有线程所有线程在屏障，都暂停，直到所有线程都执行屏障。|
|[critical](#critical)|指定代码仅执行一个线程上一次。|
|[flush](#flush-openmp)|指定的所有线程都都共享的所有对象的内存的相同视图。|
|[for](#for-openmp)|导致中完成的工作`for`要在线程之间划分的并行区域内的循环。|
|[master](#master)|指定只有主线程应执行的程序部分。|
|[排序](#ordered-openmp-directives)|指定该代码在并行化`for`应如顺序循环执行循环。|
|[parallel](#parallel)|定义并行区域，这是由多个线程并行执行的代码。|
|[部分](#sections-openmp)|标识代码段来分担所有线程。|
|[single](#single)|可以指定一段代码应在单个线程，不一定是主线程上执行。|
|[threadprivate](#threadprivate)|指定一个变量是线程私有的。|

## <a name="atomic"></a>原子

指定将以原子方式更新的内存位置。

```
#pragma omp atomic
   expression
```

### <a name="parameters"></a>参数

*表达式*<br/>
包含左值，你想要防止多个写入其内存位置的语句。 有关合法表达式形式的详细信息，请参阅的 OpenMP 规范。

### <a name="remarks"></a>备注

`atomic`指令支持任何 OpenMP 子句。

有关详细信息，请参阅[2.6.4 atomic 构造](../../../parallel/openmp/2-6-4-atomic-construct.md)。

### <a name="example"></a>示例

```
// omp_atomic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define MAX 10

int main() {
   int count = 0;
   #pragma omp parallel num_threads(MAX)
   {
      #pragma omp atomic
      count++;
   }
   printf_s("Number of threads: %d\n", count);
}
```

```Output
Number of threads: 10
```

## <a name="barrier"></a>屏障

同步团队; 中的所有线程所有线程在屏障，都暂停，直到所有线程都执行屏障。

```
#pragma omp barrier
```

### <a name="remarks"></a>备注

`barrier`指令支持任何 OpenMP 子句。

有关详细信息，请参阅[2.6.3 barrier 指令](../../../parallel/openmp/2-6-3-barrier-directive.md)。

### <a name="example"></a>示例

有关如何使用的示例`barrier`，请参阅[主](#master)。

## <a name="critical"></a>关键

指定代码仅执行一个线程上一次。

```
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>参数

*name*<br/>
（可选）用于标识关键代码的名称。 请注意该名称必须括在括号中。

### <a name="remarks"></a>备注

`critical`指令支持任何 OpenMP 子句。

有关详细信息，请参阅[2.6.2 关键构造](../../../parallel/openmp/2-6-2-critical-construct.md)。

### <a name="example"></a>示例

```
// omp_critical.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>

#define SIZE 10

int main()
{
    int i;
    int max;
    int a[SIZE];

    for (i = 0; i < SIZE; i++)
    {
        a[i] = rand();
        printf_s("%d\n", a[i]);
    }

    max = a[0];
    #pragma omp parallel for num_threads(4)
        for (i = 1; i < SIZE; i++)
        {
            if (a[i] > max)
            {
                #pragma omp critical
                {
                    // compare a[i] and max again because max
                    // could have been changed by another thread after
                    // the comparison outside the critical section
                    if (a[i] > max)
                        max = a[i];
                }
            }
        }

    printf_s("max = %d\n", max);
}
```

```Output
41
18467
6334
26500
19169
15724
11478
29358
26962
24464
max = 29358
```

## <a name="flush-openmp"></a>刷新 (OpenMP)

指定的所有线程都都共享的所有对象的内存的相同视图。

```
#pragma omp flush [(var)]
```

### <a name="parameters"></a>参数

*var*<br/>
（可选）逗号分隔的变量表示你想要同步的对象的列表。 如果`var`未指定，刷新所有内存。

### <a name="remarks"></a>备注

`flush`指令支持任何 OpenMP 子句。

有关详细信息，请参阅[2.6.5 flush 指令](../../../parallel/openmp/2-6-5-flush-directive.md)。

### <a name="example"></a>示例

```
// omp_flush.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void read(int *data) {
   printf_s("read data\n");
   *data = 1;
}

void process(int *data) {
   printf_s("process data\n");
   (*data)++;
}

int main() {
   int data;
   int flag;

   flag = 0;

   #pragma omp parallel sections num_threads(2)
   {
      #pragma omp section
      {
         printf_s("Thread %d: ", omp_get_thread_num( ));
         read(&data);
         #pragma omp flush(data)
         flag = 1;
         #pragma omp flush(flag)
         // Do more work.
      }

      #pragma omp section
      {
         while (!flag) {
            #pragma omp flush(flag)
         }
         #pragma omp flush(data)

         printf_s("Thread %d: ", omp_get_thread_num( ));
         process(&data);
         printf_s("data = %d\n", data);
      }
   }
}
```

```Output
Thread 0: read data
Thread 1: process data
data = 2
```

## <a name="for-openmp"></a>对于 (OpenMP)

导致中完成的工作`for`要在线程之间划分的并行区域内的循环。

```
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>参数

*子句*<br/>
（可选）零个或多个子句。 请参阅支持的子句的列表的备注部分`for`。

*for_statement*<br/>
一个`for`循环。 如果用户代码中，将会导致未定义的行为`for`循环更改索引变量。

### <a name="remarks"></a>备注

`for`指令支持以下 OpenMP 子句：

- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [nowait](openmp-clauses.md#nowait)
- [排序](openmp-clauses.md#ordered-openmp-clauses)
- [private](openmp-clauses.md#private-openmp)
- [reduction](openmp-clauses.md#reduction)
- [schedule](openmp-clauses.md#schedule)

如果`parallel`同时指定，则`clauses`可以由接受的任何子句`parallel`或`for`指令，除`nowait`。

有关详细信息，请参阅[2.4.1 for 构造](../../../parallel/openmp/2-4-1-for-construct.md)。

### <a name="example"></a>示例

```
// omp_for.cpp
// compile with: /openmp
#include <stdio.h>
#include <math.h>
#include <omp.h>

#define NUM_THREADS 4
#define NUM_START 1
#define NUM_END 10

int main() {
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;
   int nThreads = 0, nTmp = nStart + nEnd;
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *
                               unsigned(abs(nTmp))) / 2;
   int nSumCalc = uTmp;

   if (nTmp < 0)
      nSumCalc = -nSumCalc;

   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)
   {
      #pragma omp master
      nThreads = omp_get_num_threads();

      #pragma omp for
      for (i=nStart; i<=nEnd; ++i) {
            #pragma omp atomic
            nSum += i;
      }
   }

   if  (nThreads == NUM_THREADS) {
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);
      nRet = 0;
   }
   else {
      printf_s("Expected %d OpenMP threads, but %d were used.\n",
               NUM_THREADS, nThreads);
      nRet = 1;
   }

   if (nSum != nSumCalc) {
      printf_s("The sum of %d through %d should be %d, "
               "but %d was reported!\n",
               NUM_START, NUM_END, nSumCalc, nSum);
      nRet = 1;
   }
   else
      printf_s("The sum of %d through %d is %d\n",
               NUM_START, NUM_END, nSum);
}
```

```Output
4 OpenMP threads were used.
The sum of 1 through 10 is 55
```

## <a name="master"></a>Master

指定只有主线程应执行的程序部分。

```
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>备注

`master`指令支持任何 OpenMP 子句。

[单个](#single)指令，可以指定一段代码应在单个线程，不一定是主线程上执行。

有关详细信息，请参阅[2.6.1 master 构造](../../../parallel/openmp/2-6-1-master-construct.md)。

### <a name="example"></a>示例

```
// omp_master.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>

int main( )
{
    int a[5], i;

    #pragma omp parallel
    {
        // Perform some computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] = i * i;

        // Print intermediate results.
        #pragma omp master
            for (i = 0; i < 5; i++)
                printf_s("a[%d] = %d\n", i, a[i]);

        // Wait.
        #pragma omp barrier

        // Continue with the computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] += i;
    }
}
```

```Output
a[0] = 0
a[1] = 1
a[2] = 4
a[3] = 9
a[4] = 16
```

## <a name="ordered-openmp-directives"></a>ordered （OpenMP 指令）

指定该代码在并行化`for`应如顺序循环执行循环。

```
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>备注

`ordered`指令必须是动态的范围内[有关](#for-openmp)或`parallel for`构造与`ordered`子句。

`ordered`指令支持任何 OpenMP 子句。

有关详细信息，请参阅[2.6.6 ordered 构造](../../../parallel/openmp/2-6-6-ordered-construct.md)。

### <a name="example"></a>示例

```
// omp_ordered.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

static float a[1000], b[1000], c[1000];

void test(int first, int last)
{
    #pragma omp for schedule(static) ordered
    for (int i = first; i <= last; ++i) {
        // Do something here.
        if (i % 2)
        {
            #pragma omp ordered
            printf_s("test() iteration %d\n", i);
        }
    }
}

void test2(int iter)
{
    #pragma omp ordered
    printf_s("test2() iteration %d\n", iter);
}

int main( )
{
    int i;
    #pragma omp parallel
    {
        test(1, 8);
        #pragma omp for ordered
        for (i = 0 ; i < 5 ; i++)
            test2(i);
    }
}
```

```Output
test() iteration 1
test() iteration 3
test() iteration 5
test() iteration 7
test2() iteration 0
test2() iteration 1
test2() iteration 2
test2() iteration 3
test2() iteration 4
```

## <a name="parallel"></a>并行

定义并行区域，这是由多个线程并行执行的代码。

```
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>参数

*子句*<br/>
（可选）零个或多个子句。  请参阅支持的子句的列表的备注部分`parallel`。

### <a name="remarks"></a>备注

`parallel`指令支持以下 OpenMP 子句：

- [copyin](openmp-clauses.md#copyin)
- [default](openmp-clauses.md#default-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [if](openmp-clauses.md#if-openmp)
- [num_threads](openmp-clauses.md#num-threads)
- [private](openmp-clauses.md#private-openmp)
- [reduction](openmp-clauses.md#reduction)
- [shared](openmp-clauses.md#shared-openmp)

`parallel` 也可以用于[各节](#sections-openmp)并[为](#for-openmp)指令。

有关详细信息，请参阅[2.3 parallel 构造](../../../parallel/openmp/2-3-parallel-construct.md)。

### <a name="example"></a>示例

下面的示例演示如何设置的线程数，并定义某个并行区域。 默认情况下在计算机上的逻辑处理器数相等的线程数。 例如，如果必须具有一个已启用超线程的物理处理器的计算机，它将具有两个逻辑处理器和两个线程。

```
// omp_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(4)
   {
      int i = omp_get_thread_num();
      printf_s("Hello from thread %d\n", i);
   }
}
```

```Output
Hello from thread 0
Hello from thread 1
Hello from thread 2
Hello from thread 3
```

### <a name="comment"></a>注释

请注意，在不同计算机上的输出顺序而异。

## <a name="sections-openmp"></a>部分 (OpenMP)

标识代码段来分担所有线程。

```
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   }
}
```

### <a name="parameters"></a>参数

*子句*<br/>
（可选）零个或多个子句。 请参阅支持的子句的列表的备注部分`sections`。

### <a name="remarks"></a>备注

`sections`指令可以包含零个或多`section`指令。

`sections`指令支持以下 OpenMP 子句：

- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [nowait](openmp-clauses.md#nowait)
- [private](openmp-clauses.md#private-openmp)
- [reduction](openmp-clauses.md#reduction)

如果`parallel`同时指定，则`clauses`可以由接受的任何子句`parallel`或`sections`指令，除`nowait`。

有关详细信息，请参阅[2.4.2 sections 构造](../../../parallel/openmp/2-4-2-sections-construct.md)。

### <a name="example"></a>示例

```
// omp_sections.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel sections num_threads(4)
    {
        printf_s("Hello from thread %d\n", omp_get_thread_num());
        #pragma omp section
        printf_s("Hello from thread %d\n", omp_get_thread_num());
    }
}
```

```Output
Hello from thread 0
Hello from thread 0
```

## <a name="single"></a>单个

可以指定一段代码应在单个线程，不一定是主线程上执行。

```
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>参数

*子句*<br/>
（可选）零个或多个子句。 请参阅支持的子句的列表的备注部分`single`。

### <a name="remarks"></a>备注

`single`指令支持以下 OpenMP 子句：

- [copyprivate](openmp-clauses.md#copyprivate)
- [firstprivate](openmp-clauses.md#firstprivate)
- [nowait](openmp-clauses.md#nowait)
- [private](openmp-clauses.md#private-openmp)

[主](#master)指令，可以指定应仅在主线程上执行的代码段。

有关详细信息，请参阅[2.4.3 单一构造](../../../parallel/openmp/2-4-3-single-construct.md)。

### <a name="example"></a>示例

```cpp
// omp_single.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(2)
   {
      #pragma omp single
      // Only a single thread can read the input.
      printf_s("read input\n");

      // Multiple threads in the team compute the results.
      printf_s("compute results\n");

      #pragma omp single
      // Only a single thread can write the output.
      printf_s("write output\n");
    }
}
```

```Output
read input
compute results
compute results
write output
```

## <a name="threadprivate"></a>threadprivate

指定一个变量是线程私有的。

```
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>参数

*var*<br/>
你想要对线程进行私有变量的以逗号分隔列表。 `var` 必须是全局或命名空间的范围内的变量或静态局部变量。

### <a name="remarks"></a>备注

`threadprivate`指令支持任何 OpenMP 子句。

有关详细信息，请参阅[2.7.1 threadprivate 指令](../../../parallel/openmp/2-7-1-threadprivate-directive.md)。

`threadprivate`指令基于[线程](../../../cpp/thread.md)属性使用[__declspec](../../../cpp/declspec.md)关键字; 限制`__declspec(thread)`适用于`threadprivate`。

不能使用`threadprivate`中将通过加载任意 DLL [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya)。  此禁止包括与加载的 Dll [/DELAYLOAD （延迟加载导入）](../../../build/reference/delayload-delay-load-import.md)，该列也会使用`LoadLibrary`。

可以使用`threadprivate`以静态方式在进程启动时加载的 DLL 中。

因为`threadprivate`基于`__declspec(thread)`、`threadprivate`变量将在任何线程已启动的过程中，而不仅仅是这些线程属于按并行区域生成一个线程团队中存在。  请注意此实现详细信息;您可能会注意到，有关示例，该构造函数`threadprivate`通常则预期更多调用用户定义的类型。

一个`threadprivate`destructable 类型的变量不能保证具有调用其析构函数。  例如：

```
struct MyType
{
    ~MyType();
};

MyType threaded_var;
#pragma omp threadprivate(threaded_var)
int main()
{
    #pragma omp parallel
    {}
}
```

用户具有关于构成并行区域的线程将终止时无法控制。  如果这些线程存在时在进程退出，线程不会告知进程退出，并且不会为调用的析构函数`threaded_var`除退出任何线程上 （此处，主线程）。  使代码不应依靠的正确析构`threadprivate`变量。

### <a name="example"></a>示例

有关使用的示例`threadprivate`，请参阅[专用](openmp-clauses.md#private-openmp)。
