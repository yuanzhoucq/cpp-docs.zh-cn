---
title: 编译器错误 C3890 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3890
dev_langs:
- C++
helpviewer_keywords:
- C3890
ms.assetid: 2f22c2fd-c14e-45e1-b936-b739ffc0b135
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc1bfbba9cfb8991491bcbb42d2e13c586c7fc26
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3890"></a>编译器错误 C3890
var： 不能采用 literal 数据成员的地址  
  
 垃圾回收堆上存在的 literal 数据成员。  可以移动已垃圾回收堆上的对象，因此采用的地址不是很有用。  
  
 下面的示例生成 C3890:  
  
```  
// C3890.cpp  
// compile with: /clr  
ref struct Y1 {  
   literal int staticConst = 9;  
};  
  
int main() {  
   int p = &Y1::staticConst;   // C3890  
   int p2 = Y1::staticConst;   // OK  
}  
```