---
title: OMP_NUM_THREADS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NUM_THREADS
dev_langs:
- C++
helpviewer_keywords:
- OMP_NUM_THREADS OpenMP environment variable
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39f45b9c81d5339b2b6afe4c77fdc9bac6b5d731
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091161"
---
# <a name="ompnumthreads"></a>OMP_NUM_THREADS
并行区域中设置的最大线程数，除非被重写[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或[num_threads](../../../parallel/openmp/reference/num-threads.md)。  
  
## <a name="syntax"></a>语法  
  
```  
set OMP_NUM_THREADS[=num]  
```  
  
### <a name="parameters"></a>参数
  
*num*<br/>
最大并行区域，最多为 64 在 Visual c + + 实现中所需的线程数。  
  
## <a name="remarks"></a>备注  
 **OMP_NUM_THREADS**环境变量可以通过重写[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)函数或通过[num_threads](../../../parallel/openmp/reference/num-threads.md)。  
  
 默认值`num`Visual c + + 中实现的 OpenMP 标准是虚拟处理器，包括超线程 Cpu 的数量。  
  
 有关详细信息，请参阅[4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md)。  
  
## <a name="example"></a>示例  
 下面的命令集**OMP_NUM_THREADS**为 16 的环境变量：  
  
```  
set OMP_NUM_THREADS=16  
```  
  
 下面的命令显示的当前设置**OMP_NUM_THREADS**环境变量：  
  
```  
set OMP_NUM_THREADS  
```  
  
## <a name="see-also"></a>请参阅  
 [环境变量](../../../parallel/openmp/reference/openmp-environment-variables.md)