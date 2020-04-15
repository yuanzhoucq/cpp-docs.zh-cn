---
title: OpenMP 指令
ms.date: 03/20/2019
f1_keywords:
- OpenMP directives
- atomic
- barrier
- critical
- flush
- for
- master
- parallel
- section
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
ms.openlocfilehash: 569419b3422b155afc6e9692efaecd4e5a06f188
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366448"
---
# <a name="openmp-directives"></a>OpenMP 指令

提供指向 OpenMP API 中使用的指令的链接。

可视C++支持以下 OpenMP 指令。

对于并行工作共享：

|指令|说明|
|---------|-----------|
|[并行](#parallel)|定义一个并行区域，即将由多个线程并行执行的代码。|
|[for](#for-openmp)|导致在并行区域内的`for`循环中完成的工作在线程之间分配。|
|[部分](#sections-openmp)|标识要在所有线程之间划分的代码节。|
|single |允许您指定应在单个线程（不一定是主线程）上执行代码部分。|

对于主和同步：

|指令|说明|
|---------|-----------|
|[主](#master)|指定只有主线程应执行程序的一个部分。|
|[关键](#critical)|指定代码一次仅在一个线程上执行。|
|[障碍](#barrier)|同步团队中的所有线程;所有线程都在屏障处暂停，直到所有线程执行障碍。|
|[原子 (atomic)](#atomic)|指定将以原子方式更新的内存位置。|
|[冲洗](#flush-openmp)|指定所有线程对所有共享对象的内存视图相同。|
|[命令](#ordered-openmp-directives)|指定并行`for`循环下的代码应像顺序循环一样执行。|

对于数据环境：

|指令|说明|
|---------|-----------|
|[threadprivate](#threadprivate)|指定变量是线程的私有变量。|

## <a name="atomic"></a><a name="atomic"></a>原子

指定将以原子方式更新的内存位置。

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>参数

*expression*<br/>
具有*lvalue*的语句，您希望防止其内存位置对多个写入进行保护。

### <a name="remarks"></a>备注

该`atomic`指令不支持任何子句。

有关详细信息，请参阅[2.6.4 原子构造](../../../parallel/openmp/2-6-4-atomic-construct.md)。

### <a name="example"></a>示例

```cpp
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

## <a name="barrier"></a><a name="barrier"></a>障碍

同步团队中的所有线程;所有线程都在屏障处暂停，直到所有线程执行障碍。

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>备注

该`barrier`指令不支持任何子句。

有关详细信息，请参阅[2.6.3 障碍指令](../../../parallel/openmp/2-6-3-barrier-directive.md)。

### <a name="example"></a>示例

有关如何使用的示例`barrier`，请参阅[master](#master)。

## <a name="critical"></a><a name="critical"></a>关键

指定一次仅在一个线程上执行代码。

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>参数

name <br/>
（可选）用于标识关键代码的名称。 名称必须包含在括号中。

### <a name="remarks"></a>备注

该`critical`指令不支持任何子句。

有关详细信息，请参阅[2.6.2 关键构造](../../../parallel/openmp/2-6-2-critical-construct.md)。

### <a name="example"></a>示例

```cpp
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

## <a name="flush"></a><a name="flush-openmp"></a>冲洗

指定所有线程对所有共享对象的内存视图相同。

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>参数

*var*<br/>
（可选）表示要同步对象的由逗号分隔的变量列表。 如果未指定*var，* 则刷新所有内存。

### <a name="remarks"></a>备注

该`flush`指令不支持任何子句。

有关详细信息，请参阅[2.6.5 刷新指令](../../../parallel/openmp/2-6-5-flush-directive.md)。

### <a name="example"></a>示例

```cpp
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

## <a name="for"></a><a name="for-openmp"></a>对于

导致在并行区域内的`for`循环中完成的工作在线程之间分配。

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>参数

*第*<br/>
（可选）零个或多个子句，请参阅**备注**部分。

*for_statement*<br/>
循环`for`。 如果循环中的用户代码更改索引变量，`for`则会导致未定义的行为。

### <a name="remarks"></a>备注

该`for`指令支持以下子句：

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [命令](openmp-clauses.md#ordered-openmp-clauses)
- [附表](openmp-clauses.md#schedule)
- [不等待](openmp-clauses.md#nowait)

如果`parallel``clauses`也指定，可以是`parallel`或`for`指令接受的任何子句，但`nowait`除外。

有关详细信息，请参阅[2.4.1 表示构造](../../../parallel/openmp/2-4-1-for-construct.md)。

### <a name="example"></a>示例

```cpp
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

## <a name="master"></a><a name="master"></a>主人

指定只有主线程应执行程序的一个部分。

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>备注

该`master`指令不支持任何子句。

单[一](#single)指令允许您指定应在单个线程（不一定是主线程）上执行代码部分。

有关详细信息，请参阅[2.6.1 主构造](../../../parallel/openmp/2-6-1-master-construct.md)。

### <a name="example"></a>示例

```cpp
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

## <a name="ordered"></a><a name="ordered-openmp-directives"></a>命令

指定并行`for`循环下的代码应像顺序循环一样执行。

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>备注

指令`ordered`必须在[for](#for-openmp)或`parallel for`构造与`ordered`子句的动态范围内。

该`ordered`指令不支持任何子句。

有关详细信息，请参阅[2.6.6 有序构造](../../../parallel/openmp/2-6-6-ordered-construct.md)。

### <a name="example"></a>示例

```cpp
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

## <a name="parallel"></a><a name="parallel"></a>并行

定义一个并行区域，即将由多个线程并行执行的代码。

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>参数

*第*<br/>
（可选）零个或多个子句，请参阅**备注**部分。

### <a name="remarks"></a>备注

该`parallel`指令支持以下子句：

- [if](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [共享](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel`也可以与[for](#for-openmp)和[节](#sections-openmp)指令一起使用。

有关详细信息，请参阅[2.3 并行构造](../../../parallel/openmp/2-3-parallel-construct.md)。

### <a name="example"></a>示例

下面的示例演示如何设置线程数和定义并行区域。 默认情况下，线程数与计算机上的逻辑处理器数相等。 例如，如果计算机具有一个物理处理器，启用了超线程，它将有两个逻辑处理器和两个线程。 不同机器的输出顺序可能有所不同。

```cpp
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

## <a name="sections"></a><a name="sections-openmp"></a>部分

标识要在所有线程之间划分的代码节。

```cpp
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   }
}
```

### <a name="parameters"></a>参数

*第*<br/>
（可选）零个或多个子句，请参阅**备注**部分。

### <a name="remarks"></a>备注

该`sections`指令可以包含零个或多个`section`指令。

该`sections`指令支持以下子句：

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [不等待](openmp-clauses.md#nowait)

如果`parallel``clauses`也指定，可以是`parallel`或`sections`指令接受的任何子句，但`nowait`除外。

有关详细信息，请参阅[2.4.2 节构造](../../../parallel/openmp/2-4-2-sections-construct.md)。

### <a name="example"></a>示例

```cpp
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

## <a name="single"></a><a name="single"></a>单

允许您指定应在单个线程（不一定是主线程）上执行代码部分。

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>参数

*第*<br/>
（可选）零个或多个子句，请参阅**备注**部分。

### <a name="remarks"></a>备注

该`single`指令支持以下子句：

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [不等待](openmp-clauses.md#nowait)

主[指令](#master)允许您指定代码部分应仅在主线程上执行。

有关详细信息，请参阅[2.4.3 单构造](../../../parallel/openmp/2-4-3-single-construct.md)。

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

## <a name="threadprivate"></a><a name="threadprivate"></a>线程私有

指定变量是线程的私有变量。

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>参数

*var*<br/>
要对线程进行私有的变量的逗号分隔列表。 *var*必须是全局或命名空间作用域变量或本地静态变量。

### <a name="remarks"></a>备注

该`threadprivate`指令不支持任何子句。

该`threadprivate`指令基于使用[__declspec](../../../cpp/declspec.md)关键字的[线程](../../../cpp/thread.md)属性;对`__declspec(thread)`的限制`threadprivate`适用于 。 例如，`threadprivate`变量将存在于进程中启动的任何线程中，而不仅仅是由并行区域生成的线程团队的线程的线程。 请注意此实现详细信息;您可能会注意到，`threadprivate`用户定义的类型的构造函数调用的频率比预期时要频繁。

您可以在进程启动`threadprivate`时静态加载的 DLL 中使用，但是不能在将通过[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)加载`threadprivate`的任何 DLL 中使用，例如加载[/DELAYLOAD（延迟加载导入）的](../../../build/reference/delayload-delay-load-import.md)DLL，后者也使用`LoadLibrary`。

`threadprivate`*可析构*类型的变量不能保证调用其析构函数。 例如：

```cpp
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

用户无法控制构成并行区域的线程何时将终止。 如果进程退出时存在这些线程，则不会通知线程进程退出，并且除退出的线程（此处是主线程）之外的任何线程`threaded_var`上不会调用析构函数。 因此，代码不应指望变量的正确`threadprivate`销毁。

有关详细信息，请参阅[2.7.1 线程专用指令](../../../parallel/openmp/2-7-1-threadprivate-directive.md)。

### <a name="example"></a>示例

有关 使用`threadprivate`的示例，请参阅[私有](openmp-clauses.md#private-openmp)。
