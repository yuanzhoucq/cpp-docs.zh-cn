---
title: omp_set_nested |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_set_nested OpenMP function
ms.assetid: fa1cb08c-7b8b-42c9-8654-2c33dcffb5b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc3506c35dca469febafe21509064abc1726d633
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116875"
---
# <a name="ompsetnested"></a>omp_set_nested
启用嵌套并行度。  
  
## <a name="syntax"></a>语法  
  
```  
void omp_set_nested(  
   int val  
);  
```  
  
### <a name="parameters"></a>参数
  
*val*<br/>
如果非零，使嵌套的并行度。 如果为零，则禁用嵌套并行度。  
  
## <a name="remarks"></a>备注  
 OMP 嵌套并行度可以与开启`omp_set_nested`，或通过设置[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)环境变量。  
  
 设置`omp_set_nested`将覆盖的设置`OMP_NESTED`环境变量。  
  
 启用时，环境变量可以中断否则为正常运行的程序，因为线程数以指数方式增加嵌套并行区域时。  例如 recurses 6 次，并将设置为 4 的 OMP 线程数，需要 4096 (4 到 6 的强大功能) 的函数线程通常情况下，应用程序的性能会降低，如果线程数超过处理器的数量。 一个例外就是 I/O 绑定应用程序。  
  
 使用[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)若要显示的当前设置`omp_set_nested`。  
  
 有关详细信息，请参阅[3.1.9 omp_set_nested 函数](../../../parallel/openmp/3-1-9-omp-set-nested-function.md)。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>请参阅  
 [函数](../../../parallel/openmp/reference/openmp-functions.md)