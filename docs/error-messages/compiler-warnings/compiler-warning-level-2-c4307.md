---
title: "编译器警告 （等级 2） C4307 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4307
dev_langs: C++
helpviewer_keywords: C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2647133788bdaafb2f69f2edc5b8e13cfa07cc5b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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