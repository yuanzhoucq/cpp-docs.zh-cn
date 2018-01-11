---
title: "原子 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: atomic
dev_langs: C++
helpviewer_keywords: atomic OpenMP directive
ms.assetid: 275e0338-cf2f-4525-97b5-696250000df7
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e3d190504a0e4caab864c637d7053836b01f88f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="atomic"></a>Atomic — 原子
指定将以原子方式更新的内存位置。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma omp atomic  
   expression  
```  
  
#### <a name="parameters"></a>参数  
 `expression`  
 你想要防止多次写入包含其内存位置的左值的语句。 有关合法表达式窗体的详细信息，请参阅 OpenMP 规范。  
  
## <a name="remarks"></a>备注  
 `atomic`指令支持没有 OpenMP 子句。  
  
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