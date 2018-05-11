---
title: 表达式计算器错误 CXX0039 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0039
dev_langs:
- C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8681d73d2889433516b205a47c500193bbeabdb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0039"></a>表达式计算器错误 CXX0039
符号是不明确  
  
 C 表达式计算器无法确定要在表达式中使用的符号的哪个实例。 该符号在继承树中多次出现。  
  
 你必须使用范围解析运算符 (`::`) 若要显式指定要在表达式中使用的实例。  
  
 此错误是与 CAN0039 相同。