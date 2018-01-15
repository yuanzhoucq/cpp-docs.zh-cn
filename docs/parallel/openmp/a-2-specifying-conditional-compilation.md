---
title: "指定条件编译的 A.2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 93557eaae2c8661697f7bda383b50f2e1ba9e2cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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