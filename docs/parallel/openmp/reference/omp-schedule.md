---
title: OMP_SCHEDULE |Microsoft Docs
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
ms.openlocfilehash: fd5bf96706b94ffbba8cb1b9aeeee8701b266e5d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115031"
---
# <a name="ompschedule"></a>OMP_SCHEDULE
修改的行为[计划](../../../parallel/openmp/reference/schedule.md)子句时`schedule(runtime)`中指定`for`或`parallel for`指令。  
  
## <a name="syntax"></a>语法  
  
```  
set OMP_SCHEDULE[=type[,size]]  
```  
  
## <a name="arguments"></a>自变量

*size*<br/>
（可选）指定的迭代的大小。 `size` 必须为正整数。 默认值为 1，除非当`type`是静态的。 时未有效`type`是`runtime`。  
  
*type*<br/>
计划的类型：  
  
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