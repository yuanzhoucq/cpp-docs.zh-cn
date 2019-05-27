---
title: 显式重写（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
ms.openlocfilehash: 7d36793e4467f9454aca1eb207f3c3dfbd483bff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516672"
---
# <a name="explicit-overrides--ccli-and-ccx"></a>显式重写（C++/CLI 和 C++/CX）

本主题探讨了如何显式重写基类或基接口的成员。 已命名（显式）重写应该只用于将方法重写为名称不同的派生方法。

## <a name="all-runtimes"></a>所有运行时

### <a name="syntax"></a>语法

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>参数

overriding-function-declarator<br/>
重写函数的返回类型、名称和参数列表。  请注意，重写函数不必与被重写函数同名。

*type*<br/>
包含要重写的函数的基类型。

*函数*<br/>
一个或多个要重写的函数名称的逗号分隔列表。

overriding-function-definition<br/>
定义重写函数的函数主体语句。

### <a name="remarks"></a>备注

显式重写可用于创建方法签名的别名，或为签名相同的方法提供不同实现。

若要了解如何修改继承类型和继承类型成员的行为，请参阅[重写说明符](override-specifiers-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 运行时

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="remarks"></a>备注

若要了解本机代码或使用 `/clr:oldSyntax` 编译的代码中的显式重写，请参阅[显式重写](../cpp/explicit-overrides-cpp.md)。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的代码示例展示了如何简单隐式重写和实现基接口中的成员（未使用显式重写）。

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

下面的代码示例展示了如何使用显式重写语法来实现所有使用公共签名的接口成员。

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

下面的代码示例展示了函数重写的名称如何与它要实现的函数不同。

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

下面的代码示例展示了实现类型安全集合的显式接口实现。

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

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)