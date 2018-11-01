---
title: A.16   使用锁
ms.date: 11/04/2016
ms.assetid: 873bf32b-6cfe-4ce1-b994-bef80b50f399
ms.openlocfilehash: 6afb94660acdc79ea5a7eb61d3bf7e21fd70d751
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458976"
---
# <a name="a16---using-locks"></a>A.16   使用锁

在以下示例中，(对于[第 3.2 节](../../parallel/openmp/3-2-lock-functions.md)第 41 页上) 注意到的锁函数的参数应具有类型`omp_lock_t`，并且没有无需刷新它。  锁函数导致线程等待第一个关键部分中，进入时处于空闲状态，但若要完成其他工作的同时等待第二个条目。  `omp_set_lock`函数的块，但`omp_test_lock`函数不是，不允许在 $ skip （） 执行中的工作。

## <a name="example"></a>示例

### <a name="code"></a>代码

```
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