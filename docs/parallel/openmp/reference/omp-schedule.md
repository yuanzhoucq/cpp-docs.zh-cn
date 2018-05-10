---
title: OMP_SCHEDULE |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_SCHEDULE
dev_langs:
- C++
helpviewer_keywords:
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5052aaadc673e38a844ea5b0d1e11ff3a96f3fbe
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="ompschedule"></a>OMP_SCHEDULE
修改的行为[计划](../../../parallel/openmp/reference/schedule.md)子句时`schedule(runtime)`中指定`for`或`parallel for`指令。  
  
## <a name="syntax"></a>语法  
  
```  
set OMP_SCHEDULE[=type[,size]]  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `size`（可选）  
 指定的迭代的大小。 `size` 必须是正整数。 默认值为 1，除非`type`是静态的。 不是有效的在`type`是`runtime`。  
  
 `type`  
 计划类型：  
  
-   `dynamic`  
  
-   `guided`  
  
-   `runtime`  
  
-   `static`  
  
## <a name="remarks"></a>备注  
 OpenMP 标准的 Visual c + + 实现中的默认值是`OMP_SCHEDULE=static,0`。  
  
 有关详细信息，请参阅[4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md)。  
  
## <a name="example"></a>示例  
 下面的命令集**OMP_SCHEDULE**环境变量：  
  
```  
set OMP_SCHEDULE="guided,2"  
```  
  
 下面的命令显示的当前设置**OMP_SCHEDULE**环境变量：  
  
```  
set OMP_SCHEDULE  
```  
  
## <a name="see-also"></a>请参阅  
 [环境变量](../../../parallel/openmp/reference/openmp-environment-variables.md)