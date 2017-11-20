---
title: "默认值 (OpenMP) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: default
dev_langs: C++
helpviewer_keywords:
- default OpenMP clause
- defaults, OpenMP clause
ms.assetid: 96055106-a8f0-40b3-8319-e412b6e07bf8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: caafb7818c32dad7b21ac7a05d10f77753c1da73
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="default-openmp"></a>default (OpenMP)
并行区域中指定的未区分范围的变量的行为。  
  
## <a name="syntax"></a>语法  
  
```  
default(shared | none)  
```  
  
## <a name="remarks"></a>备注  
 `shared`它实际上是如果`default`子句未指定，意味着将被视为并行区域内的任何变量，如同它指定与[共享](../../../parallel/openmp/reference/shared-openmp.md)子句。 `none`意味着在作用域不是使用并行区域中使用的任何变量[私有](../../../parallel/openmp/reference/private-openmp.md)，[共享](../../../parallel/openmp/reference/shared-openmp.md)，[缩减](../../../parallel/openmp/reference/reduction.md)， [firstprivate](../../../parallel/openmp/reference/firstprivate.md)，或[lastprivate](../../../parallel/openmp/reference/lastprivate.md)子句将导致编译器错误。  
  
 `default`适用于以下指令：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [部分](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关详细信息，请参阅[2.7.2.5 默认](../../../parallel/openmp/2-7-2-5-default.md)。  
  
## <a name="example"></a>示例  
 请参阅[私有](../../../parallel/openmp/reference/private-openmp.md)有关的使用示例`default`。  
  
## <a name="see-also"></a>另请参阅  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)