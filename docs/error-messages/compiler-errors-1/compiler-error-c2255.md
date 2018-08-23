---
title: 编译器错误 C2255 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2255
dev_langs:
- C++
helpviewer_keywords:
- C2255
ms.assetid: 67dc4cb0-de6b-4405-bd64-d47736367a93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 314d53017cf809e0ca38838cdfb3b3bb4b22437c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169600"
---
# <a name="compiler-error-c2255"></a>编译器错误 C2255
“元素”: 不允许位于类定义之外  
  
 例如，非成员函数声明 `friend`。  
  
 下面的示例生成 C2255:  
  
```  
// C2255.cpp  
// compile with: /c  
class A {  
private:  
   void func1();  
   friend void func2();  
};  
  
friend void func1() {}   // C2255  
void func2(){}  
```