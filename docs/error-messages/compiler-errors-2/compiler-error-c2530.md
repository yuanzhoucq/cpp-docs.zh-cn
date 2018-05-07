---
title: 编译器错误 C2530 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2530
dev_langs:
- C++
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b226ef5ca0e839c745e13d4118264a69ca408db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2530"></a>编译器错误 C2530
identifier： 必须初始化引用  
  
 你必须初始化引用声明它时，除非它已被声明：  
  
-   使用关键字[extern](../../cpp/using-extern-to-specify-linkage.md)。  
  
-   作为类、 结构或联合的成员 （和构造函数中初始化）。  
  
-   作为函数声明或定义中的参数。  
  
-   作为函数的返回类型。  
  
 下面的示例生成 C2530:  
  
```  
// C2530.cpp  
int main() {  
   int i = 0;  
   int &j;   // C2530  
   int &k = i;   // OK  
}  
```