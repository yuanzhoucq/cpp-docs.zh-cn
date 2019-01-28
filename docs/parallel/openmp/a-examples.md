---
title: 答： 示例
ms.date: 01/18/2019
ms.assetid: c0f6192f-a205-449b-b84c-cb30dbcc8b8f
ms.openlocfilehash: 061490d34829175bfbdcd84d6208aa396bb19671
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087296"
---
# <a name="a-examples"></a>答： 示例

以下是本文档中定义的构造的示例。 仅当有必要，复合指令后的语句，非复合语句从其前面的指令缩进。

## <a name="a1-a-simple-loop-in-parallel"></a>A.1 并行的一个简单循环

下面的示例演示如何并行化循环使用[并行的](2-directives.md#251-parallel-for-construct)指令。 循环迭代变量是默认情况下，专用的因此无需显式指定 private 子句中。

```cpp
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```

## <a name="a2-conditional-compilation"></a>A.2 条件编译

下面的示例说明如何使用条件编译使用 OpenMP 宏[_OPENMP](2-directives.md#22-conditional-compilation)。 与 OpenMP 编译`_OPENMP`将成为定义宏。

```cpp
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

定义预处理器运算符允许多个要测试单个指令中的宏。

```cpp
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

## <a name="a3-parallel-regions"></a>A.3 并行区域

[并行](2-directives.md#23-parallel-construct)指令可用于在粗粒度的并行程序中。 在以下示例中，每个线程中并行区域决定全局数组的哪个部分`x`，工作线程数：

```cpp
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```

## <a name="a4-the-nowait-clause"></a>A.4 nowait 子句

如果有多个独立循环并行区域内的，则可以使用[nowait](2-directives.md#241-for-construct)子句以避免隐式末尾的屏障`for`指令，如下所示：

```cpp
#pragma omp parallel
{
    #pragma omp for nowait
        for (i=1; i<n; i++)
             b[i] = (a[i] + a[i-1]) / 2.0;
    #pragma omp for nowait
        for (i=0; i<m; i++)
            y[i] = sqrt(z[i]);
}
```

## <a name="a5-the-critical-directive"></a>A.5 critical 指令

下面的示例包括若干[关键](2-directives.md#262-critical-construct)指令。 该示例阐释了队列的模型在其中取消排队和从事一项任务。 若要防止多个线程取消排队相同的任务，取消排队操作必须为`critical`部分。 由于在此示例中的两个队列都是独立的它们受到`critical`具有不同名称的指令*xaxis*并*y 轴*。

```cpp
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```

## <a name="a6-the-lastprivate-clause"></a>A.6 lastprivate 子句

有时正确的执行取决于循环的最后一次迭代将赋给变量的值。 此类程序必须列出所有此类变量作为参数[lastprivate](2-directives.md#2723-lastprivate)子句，以便变量的值将与按顺序执行循环时相同。

```cpp
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

在前面的示例中，值`i`末尾的并行区域将等于`n-1`，如下所示的顺序的情况。

## <a name="a7-the-reduction-clause"></a>A.7 reduction 子句

下面的示例演示[减少](2-directives.md#2726-reduction)子句：

```cpp
#pragma omp parallel for private(i) shared(x, y, n) \
                         reduction(+: a, b)
    for (i=0; i<n; i++) {
        a = a + x[i];
        b = b + y[i];
    }
```

## <a name="a8-parallel-sections"></a>A.8 并行段

在下面的示例 (对于[部分 2.4.2](2-directives.md#242-sections-construct))，函数*xaxis*， *y 轴*，以及*zaxis*可以并发执行。 第一个`section`指令是可选的。  所有`section`指令需要出现在的词法范围`parallel sections`构造。

```cpp
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```

## <a name="a9-single-directives"></a>A.9 Single 指令

下面的示例演示[单个](2-directives.md#243-single-construct)指令。 在示例中，只有一个线程 (通常遇到的第一个线程`single`指令) 打印进度消息。 用户必须对哪个线程将执行不进行任何假设`single`部分。 所有其他线程将跳过`single`部分，并在末尾的屏障停止`single`构造。 如果其他线程会继续运行而无需等待执行的线程`single`部分中，`nowait`子句可以指定在`single`指令。

```cpp
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```

## <a name="a10-sequential-ordering"></a>A.10 顺序排序

[排序部分](2-directives.md#266-ordered-construct)可用于按顺序排序的输出具有并行完成的工作。 以下程序将输出按顺序排列的索引：

```cpp
#pragma omp for ordered schedule(dynamic)
    for (i=lb; i<ub; i+=st)
        work(i);
void work(int k)
{
    #pragma omp ordered
        printf_s(" %d", k);
}
```

## <a name="a11-a-fixed-number-of-threads"></a>A.11 一个固定线程的数

某些程序依赖于固定的预先指定的正确执行的线程数。  指动态调整的线程数的默认设置是实现定义的因为此类程序可以选择关闭动态线程功能，并设置显式要保持可移植性的线程数。 下面的示例演示如何执行此操作使用[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)，并[omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function):

```cpp
omp_set_dynamic(0);
omp_set_num_threads(16);
#pragma omp parallel shared(x, npoints) private(iam, ipoints)
{
    if (omp_get_num_threads() != 16)
      abort();
    iam = omp_get_thread_num();
    ipoints = npoints/16;
    do_by_16(x, iam, ipoints);
}
```

在此示例中，程序才会执行正确通过 16 个线程执行。 如果对实现进行能够支持 16 个线程，此示例中的行为是实现定义的。

在并行区域，而不考虑动态线程设置期间，执行并行区域的线程数量保持不变。 动态线程机制确定要使用并行区域开始时的线程数并将其保留常量区域的持续时间。

## <a name="a12-the-atomic-directive"></a>A.12 atomic 指令

下面的示例可避免争用条件 (同时进行更新的元素*x*由多个线程) 通过使用[原子](2-directives.md#264-atomic-construct)指令：

```cpp
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

使用的优点`atomic`指令在此示例中是允许更新的 x 会并行发生两个不同元素。 如果[关键](2-directives.md#262-critical-construct)然后所有更新的元素到相反，使用指令*x*按顺序 （尽管不在任何有保证的顺序） 执行。

`atomic`指令仅适用于紧随的 C 或 c + + 语句。  因此中的元素*y*不会在此示例中以原子方式更新。

## <a name="a13-a-flush-directive-with-a-list"></a>A.13 一个列表的 flush 指令

下面的示例使用`flush`指令为特定对象对的线程之间的点到点同步：

```cpp
int   sync[NUMBER_OF_THREADS];
float work[NUMBER_OF_THREADS];
#pragma omp parallel private(iam,neighbor) shared(work,sync)
{
    iam = omp_get_thread_num();
    sync[iam] = 0;
    #pragma omp barrier

    // Do computation into my portion of work array
    work[iam] = ...;

    //  Announce that I am done with my work
    // The first flush ensures that my work is
    // made visible before sync.
    // The second flush ensures that sync is made visible.
    #pragma omp flush(work)
    sync[iam] = 1;
    #pragma omp flush(sync)

    // Wait for neighbor
    neighbor = (iam>0 ? iam : omp_get_num_threads()) - 1;
    while (sync[neighbor]==0)
    {
        #pragma omp flush(sync)
    }

    // Read neighbor's values of work array
    ... = work[neighbor];
}
```

## <a name="a14-a-flush-directive-without-a-list"></a>A.14 一个不带列表的 flush 指令

下面的示例 (对于[部分 2.6.5](2-directives.md#265-flush-directive)) 将受影响的共享的对象区分开来`flush`指令与不受影响的共享对象中没有列表：

```cpp
// omp_flush_without_list.c
#include <omp.h>

int x, *p = &x;

void f1(int *q)
{
    *q = 1;
    #pragma omp flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

void f2(int *q)
{
    #pragma omp barrier
    *q = 2;

    #pragma omp barrier
    // a barrier implies a flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

int g(int n)
{
    int i = 1, j, sum = 0;
    *p = 1;

    #pragma omp parallel reduction(+: sum) num_threads(10)
    {
        f1(&j);
        // i, n and sum were not flushed
        //   because they were not accessible in f1
        // j was flushed because it was accessible
        sum += j;
        f2(&j);
        // i, n, and sum were not flushed
        //   because they were not accessible in f2
        // j was flushed because it was accessible
        sum += i + j + *p + n;
    }
    return sum;
}

int main()
{
}
```

## <a name="a15-the-number-of-threads-used"></a>A.15 使用的线程数

请考虑以下不正确的示例 (对于[第 3.1.2 节](3-run-time-library-functions.md#312-omp_get_num_threads-function)):

```cpp
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

`omp_get_num_threads()`串行节的代码，因此调用返回 1 *np*始终将等于 1 在前面的示例。 若要确定将为并行区域部署的线程数，请调用应并行区域内。

下面的示例演示如何重写此程序，而不包含查询的线程数：

```cpp
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```

## <a name="a16-locks"></a>A.16 锁

在下面的示例 (对于[部分 3.2](3-run-time-library-functions.md#32-lock-functions))，锁定函数的参数应具有类型`omp_lock_t`，并且没有无需刷新它。  锁函数导致线程等待第一个关键部分中，进入时处于空闲状态，但若要完成其他工作的同时等待第二个条目。  `omp_set_lock`函数的块，但`omp_test_lock`函数不会允许在工作`skip()`即可。

```cpp
// omp_using_locks.c
// compile with: /openmp /c
#include <stdio.h>
#include <omp.h>

void work(int);
void skip(int);

int main() {
   omp_lock_t lck;
   int id;

   omp_init_lock(&lck);
   #pragma omp parallel shared(lck) private(id)
   {
      id = omp_get_thread_num();

      omp_set_lock(&lck);
      printf_s("My thread id is %d.\n", id);

      // only one thread at a time can execute this printf
      omp_unset_lock(&lck);

      while (! omp_test_lock(&lck)) {
         skip(id);   // we do not yet have the lock,
                     // so we must do something else
      }
      work(id);     // we now have the lock
                    // and can do the work
      omp_unset_lock(&lck);
   }
   omp_destroy_lock(&lck);
}
```

## <a name="a17-nestable-locks"></a>A.17 可嵌套锁

下面的示例 (对于[部分 3.2](3-run-time-library-functions.md#32-lock-functions)) 演示如何使用可嵌套锁来同步更新到整个结构和为其成员之一。

```cpp
#include <omp.h>
typedef struct {int a,b; omp_nest_lock_t lck;} pair;

void incr_a(pair *p, int a)
{
    // Called only from incr_pair, no need to lock.
    p->a += a;
}

void incr_b(pair *p, int b)
{
    // Called both from incr_pair and elsewhere,
    // so need a nestable lock.

    omp_set_nest_lock(&p->lck);
    p->b += b;
    omp_unset_nest_lock(&p->lck);
}

void incr_pair(pair *p, int a, int b)
{
    omp_set_nest_lock(&p->lck);
    incr_a(p, a);
    incr_b(p, b);
    omp_unset_nest_lock(&p->lck);
}

void f(pair *p)
{
    extern int work1(), work2(), work3();
    #pragma omp parallel sections
    {
        #pragma omp section
            incr_pair(p, work1(), work2());
        #pragma omp section
            incr_b(p, work3());
    }
}
```

## <a name="a18-nested-for-directives"></a>A.18 嵌套的指令

下面的示例对`for`[指令嵌套](2-directives.md#29-directive-nesting)兼容因为内部和外部`for`指令将绑定到不同的并行区域：

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
        {
            #pragma omp parallel shared(i, n)
            {
                #pragma omp for
                    for (j=0; j<n; j++)
                        work(i, j);
            }
        }
}
```

此外，还符合前面的示例中的以下变体：

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
            work1(i, n);
}

void work1(int i, int n)
{
    int j;
    #pragma omp parallel default(shared)
    {
        #pragma omp for
            for (j=0; j<n; j++)
                work2(i, j);
    }
    return;
}
```

## <a name="a19-examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19 示例显示不正确嵌套的工作共享指令

在本部分中的示例演示了[指令嵌套](2-directives.md#29-directive-nesting)规则。

下面的示例是不符合要求因为内部和外部`for`指令嵌套的并且将绑定到相同`parallel`指令：

```cpp
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

前面中的以下动态嵌套的版本也是示例的不符合要求的：

```cpp
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

下面的示例是不符合要求由于`for`和`single`嵌套的指令，并且它们将绑定到同一个并行区域：

```cpp
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

下面的示例是不符合要求由于`barrier`内`for`可能会导致死锁：

```cpp
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

下面的示例是不符合要求因为`barrier`导致死锁，因为，一次只有一个线程可以进入关键节：

```cpp
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

下面的示例是不符合要求由于`barrier`导致死锁，因为，只有一个线程执行`single`部分：

```cpp
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```

## <a name="a20-bind-barrier-directives"></a>A.20 barrier 指令绑定

指令的绑定规则调用`barrier`指令将绑定到最接近封闭`parallel`指令。 指令的绑定的详细信息，请参阅[部分 2.8](2-directives.md#28-directive-binding)。

在下面的示例中，从调用*主要*到*sub2 来*兼容因为`barrier`(中*sub3*) 将绑定到并行区域*sub2 报表*. 从调用*主要*到*sub1*兼容因为`barrier`将绑定到子例程中的并行区域*sub2 来*。  从调用*主要*到*sub3*兼容因为`barrier`不会将绑定到任何并行区域并将被忽略。 此外，`barrier`仅同步封闭并行区域中的线程和中创建的不是所有线程的团队*sub1*。

```cpp
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```

## <a name="a21-scope-variables-with-the-private-clause"></a>A.21 使用 private 子句设置作用域变量

值`i`和`j`在以下示例中未定义在从并行区域退出：

```cpp
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

有关详细信息`private`子句，请参阅[部分 2.7.2.1](2-directives.md#2721-private)。

## <a name="a22-the-defaultnone-clause"></a>A.22 default （none） 子句

下面的示例用于区分受影响的变量`default(none)`子句不是变量中：

```cpp
// openmp_using_clausedefault.c
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int x, y, z[1000];
#pragma omp threadprivate(x)

void fun(int a) {
   const int c = 1;
   int i = 0;

   #pragma omp parallel default(none) private(a) shared(z)
   {
      int j = omp_get_num_thread();
             //O.K.  - j is declared within parallel region
      a = z[j];       // O.K.  - a is listed in private clause
                      //      - z is listed in shared clause
      x = c;          // O.K.  - x is threadprivate
                      //      - c has const-qualified type
      z[i] = y;       // C3052 error - cannot reference i or y here

      #pragma omp for firstprivate(y)
         for (i=0; i<10 ; i++) {
            z[i] = y;  // O.K. - i is the loop control variable
                       // - y is listed in firstprivate clause
          }
       z[i] = y;   // Error - cannot reference i or y here
   }
}
```

有关详细信息`default`子句，请参阅[部分 2.7.2.5](2-directives.md#2725-default)。

## <a name="a23-examples-of-the-ordered-directive"></a>A.23 ordered 指令的示例

可以有多个有序的部分`for`与指定`ordered`子句。 第一个示例是不符合要求，因为 API 指定以下规则：

"具有循环的迭代`for`构造必须执行相同`ordered`指令超过一次，并且它必须执行多个`ordered`指令。" (请参阅[部分 2.6.6](2-directives.md#266-ordered-construct)。)

在此不符合要求的示例中，所有迭代都执行两个有序的部分：

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

下面的示例符合`for`与多个有序部分：

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```

## <a name="a24-example-of-the-private-clause"></a>A.24 private 子句的示例

[专用](2-directives.md#2721-private)子句并行区域是仅在影响词法范围内的区域，而不适用于区域的动态范围中。  因此，在以下示例中，使用该变量的任何内`for`例程中的循环*f*的私有副本是指，while 中的使用情况例程*g*引用全局。

```cpp
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```

## <a name="a25-examples-of-the-copyprivate-data-attribute-clause"></a>A.25 copyprivate 数据特性子句示例

**示例 1:**[Copyprivate](2-directives.md#2728-copyprivate)子句可用于广播由单线程直接向私有变量在其他线程中的所有实例获取的值。

```cpp
float x, y;
#pragma omp threadprivate(x, y)

void init( )
{
    float a;
    float b;

    #pragma omp single copyprivate(a,b,x,y)
    {
        get_values(a,b,x,y);
    }

    use_values(a, b, x, y);
}
```

如果例行*init*称为从串行区域，其行为不受影响的指令的存在。 在调用*get_values*例程已执行由一个线程，没有线程直到指定的专用对象使构造， *b*， *x*，并*y*中所有线程变得与定义为具有读取的值。

**示例 2:** 与前面的示例，假设必须由特定线程，说的主线程执行读取。 在这种情况下，`copyprivate`子句不能用于执行广播直接，但它可用于提供对临时共享对象的访问。

```cpp
float read_next( )
{
    float * tmp;
    float return_val;

    #pragma omp single copyprivate(tmp)
    {
        tmp = (float *) malloc(sizeof(float));
    }

    #pragma omp master
    {
        get_float( tmp );
    }

    #pragma omp barrier
    return_val = *tmp;
    #pragma omp barrier

    #pragma omp single
    {
       free(tmp);
    }

    return return_val;
}
```

**示例 3:** 假设并行区域内所需的锁对象的数目不能轻松地确定之前输入它。 `copyprivate`子句可用于提供对该并行区域内分配的共享的锁对象的访问。

```cpp
#include <omp.h>

omp_lock_t *new_lock()
{
    omp_lock_t *lock_ptr;

    #pragma omp single copyprivate(lock_ptr)
    {
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));
        omp_init_lock( lock_ptr );
    }

    return lock_ptr;
}
```

## <a name="a26-the-threadprivate-directive"></a>A.26 threadprivate 指令

下面的示例演示如何使用[threadprivate](2-directives.md#271-threadprivate-directive)指令，以便为每个线程提供单独的计数器。

### <a name="example-1"></a>示例 1

```cpp
int counter = 0;
#pragma omp threadprivate(counter)

int sub()
{
    counter++;
    return(counter);
}
```

### <a name="example-2"></a>示例 2

```cpp
int sub()
{
    static int counter = 0;
    #pragma omp threadprivate(counter)
    counter++;
    return(counter);
}
```

## <a name="a27-c99-variable-length-arrays"></a>A.27 C99 可变长度数组

下面的示例演示如何使用 C99 变量长度数组 (VLAs) 中[firstprivate](2-directives.md#2722-firstprivate)指令。

> [!NOTE]
> 在 Visual c + + 中目前不支持可变长度数组。

```cpp
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```

## <a name="a28-the-numthreads-clause"></a>A.28 num_threads 子句

下面的示例演示[num_threads](2-directives.md#23-parallel-construct)子句。 并行区域最多 10 个线程执行。

```cpp
#include <omp.h>
main()
{
    omp_set_dynamic(1);
    ...
    #pragma omp parallel num_threads(10)
    {
        ... parallel region ...
    }
}
```

## <a name="a29-work-sharing-constructs-inside-a-critical-construct"></a>A.29 critical 构造内的工作共享构造

下面的示例演示了如何使用内部的工作共享构造`critical`构造。 此示例是符合的因为工作共享构造和`critical`构造没有将绑定到同一个并行区域。

```cpp
void f()
{
  int i = 1;
  #pragma omp parallel sections
  {
    #pragma omp section
    {
      #pragma omp critical (name)
      {
        #pragma omp parallel
        {
          #pragma omp single
          {
            i++;
          }
        }
      }
    }
  }
}
```

## <a name="a30-reprivatization"></a>A.30 重新私有化

下面的示例演示如何重新私有化的变量。 可以标记为私有变量`private`再次在嵌套指令中。 无需共享封闭并行区域中的这些变量。

```cpp
int i, a;
...
#pragma omp parallel private(a)
{
  ...
  #pragma omp parallel for private(a)
  for (i=0; i<10; i++)
     {
       ...
     }
}
```

## <a name="a31-thread-safe-lock-functions"></a>A.31 线程安全的锁函数

下面的 c + + 示例演示如何通过使用初始化数组的并行区域中的锁[omp_init_lock](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions)。

```cpp
// A_13_omp_init_lock.cpp
// compile with: /openmp
#include <omp.h>

omp_lock_t *new_locks() {
   int i;
   omp_lock_t *lock = new omp_lock_t[1000];
   #pragma omp parallel for private(i)
   for (i = 0 ; i < 1000 ; i++)
      omp_init_lock(&lock[i]);

   return lock;
}

int main () {}
```
