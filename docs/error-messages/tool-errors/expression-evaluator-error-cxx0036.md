---
title: 表达式计算器错误 CXX0036 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0036
dev_langs:
- C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18e1bf3cda85d7b3d64d51279688a52cec5c0336
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301679"
---
# <a name="expression-evaluator-error-cxx0036"></a>表达式计算器错误 CXX0036
错误上下文 {...} specification  
  
 可以通过使用上下文运算符中的多个错误的任何生成此消息 (**{}**)。  
  
-   上下文运算符的语法 (**{}**) 未正确给定。  
  
     上下文运算符的语法是：  
  
     {*函数*，*模块*，*dll*}*表达式*  
  
     这将指定的上下文*表达式*。 上下文运算符类型强制转换为具有相同的优先级和使用情况。  
  
     可以省略尾随逗号。 如果任一*函数*，*模块*，或*dll*包含文本逗号，必须将整个名称括在括号中。  
  
-   函数名称拼写错误，或指定的模块或动态链接库中不存在。  
  
     C 是区分大小写的语言，因为*函数*必须特别中的正确大小写，因为它在源中定义。  
  
-   找不到模块或 DLL。  
  
     请检查指定的模块或 DLL 的完整路径名称。  
  
 此错误是与 CAN0036 相同。