---
title: 编译器警告 （等级 2） C4307 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4307
dev_langs:
- C++
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52914fc5825bda5647308c006b853538f3d6225e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292027"
---
# <a name="compiler-warning-level-2-c4307"></a>编译器警告（等级 2）C4307
operator： 整型常数溢出  
  
 导致溢出为其分配的空间的整数常量表达式中使用的运算符。 你可能需要使用更大的类型常量。 A**带符号整型**包含比值小`unsigned int`因为**带符号整型**使用一位来表示符号。  
  
 下面的示例生成 C4307:  
  
```  
// C4307.cpp  
// compile with: /W2  
int i = 2000000000 + 2000000000;   // C4307  
int j = (unsigned)2000000000 + 2000000000;   // OK  
  
int main()  
{  
}  
```