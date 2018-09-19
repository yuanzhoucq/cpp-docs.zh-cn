---
title: 原子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- atomic
dev_langs:
- C++
helpviewer_keywords:
- atomic OpenMP directive
ms.assetid: 275e0338-cf2f-4525-97b5-696250000df7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7e9e9ecad2f6ea53e2f922799340eee47dd4a7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037484"
---
# <a name="atomic"></a>Atomic — 原子
指定将以原子方式更新的内存位置。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma omp atomic  
   expression  
```  
  
#### <a name="parameters"></a>参数  
*表达式*<br/>
你想要防止多个写入包含其内存位置的左值的语句。 有关合法表达式形式的详细信息，请参阅的 OpenMP 规范。  
  
## <a name="remarks"></a>备注  
 `atomic`指令支持任何 OpenMP 子句。  
  
 有关详细信息，请参阅[2.6.4 atomic 构造](../../../parallel/openmp/2-6-4-atomic-construct.md)。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>请参阅  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)