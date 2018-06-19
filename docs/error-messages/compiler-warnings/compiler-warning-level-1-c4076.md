---
title: 编译器警告 （等级 1） C4076 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4076
dev_langs:
- C++
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1cfa28469e099dbf2b6bd43213073c304d0b2894
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275468"
---
# <a name="compiler-warning-level-1-c4076"></a>编译器警告（等级 1）C4076
“typemod”: 不能和“typename”类型一起使用  
  
 类型修饰符（无论是 **有符号** 还是 `unsigned`）不能用于非整数类型。 ***typemod*** 将被忽略。  
  
## <a name="example"></a>示例  
 以下示例生成 C4076:  
  
```  
// C4076.cpp  
// compile with: /W1 /LD  
unsigned double x;   // C4076  
```