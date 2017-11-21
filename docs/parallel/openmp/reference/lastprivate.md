---
title: "lastprivate |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: lastprivate
dev_langs: C++
helpviewer_keywords: lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9429a54a21d58be7f2dd1667478ae653da5a8c35
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
 `lastprivate`适用于以下指令：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [部分](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关详细信息，请参阅[2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md)。  
  
## <a name="example"></a>示例  
 请参阅[计划](../../../parallel/openmp/reference/schedule.md)有关的使用示例`lastprivate`子句。  
  
## <a name="see-also"></a>另请参阅  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)