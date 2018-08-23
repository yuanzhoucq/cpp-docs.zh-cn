---
title: 编译器错误 C2438 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2438
dev_langs:
- C++
helpviewer_keywords:
- C2438
ms.assetid: 3a0ab3ba-d0e4-4d8f-971d-e503397cc827
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf42740c137953007cab2c5301bff122b553e5f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225533"
---
# <a name="compiler-error-c2438"></a>编译器错误 C2438
identifier： 无法初始化静态类数据通过构造函数  
  
 构造函数用于初始化类的静态成员。 必须在类声明的外部定义中初始化静态成员。  
  
 下面的示例生成 C2438:  
  
```  
// C2438.cpp  
struct X {  
   X(int i) : j(i) {}   // C2438  
   static int j;  
};  
  
int X::j;  
  
int main() {  
   X::j = 1;  
}  
```