---
title: "显式重写 （c + + 组件扩展） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 346dd73952934d514b2741c41d5a27816b7152ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="explicit-overrides--c-component-extensions"></a>显式重写（C++ 组件扩展）
本主题讨论如何显式重写基类或接口的成员。 命名的 （显式） 重写应仅用于重写的方法与具有不同的名称派生方法。  
  
## <a name="all-runtimes"></a>所有运行时  
 **语法**  
  
```  
  
      overriding-function-declarator = type::function [,type::function] { overriding-function-definition }  
overriding-function-declarator = function { overriding-function-definition }  
```  
  
 **参数**  
  
 *重写函数声明符*  
 重写的函数返回类型、 名称和自变量列表。  请注意，重写的函数不需要具有重写的函数相同的名称。  
  
 *type*  
 包含用于重写的函数的基类型。  
  
 *函数*  
 以逗号分隔的一个或多个要重写的函数名称列表。  
  
 *重写函数定义*  
 定义重写的函数 function 正文语句。  
  
 **备注**  
  
 使用显式重写创建别名对于方法签名，或以提供有关方法 witht 相同的签名的不同实现。  
  
 有关修改继承的类型和继承的类型成员的行为的信息，请参阅[重写说明符](../windows/override-specifiers-cpp-component-extensions.md)。  
  
## <a name="windows-runtime"></a>Windows 运行时  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 **备注**  
  
 有关显式信息在本机代码中重写或使用代码编译**/clr:oldSyntax**，请参阅[显式重写](../cpp/explicit-overrides-cpp.md)。  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的代码示例演示一个简单的、 隐式重写和一个的成员的实现在基接口中，不使用显式重写。  
  
```  
// explicit_override_1.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
}  
```  
  
 **输出**  
  
```Output  
X::f override of I1::f  
```  
  
 **示例**  
  
 下面的代码示例演示如何实现所有接口成员具有公共签名使用显式重写语法。  
  
```  
  
// explicit_override_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
interface struct I2 {  
   virtual void f();  
};  
  
ref struct X : public I1, I2 {  
   virtual void f() = I1::f, I2::f {  
      System::Console::WriteLine("X::f override of I1::f and I2::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   I2 ^ MyI2 = gcnew X;  
   MyI -> f();  
   MyI2 -> f();  
}  
```  
  
 **输出**  
  
```Output  
X::f override of I1::f and I2::f  
X::f override of I1::f and I2::f  
```  
  
 **示例**  
  
 下面的代码示例显示如何函数重写可以有与它正在实现的函数的名称不同。  
  
```  
// explicit_override_3.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void g() = I1::f {  
      System::Console::WriteLine("X::g");  
   }  
};  
  
int main() {  
   I1 ^ a = gcnew X;  
   a->f();  
}  
```  
  
 **输出**  
  
```Output  
X::g  
```  
  
 **示例**  
  
 下面的代码示例显示一个显式接口实现，实现类型安全集合。  
  
```  
// explicit_override_4.cpp  
// compile with: /clr /LD  
using namespace System;  
ref class R : ICloneable {  
   int X;  
  
   virtual Object^ C() sealed = ICloneable::Clone {  
      return this->Clone();  
   }  
  
public:  
   R() : X(0) {}  
   R(int x) : X(x) {}  
  
   virtual R^ Clone() {  
      R^ r = gcnew R;  
      r->X = this->X;  
      return r;  
   }  
};  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)