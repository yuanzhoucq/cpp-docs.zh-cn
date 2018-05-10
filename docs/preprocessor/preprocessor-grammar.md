---
title: 预处理器语法 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d14a3e00e18a2d3ac69dd472ac4056a379ada224
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="preprocessor-grammar"></a>预处理器语法
**#define***标识符**令牌字符串*选择    
  
 *#* **定义***标识符*[**(** *标识符*选择**，** *...* **，** *标识符*选择 **)**]*令牌字符串*选择    
  
 **defined(**  *identifier* **)**  
  
 **定义***标识符*   
  
 `#include` **"***路径规范***"**  
  
 `#include` **\<***路径规范***>**  
  
 **#line**  *digit-sequence*  **"** *filename* **"** opt  
  
 *#* **undef***标识符*   
  
 **#error***令牌字符串*   
  
 **#pragma***令牌字符串*   
  
 *条件*:  
 *如果一部分 elif 部件*选择*else 部分*选择*endif 行*  
  
 *如果一部分*:  
 *if-linetext*  
  
 *如果行*:  
 **#if**  *constant-expression*  
  
 **#ifdef***标识符*   
  
 **#ifndef***标识符*   
  
 *elif 部件*:  
 *elif 行文本*  
  
 *elif 部件 elif 行文本*  
  
 *elif 行*:  
 **#elif**  *constant-expression*  
  
 *else 部分*:  
 *else-linetext*  
  
 *其他行*:  
 `#else`  
  
 *endif 行*:  
 `#endif`  
  
 *数字序列*:  
 *digit*  
  
 *digit-sequence digit*  
  
 *数字*： 之一  
 **0 1 2 3 4 5 6 7 8 9**  
  
 *令牌字符串*:  
 标记字符串  
  
 *令牌*:  
 keyword  
  
 *identifier*  
  
 *constant*  
  
 *operator*  
  
 `punctuator`  
  
 *filename* :  
 合法操作系统文件名  
  
 *路径规范*:  
 合法文件路径  
  
 *文本*:  
 文本的任何序列  
  
> [!NOTE]
>  在中扩展以下非终止符[词法约定](../cpp/lexical-conventions.md)部分*c + + 语言参考*: `constant`， `constant` -*表达式*，*标识符*，*关键字*， `operator`，和`punctuator`。  
  
## <a name="see-also"></a>请参阅  
 [语法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)