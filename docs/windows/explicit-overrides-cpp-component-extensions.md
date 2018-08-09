---
title: 显式重写 （c + + 组件扩展） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1dcf129f551900792638018fa846557120e53e96
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644347"
---
# <a name="explicit-overrides--c-component-extensions"></a>显式重写（C++ 组件扩展）
本主题讨论如何显式重写基类或接口的成员。 命名的显式重写仅应该用于重写的方法与具有不同的名称派生方法。  
  
## <a name="all-runtimes"></a>所有运行时  
### <a name="syntax"></a>语法
  
```cpp  
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }  
overriding-function-declarator = function { overriding-function-definition }  
```  

### <a name="parameters"></a>参数 
 *重写函数声明符*  
 重写的函数返回类型、 名称和参数列表。  请注意，重写的函数不需要具有被重写的函数相同的名称。  
  
 *type*  
 包含用于重写的函数的基类型。  
  
 *函数*  
 以逗号分隔的一个或多个重写的函数名称的列表。  
  
 *重写函数定义*  
 定义重写的函数的函数正文语句。  
  
### <a name="remarks"></a>备注
  
 使用显式重写以创建一个别名对于方法签名，或提供方法以便使用相同的签名的不同实现。  
  
 有关修改继承的类型和继承的类型成员的行为的信息，请参阅[重写说明符](../windows/override-specifiers-cpp-component-extensions.md)。  
  
## <a name="windows-runtime"></a>Windows 运行时  
  
### <a name="requirements"></a>要求  
 编译器选项：`/ZW`  
  
## <a name="common-language-runtime"></a>公共语言运行时 
### <a name="remarks"></a>备注
  
 有关显式信息将覆盖在本机代码中或使用代码编译`/clr:oldSyntax`，请参阅[显式重写](../cpp/explicit-overrides-cpp.md)。  
  
### <a name="requirements"></a>要求  
 编译器选项：`/clr`  
  
### <a name="examples"></a>示例   
  
 下面的代码示例演示了简单的、 隐式重写和成员的实现基接口，在不使用显式重写。  
  
```cpp  
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
  
```Output  
X::f override of I1::f  
```  
  
 下面的代码示例演示如何实现所有接口成员具有公共签名，使用显式重写的语法。  
  
```cpp  
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
  
```Output  
X::f override of I1::f and I2::f  
X::f override of I1::f and I2::f  
```  
  
 下面的代码示例演示如何使函数重写具有它正在实现的函数与不同的名称。  
  
```cpp  
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
  
```Output  
X::g  
```  
  
 下面的代码示例显示了实现的类型安全集合的显式接口实现。  
  
```cpp  
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