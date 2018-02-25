---
title: "omp_set_nested |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_set_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_set_nested OpenMP function
ms.assetid: fa1cb08c-7b8b-42c9-8654-2c33dcffb5b6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9fa669874d412df5ccf431217ed56fc3d746dc8e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ompsetnested"></a>omp_set_nested
启用嵌套并行度。  
  
## <a name="syntax"></a>语法  
  
```  
void omp_set_nested(  
   int val  
);  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `val`  
 如果不为零，使嵌套的并行度。 如果为零，则禁用嵌套并行度。  
  
## <a name="remarks"></a>备注  
 OMP 嵌套并行可以与开启`omp_set_nested`，或通过设置[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)环境变量。  
  
 有关设置`omp_set_nested`将替代的设置`OMP_NESTED`环境变量。  
  
 启用时，环境变量可以中断程序否则为操作，因为的线程数以指数级增加嵌套并行区域时。  例如 6 次，并将设置为 4 的 OMP 线程数 recurses 需要 4096 (4 的 6 次幂) 的函数线程一般情况下，你的应用程序的性能，如果线程数超过处理器的数目将会降低。 一个例外将 I/O 绑定应用程序。  
  
 使用[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)要显示的当前设置`omp_set_nested`。  
  
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