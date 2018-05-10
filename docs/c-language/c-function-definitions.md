---
title: C 函数定义 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function declarators
- function definitions
- declaring functions, about function declarations
- declaring functions, declarators
- functions [C], parameters
- declarators, functions
- function parameters, function definitions
- function body
- declaring functions, variables
ms.assetid: ebab23c8-6eb8-46f3-b21d-570cd8457a80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69c9846b2ee192071b951d5b9b196d6e4b1968aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="c-function-definitions"></a>C 函数定义
函数定义指定函数的名称、函数期望接收的参数的类型和数量以及函数的返回类型。 函数定义还包括带有局部变量的声明的函数体和确定函数行为的语句。  
  
## <a name="syntax"></a>语法  
 translation-unit：  
 external-declaration  
  
 translation-unit external-declaration  
  
 external-declaration: /\* 只允许在外部（文件）范围内 \*/  
 function-definition  
  
 `declaration`  
  
 function-definition: /\* 此处的声明符是函数声明符 \*/  
 declaration-specifiers optattribute-seq optdeclarator declaration-list optcompound-statement  
  
 /\* *attribute-seq* 为 Microsoft 专用 */  
  
 原型参数为：  
  
 *declaration-specifiers*：  
 storage-class-specifier declaration-specifiers opt  
  
 type-specifier declaration-specifiers opt  
  
 type-qualifier declaration-specifiers opt  
  
 declaration-list：  
 declaration  
  
 declaration-list declaration  
  
 `declarator`：  
 pointer optdirect-declarator  
  
 direct-declarator: /\* 函数声明符 \*/  
 *direct-declarator*  **(**  *parameter-type-list*  **)** /* 新样式声明符 \*/  
  
 direct-declarator  (  identifier-list opt) /* 旧样式声明符 \*/  
  
 定义中的参数列表使用以下语法：  
  
 parameter-type-list： /\* 参数列表 \*/  
 *parameter-list*  
  
 *parameter-list* **, ...**  
  
 *parameter-list*:  
 *parameter-declaration*  
  
 parameter-list ,  parameter-declaration  
  
 *parameter-declaration*:  
 declaration-specifiers declarator  
  
 declaration-specifiers abstract declarator opt  
  
 旧式函数定义中的参数列表使用以下语法：  
  
 identifier-list：/\* 在旧式函数定义和声明中使用 \*/  
 *identifier*  
  
 identifier-list ,  identifier  
  
 函数体的语法为：  
  
 compound-statement：/\* 函数体 \*/  
 {  `declaration`-list optstatement-list opt}  
  
 仅有的可修改函数声明的存储类说明符是 `extern` 和 static。 `extern` 说明符表示可以从其他文件引用函数；即，将函数名导出到链接器。 static 说明符表示不能从其他文件引用函数；即，链接器不会导出名称。 如果存储类未在函数定义中出现，则假定 `extern`。 在任何情况下，从定义点到文件的末尾函数始终可见。  
  
 可选的 declaration-specifiers 和必需的 `declarator` 共同指定函数的返回类型和名称。 `declarator` 是用来命名函数的标识符与函数名后面的括号的组合。 可选的 attribute-seq 非终止符是在[函数特性](../c-language/function-attributes.md)中定义的 Microsoft 专用功能。  
  
 direct-declarator（在 `declarator` 语法中）指定要定义的函数的名称及其参数的标识符。 如果 direct-declarator 包括 parameter-type-list，则该列表将指定所有参数的类型。 此类声明符还用作以后对函数进行调用时的函数原型。  
  
 函数定义中的 declaration-list 内的 `declaration` 不能包含除 register 之外的 storage-class-specifier。 仅当为 `int` 类型的值指定 register 存储类时，才能省略 declaration-specifiers 语法中的 type-specifier。  
  
 compound-statement 是包含局部变量声明、对在外部声明的项的引用和语句的函数体。  
  
 [函数特性](../c-language/function-attributes.md)、[存储类](../c-language/storage-class.md)、[返回类型](../c-language/return-type.md)、[参数](../c-language/parameters.md)和[函数体](../c-language/function-body.md)节详细地描述了函数定义的组成部分。  
  
## <a name="see-also"></a>请参阅  
 [函数](../c-language/functions-c.md)