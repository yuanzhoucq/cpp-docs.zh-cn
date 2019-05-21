---
title: abstract（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
ms.openlocfilehash: d5060f1a0950b9b2ac2638b99ff157983944a3bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516162"
---
# <a name="abstract--ccli-and-ccx"></a>abstract（C++/CLI 和 C++/CX）

abstract 关键字声明以下两者之一：

- 类型可被用作基类型，但其自身无法进行实例化。

- 只可在派生类型中定义类型成员函数。

## <a name="all-platforms"></a>所有平台

### <a name="syntax"></a>语法

class-declaration class-identifier abstract {}

virtual return-type member-function-identifier () abstract ;

### <a name="remarks"></a>备注

第一个示例语法将类声明为抽象类。 如果 `/ZW` 或 `/clr` 编译器选项已指定，类声明组件可以是本机 C++ 声明（class 或 struct），也可以是 C++ 扩展声明（ref class 或 ref struct）。

第二个示例语法将虚拟成员函数声明为抽象函数。 将函数声明为抽象函数等同于将其声明为纯虚拟函数。 将成员函数声明为抽象函数也会导致封闭类声明为抽象类。

本机专用代码和平台专用代码支持 abstract 关键字；也就是说，它可以使用或不使用 `/ZW` 或 `/clr` 编译器选项进行编译。

在编译时，可以使用 `__is_abstract(type)` 类型特征来检测类型是否是 abstract。 有关详细信息，请参阅[编译器对类型特征的支持](compiler-support-for-type-traits-cpp-component-extensions.md)。

abstract 关键字是上下文相关重写说明符。 若要详细了解上下文相关关键字，请参阅[上下文相关关键字](context-sensitive-keywords-cpp-component-extensions.md)。 若要详细了解重写说明符，请参阅[操作说明：在本机编译中声明重写说明符](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

## <a name="windows-runtime"></a>Windows 运行时

有关详细信息，请参阅 [ref class 和 ref struct](../cppcx/ref-classes-and-structs-c-cx.md)。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的代码示例生成了错误，因为类 `X` 被标记为 abstract。

```cpp
// abstract_keyword.cpp
// compile with: /clr
ref class X abstract {
public:
   virtual void f() {}
};

int main() {
   X ^ MyX = gcnew X;   // C3622
}
```

下面的代码示例生成了错误，因为它实例化被标记为 abstract 的本机类。 无论是否使用 `/clr` 编译器选项，都将出现此错误。

```cpp
// abstract_keyword_2.cpp
class X abstract {
public:
   virtual void f() {}
};

int main() {
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'
                    // cannot be instantiated. See declaration of 'X'}
```

下面的代码示例生成了错误，因为函数 `f` 虽包含定义，但被标记为 abstract。 示例中的最后一条语句显示声明抽象虚拟函数等效于声明纯虚拟函数。

```cpp
// abstract_keyword_3.cpp
// compile with: /clr
ref class X {
public:
   virtual void f() abstract {}   // C3634
   virtual void g() = 0 {}   // C3634
};
```

## <a name="see-also"></a>请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
