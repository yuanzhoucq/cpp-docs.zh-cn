---
title: 链接器工具错误 LNK2020 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2020
dev_langs:
- C++
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33dd1b381d36a90f2e9b144e690e364ac512c081
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301952"
---
# <a name="linker-tools-error-lnk2020"></a>链接器工具错误 LNK2020
无法解析的标记 token  
  
 类似于未定义的外部错误，只不过引用是通过元数据。 在元数据，必须定义所有函数和数据。  
  
 若要解决：  
  
-   定义缺少的函数或数据，或  
  
-   包括的对象文件或在其中缺少的函数或数据已定义的库。  
  
## <a name="example"></a>示例  
 下面的示例生成 LNK2020。  
  
```  
// LNK2020.cpp  
// compile with: /clr /LD  
ref struct A {  
   A(int x);   // LNK2020  
   static int f();   // LNK2020  
};  
  
// OK  
ref struct B {  
   B(int x) {}  
   static int f() { return 0; }  
};  
```  
  
## <a name="example"></a>示例  
 如果你创建的变量的一种托管的模板类型，但不是还实例化类型，也会发生 LNK2020。  
  
 下面的示例生成 LNK2020。  
  
```  
// LNK2020_b.cpp  
// compile with: /clr   
  
template <typename T>  
ref struct Base {  
   virtual void f1() {};  
};  
  
template <typename T>  
ref struct Base2 {  
   virtual void f1() {};  
};  
  
int main() {  
   Base<int>^ p;   // LNK2020  
   Base2<int>^ p2 = gcnew Base2<int>();   // OK  
};  
```