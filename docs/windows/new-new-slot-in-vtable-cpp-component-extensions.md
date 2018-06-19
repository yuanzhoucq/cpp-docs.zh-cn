---
title: 新 (新 vtable 中的槽） （c + + 组件扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7189909f3cff84d2bb1a767e4ddeda817bcd6128
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879778"
---
# <a name="new-new-slot-in-vtable--c-component-extensions"></a>new（vtable 中的新槽）（C++ 组件扩展）
`new`关键字指示虚拟成员将获取 vtable 中的新槽。  
  
## <a name="all-runtimes"></a>所有运行时  
 （此语言功能没有适用于所有运行时的备注。）  
  
## <a name="windows-runtime"></a>Windows 运行时  
 不支持在 Windows 运行时中。  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 **备注**  
  
 在 **/clr**编译，`new`指示虚拟成员将获取 vtable 中的新槽; 该函数不重写基类方法。  
  
 `new` 导致 newslot 修饰符添加到的 IL 的函数。  Newslot 有关的详细信息，请参阅：  
  
-   [MethodInfo.GetBaseDefinition 方法](https://msdn.microsoft.com/en-us/library/system.reflection.methodinfo.getbasedefinition.aspx)  
  
-   [MethodAttributes 枚举](https://msdn.microsoft.com/en-us/library/system.reflection.methodattributes.aspx)  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的示例演示的效果`new`。  
  
```  
// newslot.cpp  
// compile with: /clr  
ref class C {  
public:  
   virtual void f() {  
      System::Console::WriteLine("C::f() called");  
   }  
  
   virtual void g() {  
      System::Console::WriteLine("C::g() called");  
   }  
};  
  
ref class D : public C {  
public:  
   virtual void f() new {  
      System::Console::WriteLine("D::f() called");  
   }  
  
   virtual void g() override {  
      System::Console::WriteLine("D::g() called");  
   }  
};  
  
ref class E : public D {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("E::f() called");  
   }  
};  
  
int main() {  
   D^ d = gcnew D;  
   C^ c = gcnew D;  
  
   c->f();   // calls C::f  
   d->f();   // calls D::f  
  
   c->g();   // calls D::g  
   d->g();   // calls D::g  
  
   D ^ e = gcnew E;  
   e->f();   // calls E::f  
}  
```  
  
 **输出**  
  
```Output  
C::f() called  
  
D::f() called  
  
D::g() called  
  
D::g() called  
  
E::f() called  
```  
  
## <a name="see-also"></a>请参阅  
 [运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)   
 [重写说明符](../windows/override-specifiers-cpp-component-extensions.md)