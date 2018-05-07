---
title: 数学错误 M6201 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6201
dev_langs:
- C++
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6a15e841cfc8daf1abdafc9997698807e7356af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="math-error-m6201"></a>数学错误 M6201
function: _DOMAIN 错误  
  
 给定的函数的自变量为域外部的合法的输入值，该函数。  
  
## <a name="example"></a>示例  
  
```  
result = sqrt(-1.0)   // C statement  
result = SQRT(-1.0)   !  FORTRAN statement  
```  
  
 此错误调用`_matherr`函数名称、 其参数与错误类型的函数。 您可以重新编写`_matherr`函数以自定义的某些运行时浮点数学错误处理。