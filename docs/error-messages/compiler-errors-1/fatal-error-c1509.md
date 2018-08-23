---
title: 错误 C1509 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1509
dev_langs:
- C++
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fec83f6b6138eacc613e560b9da4557079d6677d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198789"
---
# <a name="fatal-error-c1509"></a>错误 C1509
编译器限制： 函数 function 中的有太多异常处理程序状态。 简化函数  
  
 代码超过异常处理程序状态 （32768 个状态） 的内部限制。  
  
 最常见原因是该函数包含用户定义的类变量和算术运算符的复杂表达式。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  通过将公共子表达式分配给临时变量来简化表达式。  
  
2.  将函数拆分为较小的函数。