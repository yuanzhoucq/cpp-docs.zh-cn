---
title: OpenMP 函数
ms.date: 10/23/2018
f1_keywords:
- OpenMP functions
- omp_destroy_lock
- omp_destroy_nest_lock
- omp_get_dynamic
- omp_get_max_threads
- omp_get_nested
- omp_get_num_procs
- omp_get_num_threads
- omp_get_thread_num
- omp_get_wtick
- omp_get_wtime
- omp_in_parallel
- omp_init_lock
- omp_init_nest_lock
- omp_set_dynamic
- omp_set_lock
- omp_set_nest_lock
- omp_set_nested
- omp_set_num_threads
- omp_test_lock
- omp_test_nest_lock
- omp_unset_lock
- omp_unset_nest_lock
helpviewer_keywords:
- OpenMP functions
- omp_destroy_lock OpenMP function
- omp_destroy_nest_lock OpenMP function
- omp_get_dynamic OpenMP function
- omp_get_max_threads OpenMP function
- omp_get_nested OpenMP function
- omp_get_num_procs OpenMP function
- omp_get_num_threads OpenMP function
- omp_get_thread_num OpenMP function
- omp_get_wtick OpenMP function
- omp_get_wtime OpenMP function
- omp_in_parallel OpenMP function
- omp_init_lock OpenMP function
- omp_init_nest_lock OpenMP function
- omp_set_dynamic OpenMP function
- omp_set_lock OpenMP function
- omp_set_nest_lock OpenMP function
- omp_set_nested OpenMP function
- omp_set_num_threads OpenMP function
- omp_test_lock OpenMP function
- omp_test_nest_lock OpenMP function
- omp_unset_lock OpenMP function
- omp_unset_nest_lock OpenMP function
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
ms.openlocfilehash: 0435d75b69ea870db50739933245925d6860cbf9
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51333275"
---
# <a name="openmp-functions"></a>OpenMP 函数

提供指向 OpenMP API 中使用的函数。

OpenMP 标准的 Visual c + + 实现包括以下函数。

