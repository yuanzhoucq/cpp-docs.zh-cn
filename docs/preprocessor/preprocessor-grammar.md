---
title: "预处理器语法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02b3597b035e3ea4bfa1670aa405109f4c01a077
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="preprocessor-grammar"></a>预处理器语法
**#define**  *identifier* *token-string*opt  
  
 *#* **define**  *identifier*[**(** *identifier*opt**,** *...* **,** *identifier*opt **)**] *token-string*opt  
  
 **defined(**  *identifier* **)**  
  
 **defined**  *identifier*  
  
 `#include` **"***path-spec***"**  
  
 `#include` **\<***path-spec***>**  
  
 **#line**  *digit-sequence*  **"** *filename* **"**opt  
  
 *#* **undef**  *identifier*  
  
 **#error**  *token-string*  
  
 **#pragma**  *token-string*  
  
 *条件*:  
 *如果一部分 elif 部件*选择*else 部分*选择*endif 行*  
  
 *如果一部分*:  
 *if-linetext*  
  
 *如果行*:  
 **#if**  *constant-expression*  
  
 **#ifdef**  *identifier*  
  
 **#ifndef**  *identifier*  
  
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