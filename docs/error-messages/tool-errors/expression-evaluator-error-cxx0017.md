---
title: "表达式计算器错误 CXX0017 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0017
dev_langs:
- C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e769e9886168c9f19ad110c48d848a9b84ab8aac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0017"></a>表达式计算器错误 CXX0017
未找到符号  
  
 找不到表达式中指定的符号。  
  
 此错误的一个可能的原因是中的符号名称的大小写不匹配。 因为 C 和 c + + 是区分大小写的语言，必须在其中它定义在源中的正确大小写中写给定的符号名称。  
  
 尝试转换以在调试期间查看变量的变量时，可能出现此错误。 `typedef`声明类型的新名称，但不定义新类型。 类型转换在调试器中尝试需要已定义的类型的名称。  
  
 此错误是与 CAN0017 相同。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  请确保该符号已声明中使用其中的程序的点处。  
  
2.  使用实际类型名称将变量强制转换在调试器中，而不是`typedef`-定义名称。