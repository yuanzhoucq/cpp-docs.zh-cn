---
title: 如何： 用 interior_ptr 关键字声明值类型 (C + + /cli CLI) |Microsoft 文档
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
ms.openlocfilehash: 6015d5a61589b8ed2d38b6491392fd42e4f38ef1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879472"
---
# <a name="how-to-declare-value-types-with-the-interiorptr-keyword-ccli"></a>如何：用 interior_ptr 关键字声明值类型 (C++/CLI)
`interior_ptr` 可以与值类型一起使用。  
  
> [!IMPORTANT]
>  通过支持此语言功能 **/clr**编译器选项，但不是 **/ZW**编译器选项。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 以下 C + + /cli CLI 示例演示如何使用`interior_ptr`使用值类型。  
  
### <a name="code"></a>代码  
  
```  
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
  
### <a name="output"></a>输出  
  
```  
1  
2  
2  
3  
3  
3  
```  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 在值类型中，`this` 指针的计算结果为 interior_ptr。  
  
 在值类型 `V` 的非静态成员函数体中，`this` 是类型 `interior_ptr<V>` 的表达式，后者的值是函数调用的对象地址。  
  
### <a name="code"></a>代码  
  
```  
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
  
```  
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
  
### <a name="output"></a>输出  
  
```  
22  
23  
hello  
```  
  
## <a name="see-also"></a>请参阅  
 [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)