|函数|描述|
|--------|-----------|
|[omp_destroy_lock](#omp-destroy-lock)|取消初始化锁。|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|取消初始化可嵌套锁。|
|[omp_get_dynamic](#omp-get-dynamic)|返回一个值，该值指示是否的即将推出的并行区域中可用的线程数可以调整运行时。|
|[omp_get_max_threads](#omp-get-max-threads)|返回一个整数，如果无需并行区域可用的线程数大于或等于[num_threads](openmp-clauses.md#num-threads)此时在代码中定义。|
|[omp_get_nested](#omp-get-nested)|返回一个值，该值指示是否启用了嵌套并行度。|
|[omp_get_num_procs](#omp-get-num-procs)|返回调用函数时可用的处理器数。|
|[omp_get_num_threads](#omp-get-num-threads)|并行区域中返回线程的数。|
|[omp_get_thread_num](#omp-get-thread-num)|返回其线程团队中执行的线程的线程数。|
|[omp_get_wtick](#omp-get-wtick)|返回处理器时钟计时周期之间等待的秒数。|
|[omp_get_wtime](#omp-get-wtime)|返回从某一时刻已用的值以秒为单位的时间。|
|[omp_in_parallel](#omp-in-parallel)|返回非零，如果从并行区域内调用。|
|[omp_init_lock](#omp-init-lock)|初始化是简单的锁定。|
|[omp_init_nest_lock](#omp-init-nest-lock)|初始化一个锁。|
|[omp_set_dynamic](#omp-set-dynamic)|指示运行时可进行调整的即将推出的并行区域中可用的线程数。|
|[omp_set_lock](#omp-set-lock)|块线程执行，直到锁可用。|
|[omp_set_nest_lock](#omp-set-nest-lock)|块线程执行，直到锁可用。|
|[omp_set_nested](#omp-set-nested)|启用嵌套并行度。|
|[omp_set_num_threads](#omp-set-num-threads)|在即将发布的并行区域设置的线程数，除非被重写[num_threads](openmp-clauses.md#num-threads)子句。|
|[omp_test_lock](#omp-test-lock)|尝试设置一个锁，但不会阻止线程执行。|
|[omp_test_nest_lock](#omp-test-nest-lock)|尝试设置可嵌套锁，但不会阻止线程执行。|
|[omp_unset_lock](#omp-unset-lock)|释放锁。|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|释放可嵌套锁。|

## <a name="omp-destroy-lock"></a>omp_destroy_lock

取消初始化锁。

```
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
类型的变量[omp_lock_t](openmp-data-types.md#omp-lock-t)与初始化[omp_init_lock](#omp-init-lock)。

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函数](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。

### <a name="example"></a>示例

请参阅[omp_init_lock](#omp-init-lock)有关的使用示例`omp_destroy_lock`。

## <a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

取消初始化可嵌套锁。

```
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
类型的变量[omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t)与初始化[omp_init_nest_lock](#omp-init-nest-lock)。

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函数](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。

### <a name="example"></a>示例

请参阅[omp_init_nest_lock](#omp-init-nest-lock)有关的使用示例`omp_destroy_nest_lock`。

## <a name="omp-get-dynamic"></a>omp_get_dynamic

返回一个值，该值指示是否的即将推出的并行区域中可用的线程数可以调整运行时。

```
int omp_get_dynamic();
```

### <a name="return-value"></a>返回值

一个非零值意味着将动态调整线程。

### <a name="remarks"></a>备注

使用指定的线程的动态调整[omp_set_dynamic](#omp-set-dynamic)并[OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic)。

有关详细信息，请参阅[3.1.7 omp_set_dynamic 函数](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。

### <a name="example"></a>示例

请参阅[omp_set_dynamic](#omp-set-dynamic)有关的使用示例`omp_get_dynamic`。

## <a name="omp-get-max-threads"></a>omp_get_max_threads

返回一个整数，如果无需并行区域可用的线程数大于或等于[num_threads](openmp-clauses.md#num-threads)此时在代码中定义。

```
int omp_get_max_threads( )
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.1.3 omp_get_max_threads 函数](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md)。

### <a name="example"></a>示例

```
// omp_get_max_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(8);
    printf_s("%d\n", omp_get_max_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));
}
```

```Output
8
8
8
8
8
```

## <a name="omp-get-nested"></a>omp_get_nested

返回一个值，该值指示是否启用了嵌套并行度。

```
int omp_get_nested( );
```

### <a name="return-value"></a>返回值

一个非零值表示启用嵌套的并行度。

### <a name="remarks"></a>备注

使用指定嵌套并行度[omp_set_nested](#omp-set-nested)并[OMP_NESTED](openmp-environment-variables.md#omp-nested)。

有关详细信息，请参阅[3.1.10 omp_get_nested 函数](../../../parallel/openmp/3-1-10-omp-get-nested-function.md)。

### <a name="example"></a>示例

请参阅[omp_set_nested](#omp-set-nested)有关的使用示例`omp_get_nested`。

## <a name="omp-get-num-procs"></a>omp_get_num_procs

返回调用函数时可用的处理器数。

```
int omp_get_num_procs();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.1.5 omp_get_num_procs 函数](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md)。

### <a name="example"></a>示例

```
// omp_get_num_procs.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    printf_s("%d\n", omp_get_num_procs( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_procs( ));
        }
}
```

```Output
// Expect the following output when the example is run on a two-processor machine:
2
2
```

## <a name="omp-get-num-threads"></a>omp_get_num_threads

并行区域中返回线程的数。

```
int omp_get_num_threads( );
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.1.2 omp_get_num_threads 函数](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)。

### <a name="example"></a>示例

```
// omp_get_num_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_num_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));
}
```

```Output
1
4
1
3
1
```

## <a name="omp-get-thread-num"></a>omp_get_thread_num

返回其线程团队中执行的线程的线程数。

```
int omp_get_thread_num( );
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.1.4 omp_get_thread_num 函数](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md)。

### <a name="example"></a>示例

请参阅[并行](openmp-directives.md#parallel)有关的使用示例`omp_get_thread_num`。

## <a name="omp-get-wtick"></a>omp_get_wtick

返回处理器时钟计时周期之间等待的秒数。

```
double omp_get_wtick( );
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.3.2 omp_get_wtick 函数](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md)。

### <a name="example"></a>示例

请参阅[omp_get_wtime](#omp-get-wtime)有关的使用示例`omp_get_wtick`。

## <a name="omp-get-wtime"></a>omp_get_wtime

返回从某一时刻已用的值以秒为单位的时间。

```
double omp_get_wtime( );
```

### <a name="return-value"></a>返回值

返回一个值以秒为单位的时间已用从一些任意的但一致的点。

### <a name="remarks"></a>备注

在程序执行，使得即将推出的比较过程，该点将保持一致。

有关详细信息，请参阅[3.3.1 omp_get_wtime 函数](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md)。

### <a name="example"></a>示例

```
// omp_get_wtime.cpp
// compile with: /openmp
#include "omp.h"
#include <stdio.h>
#include <windows.h>

int main() {
    double start = omp_get_wtime( );
    Sleep(1000);
    double end = omp_get_wtime( );
    double wtick = omp_get_wtick( );

    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",
             start, end, end - start);

    printf_s("wtick = %.16g\n1/wtick = %.16g\n",
             wtick, 1.0 / wtick);
}
```

```Output
start = 594255.3671159324
end = 594256.3664474116
diff = 0.9993314791936427
wtick = 2.793651148400146e-007
1/wtick = 3579545
```

## <a name="omp-in-parallel"></a>omp_in_parallel

返回非零，如果从并行区域内调用。

```
int omp_in_parallel( );
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.1.6 omp_in_parallel 函数](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md)。

### <a name="example"></a>示例

```
// omp_in_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_in_parallel( ));

    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_in_parallel( ));
        }
}
```

```Output
0
1
```

## <a name="omp-init-lock"></a>omp_init_lock

初始化是简单的锁定。

```
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
类型的变量[omp_lock_t](openmp-data-types.md#omp-lock-t)。

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.2.1 omp_init_lock 和 omp_init_nest_lock 函数](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)。

### <a name="example"></a>示例

```
// omp_init_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t my_lock;

int main() {
   omp_init_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num( );
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_lock(&my_lock);
         printf_s("Thread %d - starting locked region\n", tid);
         printf_s("Thread %d - ending locked region\n", tid);
         omp_unset_lock(&my_lock);
      }
   }

   omp_destroy_lock(&my_lock);
}
```

```Output
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
```

## <a name="omp-init-nest-lock"></a>omp_init_nest_lock

初始化一个锁。

```
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
类型的变量[omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t)。

### <a name="remarks"></a>备注

初始嵌套计数为零。

有关详细信息，请参阅[3.2.1 omp_init_lock 和 omp_init_nest_lock 函数](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)。

### <a name="example"></a>示例

```
// omp_init_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t my_lock;

void Test() {
   int tid = omp_get_thread_num( );
   omp_set_nest_lock(&my_lock);
   printf_s("Thread %d - starting nested locked region\n", tid);
   printf_s("Thread %d - ending nested locked region\n", tid);
   omp_unset_nest_lock(&my_lock);
}

int main() {
   omp_init_nest_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_nest_lock(&my_lock);
            if (i % 3)
               Test();
            omp_unset_nest_lock(&my_lock);
        }
    }

    omp_destroy_nest_lock(&my_lock);
}
```

```Output
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
```

## <a name="omp-set-dynamic"></a>omp_set_dynamic

指示运行时可进行调整的即将推出的并行区域中可用的线程数。

```
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>参数

*val*<br/>
一个值，指示是否可以通过在运行时调整在即将发布的并行区域中可用的线程数。  如果非零，则运行时可以调整的线程数，如果为零，则运行时不会动态调整线程数。

### <a name="remarks"></a>备注

线程数将永远不会超出设置的值[omp_set_num_threads](#omp-set-num-threads)或通过[OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads)。

使用[omp_get_dynamic](#omp-get-dynamic)若要显示的当前设置`omp_set_dynamic`。

设置`omp_set_dynamic`将覆盖的设置[OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic)环境变量。

有关详细信息，请参阅[3.1.7 omp_set_dynamic 函数](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。

### <a name="example"></a>示例

```
// omp_set_dynamic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_dynamic(9);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_dynamic( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_dynamic( ));
        }
}
```

```Output
1
1
```

## <a name="omp-set-lock"></a>omp_set_lock

块线程执行，直到锁可用。

```
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
类型的变量[omp_lock_t](openmp-data-types.md#omp-lock-t)与初始化[omp_init_lock](#omp-init-lock)。

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.2.3 omp_set_lock 和 omp_set_nest_lock 函数](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。

### <a name="examples"></a>示例

请参阅[omp_init_lock](#omp-init-lock)有关的使用示例`omp_set_lock`。

## <a name="omp-set-nest-lock"></a>omp_set_nest_lock

块线程执行，直到锁可用。

```
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
类型的变量[omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t)与初始化[omp_init_nest_lock](#omp-init-nest-lock)。

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.2.3 omp_set_lock 和 omp_set_nest_lock 函数](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。

### <a name="examples"></a>示例

请参阅[omp_init_nest_lock](#omp-init-nest-lock)有关的使用示例`omp_set_nest_lock`。

## <a name="omp-set-nested"></a>omp_set_nested

启用嵌套并行度。

```
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>参数

*val*<br/>
一个非零值使嵌套并行性，而零禁用嵌套并行度。

### <a name="remarks"></a>备注

OMP 嵌套并行度可以与开启`omp_set_nested`，或通过设置[OMP_NESTED](openmp-environment-variables.md#omp-nested)环境变量。

设置`omp_set_nested`将覆盖的设置`OMP_NESTED`环境变量。

由于线程数以指数方式增加嵌套并行区域时，启用环境变量可能会中断是否则为正常运行的程序。  例如，将设置为 4 的 OMP 线程数与递归六次的函数需要 4096 (4 到 6 的强大功能) 线程。 除使用 O 绑定的应用程序，应用程序的性能通常会降低如果有更多个处理器的线程。

使用[omp_get_nested](#omp-get-nested)若要显示的当前设置`omp_set_nested`。

有关详细信息，请参阅[3.1.9 omp_set_nested 函数](../../../parallel/openmp/3-1-9-omp-set-nested-function.md)。

### <a name="example"></a>示例

```
// omp_set_nested.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_nested(1);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_nested( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_nested( ));
        }
}
```

```Output
1
1
```

## <a name="omp-set-num-threads"></a>omp_set_num_threads

在即将发布的并行区域设置的线程数，除非被重写[num_threads](openmp-clauses.md#num-threads)子句。

```
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>参数

*num_threads*<br/>
并行区域中的线程数。

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.1.1 omp_set_num_threads 函数](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)。

### <a name="example"></a>示例

请参阅[omp_get_num_threads](#omp-get-num-threads)有关的使用示例`omp_set_num_threads`。

## <a name="omp-test-lock"></a>omp_test_lock

尝试设置一个锁，但不会阻止线程执行。

```
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
类型的变量[omp_lock_t](openmp-data-types.md#omp-lock-t)与初始化[omp_init_lock](#omp-init-lock)。

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.2.5 omp_test_lock 和 omp_test_nest_lock 函数](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)。

### <a name="example"></a>示例

```
// omp_test_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t simple_lock;

int main() {
    omp_init_lock(&simple_lock);

    #pragma omp parallel num_threads(4)
    {
        int tid = omp_get_thread_num();

        while (!omp_test_lock(&simple_lock))
            printf_s("Thread %d - failed to acquire simple_lock\n",
                     tid);

        printf_s("Thread %d - acquired simple_lock\n", tid);

        printf_s("Thread %d - released simple_lock\n", tid);
        omp_unset_lock(&simple_lock);
    }

    omp_destroy_lock(&simple_lock);
}
```

```Output
Thread 1 - acquired simple_lock
Thread 1 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - acquired simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - acquired simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - released simple_lock
Thread 3 - failed to acquire simple_lock
Thread 3 - acquired simple_lock
Thread 3 - released simple_lock
```

## <a name="omp-test-nest-lock"></a>omp_test_nest_lock

尝试设置可嵌套锁，但不会阻止线程执行。

```
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
类型的变量[omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t)与初始化[omp_init_nest_lock](#omp-init-nest-lock)。

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.2.5 omp_test_lock 和 omp_test_nest_lock 函数](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)。

### <a name="example"></a>示例

```
// omp_test_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t nestable_lock;

int main() {
   omp_init_nest_lock(&nestable_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num();
      while (!omp_test_nest_lock(&nestable_lock))
         printf_s("Thread %d - failed to acquire nestable_lock\n",
                tid);

      printf_s("Thread %d - acquired nestable_lock\n", tid);

      if (omp_test_nest_lock(&nestable_lock)) {
         printf_s("Thread %d - acquired nestable_lock again\n",
                tid);
         printf_s("Thread %d - released nestable_lock\n",
                tid);
         omp_unset_nest_lock(&nestable_lock);
      }

      printf_s("Thread %d - released nestable_lock\n", tid);
      omp_unset_nest_lock(&nestable_lock);
   }

   omp_destroy_nest_lock(&nestable_lock);
}
```

```Output
Thread 1 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock again
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - acquired nestable_lock
Thread 2 - acquired nestable_lock again
Thread 2 - released nestable_lock
Thread 2 - released nestable_lock
```

## <a name="omp-unset-lock"></a>omp_unset_lock

释放锁。

```
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
类型的变量[omp_lock_t](openmp-data-types.md#omp-lock-t)与初始化[omp_init_lock](#omp-init-lock)、 由线程拥有和函数中执行。

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函数](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。

### <a name="example"></a>示例

请参阅[omp_init_lock](#omp-init-lock)有关的使用示例`omp_unset_lock`。

## <a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

释放可嵌套锁。

```
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
类型的变量[omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t)与初始化[omp_init_nest_lock](#omp-init-nest-lock)、 由线程拥有和函数中执行。

### <a name="remarks"></a>备注

有关详细信息，请参阅[3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函数](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。

### <a name="example"></a>示例

请参阅[omp_init_nest_lock](#omp-init-nest-lock)有关的使用示例`omp_unset_nest_lock`。
