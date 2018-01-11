---
title: "数学错误 M6201 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6201
dev_langs: C++
helpviewer_keywords: M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17de7fab7b41a5a8acc2fed2f3c8185f66aadd9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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