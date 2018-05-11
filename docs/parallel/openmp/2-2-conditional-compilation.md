---
title: 2.2 条件编译 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3d8c7073548c015d9982b721387176a0ca658c2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="22-conditional-compilation"></a>2.2 条件编译
_**OPENMP**宏名称指由 OpenMP 符合实现十进制常量*yyyymm*，这将是年份和月份的已批准的规范。 此宏不能使用者的 **#define**或 **#undef**预处理指令。  
  
```  
#ifdef _OPENMP  
iam = omp_get_thread_num() + index;  
#endif  
```  
  
 如果供应商为 OpenMP 定义扩展，它们可以指定其他预定义的宏。