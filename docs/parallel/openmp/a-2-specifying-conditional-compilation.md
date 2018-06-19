---
title: 指定条件编译的 A.2 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d54245a2df2f38bed2674a3bb3923f8212d35459
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690590"
---
# <a name="a2---specifying-conditional-compilation"></a>A.2   指定条件编译
下面的示例演示如何使用条件编译使用 OpenMP 宏`_OPENMP`([2.2 节](../../parallel/openmp/2-2-conditional-compilation.md)第 8 页上)。 与 OpenMP 编译`_OPENMP`宏成为已定义。  
  
```  
# ifdef _OPENMP   
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```  
  
 定义预处理器运算符允许多个宏来在一条指令中进行测试。  
  
```  
# if defined(_OPENMP) && defined(VERBOSE)  
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```