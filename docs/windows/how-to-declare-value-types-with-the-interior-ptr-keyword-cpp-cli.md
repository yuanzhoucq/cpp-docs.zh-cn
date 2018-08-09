---
title: 如何： 用 interior_ptr 关键字声明值类型 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9abba9937bfe425fa85cbce5b0795a3f9c784d22
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017222"
---
# <a name="how-to-declare-value-types-with-the-interiorptr-keyword-ccli"></a>如何：用 interior_ptr 关键字声明值类型 (C++/CLI)
**Interior_ptr**可用于值类型。  
  
> [!IMPORTANT]
>  `/clr` 编译器选项支持此语言功能，但是 `/ZW` 编译器选项不支持此语言功能。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 以下 C + + /cli CLI 示例演示如何使用**interior_ptr**与值类型。  
  
### <a name="code"></a>代码  
  
```cpp  
// interior_ptr_value_types.cpp  
// compile with: /clr  
value struct V {  
   V(int i) : data(i){}  
   int data;  
};  
  
int main() {  
   V v(1);  
   System::Console::WriteLine(v.data);  
  
   // pointing to a value type  
   interior_ptr<V> pv = &v;  
   pv->data = 2;  
  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
  
   // pointing into a value type  
   interior_ptr<int> pi = &v.data;  
   *pi = 3;  
   System::Console::WriteLine(*pi);  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
}  
```  

```Output  
1  
2  
2  
3  
3  
3  
```  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 在值类型，**这**指针的计算结果为 interior_ptr。  
  
 中的非静态成员函数将值类型的正文`V`，**这**类型的表达式`interior_ptr<V>`其值是为其调用该函数的对象的地址。  
  
### <a name="code"></a>代码  
  
```cpp  
// interior_ptr_value_types_this.cpp  
// compile with: /clr /LD  
value struct V {  
   int data;  
   void f() {  
      interior_ptr<V> pv1 = this;  
      // V* pv2 = this;   error  
   }  
};  
```  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例演示了如何将 address-of 运算符与静态成员一起使用。  
  
 静态 Visual C++ 类型成员的地址产生本机指针。  静态值类型成员的地址是托管指针，因为值类型成员在运行时堆上分配，并且可由垃圾回收器移动。  
  
### <a name="code"></a>代码  
  
```cpp  
// interior_ptr_value_static.cpp  
// compile with: /clr  
using namespace System;  
value struct V { int i; };  
  
ref struct G {  
   static V v = {22};   
   static int i = 23;   
   static String^ pS = "hello";   
};  
  
int main() {  
   interior_ptr<int> p1 = &G::v.i;  
   Console::WriteLine(*p1);  
  
   interior_ptr<int> p2 = &G::i;  
   Console::WriteLine(*p2);  
  
   interior_ptr<String^> p3 = &G::pS;  
   Console::WriteLine(*p3);  
}  
```  
  
```Output 
22  
23  
hello  
```  
  
## <a name="see-also"></a>请参阅  
 [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)