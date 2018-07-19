---
title: 表达式计算器错误 CXX0019 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52e1679374e105ab06ce245ba68cfe92706689e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302485"
---
# <a name="expression-evaluator-error-cxx0019"></a>表达式计算器错误 CXX0019
错误的类型转换  
  
 C 表达式计算器无法执行强制转换所编写的类型。  
  
 此错误是与 CAN0019 相同。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  指定的类型是未知的。  
  
2.  没有太多级别的指针类型。 例如，类型转换  
  
    ```  
    (char **)h_message  
    ```  
  
     不能对 C 表达式计算器进行评估。