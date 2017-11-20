---
title: "函数体 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a30ad1b016e0ab4814e0ac6f6f4627cdf265f59b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="function-body"></a>函数体
“函数体”是包含指定函数行为的语句的复合语句。  
  
## <a name="syntax"></a>语法  
 function-definition：  
 declaration-specifiers optattribute-seq optdeclarator declaration-list optcompound-statement  
  
 /\* *attribute-seq* 为 Microsoft 专用 */  
  
 compound-statement：/\* 函数体 \*/  
 {  declaration-list optstatement-list opt}  
  
 在函数体中声明的变量“局部变量”具有 auto 存储类，除非另行指定。 调用函数时，将为局部变量创建存储并执行本地初始化。 执行控制权将传递给 compound-statement 中的第一个语句并继续传递，直到执行了 `return` 语句或到达函数体的末尾。 控制权随后返回到调用功能的点。  
  
 如果该函数返回了值，则必须执行包含表达式的 `return` 语句。 如果没有执行 `return` 语句或 `return` 语句不包含表达式，则函数的返回值是不确定的。  
  
## <a name="see-also"></a>另请参阅  
 [C 函数定义](../c-language/c-function-definitions.md)