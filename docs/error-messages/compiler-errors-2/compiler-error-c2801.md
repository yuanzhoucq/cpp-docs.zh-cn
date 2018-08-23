---
title: 编译器错误 C2801 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2801
dev_langs:
- C++
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f68b3f575fcb8b909f58ac2ffbcaca26580279da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33237083"
---
# <a name="compiler-error-c2801"></a>编译器错误 C2801
operator operator 必须为非静态成员  
  
 以下运算符可以进行重载仅作为非静态成员：  
  
-   分配 `=`  
  
-   类成员访问 `->`  
  
-   下标 `[]`  
  
-   函数调用 `()`  
  
 C2801 的可能原因：  
  
-   重载的运算符不是类、 结构或联合成员。  
  
-   重载的运算符被声明`static`。  
  
-   下面的示例生成 C2801:  
  
```  
// C2801.cpp  
// compile with: /c  
operator[]();   // C2801 not a member  
class A {  
   static operator->();   // C2801 static  
   operator()();   // OK  
};  
```