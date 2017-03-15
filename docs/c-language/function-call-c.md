---
title: "函数调用 (C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函数调用"
  - "函数调用, C 函数"
  - "函数 [C], 调用"
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 函数调用 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“函数调用”是包含被调用函数的名称或函数指针的值以及（可选）传递给函数的参数的表达式。  
  
## 语法  
 *postfix\-expression*:  
 *postfix\-expression*  **\(**  *argument\-expression\-list*  opt **\)**  
  
 *argument\-expression\-list*:  
 *assignment\-expression*  
  
 *argument\-expression\-list*  **,**  *assignment\-expression*  
  
 *postfix\-expression* 的计算结果必须为函数地址（例如，函数标识符或函数指针的值），并且 *argument\-expression\-list* 是其值（“参数”）传递到函数的表达式的列表（用逗号分隔）。  *argument\-expression\-list* 参数可以为空。  
  
 function\-call 表达式具有函数的返回值的值和类型。  函数不能返回数组类型的对象。  如果函数的返回类型是 `void`（即该函数已被声明为从不返回值），则 function\-call 表达式也具有 `void` 类型。（有关详细信息，请参阅[函数调用](../c-language/function-calls.md)。）  
  
## 请参阅  
 [函数调用运算符：\(\)](../cpp/function-call-operator-parens.md)