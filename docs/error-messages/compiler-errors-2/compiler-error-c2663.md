---
title: 编译器错误 C2663 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2663
dev_langs:
- C++
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f39f516b32aaf1159d47726d01623e253ee8b383
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235854"
---
# <a name="compiler-error-c2663"></a>编译器错误 C2663
function： 数字重载具有 this 指针的任何合法转换  
  
 编译器无法转换`this`到任何成员函数的重载版本。  
  
 可以通过调用非-导致此错误`const`成员函数上的`const`对象。  可能的解决方法：  
  
1.  删除`const`从对象声明。  
  
2.  添加`const`成员函数重载之一。  
  
 下面的示例生成 C2663:  
  
```  
// C2663.cpp  
struct C {  
   void f() volatile {}  
   void f() {}  
};  
  
struct D {  
   void f() volatile;  
   void f() const {}  
};  
  
const C *pcc;  
const D *pcd;  
  
int main() {  
   pcc->f();    // C2663  
   pcd->f();    // OK  
}  
```