---
title: "OMP_SCHEDULE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_SCHEDULE
dev_langs: C++
helpviewer_keywords: OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8aa1406b490128657da19f7c48c958d382850d96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
 指定的迭代的大小。 `size`必须是正整数。 默认值为 1，除非`type`是静态的。 不是有效的在`type`是`runtime`。  
  
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