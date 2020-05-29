---
title: sealed（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
ms.openlocfilehash: ab5d5b32ceb87a3b1ccf08d170889dd4825f6c17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181793"
---
# <a name="sealed--ccli-and-ccx"></a>sealed（C++/CLI 和 C++/CX）

sealed 是 ref class 的上下文相关关键字，它指明无法重写虚成员，或类型无法用作基类型。

> [!NOTE]
> ISO C++ 11 标准语言引入了 [final](../cpp/final-specifier.md) 关键字。 对标准类使用 final，并对 ref class 使用 sealed。

## <a name="all-runtimes"></a>所有运行时

## <a name="syntax"></a>语法

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>parameters

*identifier*<br/>
函数或类的名称。

return-type<br/>
函数返回的类型。

## <a name="remarks"></a>备注

在第一个语法示例中，密封了类。 在第二个示例中，密封了虚函数。

对 ref class 及其虚成员函数使用 sealed 关键字。 有关详细信息，请参阅[重写说明符和本机编译](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

在编译时，可以使用 `__is_sealed(type)` 类型特征来检测类型是否已密封。 有关详细信息，请参阅[编译器对类型特征的支持](compiler-support-for-type-traits-cpp-component-extensions.md)。

sealed 是上下文相关关键字。  有关详细信息，请参阅[上下文相关关键字](context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 运行时

请参阅 [ref class 和 ref struct](../cppcx/ref-classes-and-structs-c-cx.md)。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

（此语言功能没有只适用于公共运行时的备注。）

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的代码示例展示了 sealed 对虚成员的效果。

```cpp
// sealed_keyword.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
   virtual void g();
};

ref class X : I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }

   virtual void g() sealed {
      System::Console::WriteLine("X::f override of I1::g");
   }
};

ref class Y : public X {
public:
   virtual void f() override {
      System::Console::WriteLine("Y::f override of I1::f");
   }

   /*
   // the following override generates a compiler error
   virtual void g() override {
      System::Console::WriteLine("Y::g override of I1::g");
   }
   */
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
   MyI -> g();

   I1 ^ MyI2 = gcnew Y;
   MyI2 -> f();
}
```

```Output
X::f override of I1::f
X::f override of I1::g
Y::f override of I1::f
```

下一个代码示例演示如何将类标记为已密封。

```cpp
// sealed_keyword_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X sealed : I1 {
public:
   virtual void f() override {}
};

ref class Y : public X {   // C3246 base class X is sealed
public:
   virtual void f() override {}
};
```

## <a name="see-also"></a>另请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
