---
title: lastprivate |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- lastprivate
dev_langs:
- C++
helpviewer_keywords:
- lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5aaf80e3061877c42154ab9ee5ccd30f47f17135
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696222"
---
# <a name="lastprivate"></a>lastprivate
指定的变量的封闭上下文的版本被设置为私有版本的任何线程执行的最后一个迭代 （for 循环构造） 或最后一节 （#pragma 节）。  
  
## <a name="syntax"></a>语法  
  
```  
lastprivate(var)  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `var`  
 设置为等于私有版本的任何线程执行的最后一个迭代 （for 循环构造） 或最后一节 （#pragma 节） 的变量。  
  
## <a name="remarks"></a>备注  
 `lastprivate` 适用于以下指令：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [部分](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关详细信息，请参阅[2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md)。  
  
## <a name="example"></a>示例  
 请参阅[计划](../../../parallel/openmp/reference/schedule.md)有关的使用示例`lastprivate`子句。  
  
## <a name="see-also"></a>请参阅  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)