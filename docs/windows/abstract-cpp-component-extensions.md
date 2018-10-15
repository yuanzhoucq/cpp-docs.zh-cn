---
title: 抽象 (C + + /cli 和 C + + /cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
dev_langs:
- C++
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78a5b42de6b0ac54d060bb6369566aa446863289
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328189"
---
# <a name="abstract--ccli-and-ccx"></a>抽象 (C + + /cli 和 C + + /cli CX)

**抽象**关键字声明以下两者：

- 类型可被用作基类型，但其自身无法进行实例化。

- 只可在派生类型中定义类型成员函数。

## <a name="all-platforms"></a>所有平台

### <a name="syntax"></a>语法

*类声明**类标识符***抽象 {}**

**虚拟***返回类型**成员函数标识符* **（） 抽象;**

### <a name="remarks"></a>备注

第一个示例语法将类声明为抽象类。 *类声明*组件可以是一个本机 c + + 声明 (**类**或**结构**)，或 c + + 扩展声明 (**ref 类**或**ref 结构**) 如果`/ZW`或`/clr`指定编译器选项。

第二个示例语法将虚拟成员函数声明为抽象函数。 将函数声明为抽象函数等同于将其声明为纯虚拟函数。 将成员函数声明为抽象函数也会导致封闭类声明为抽象类。

**抽象**关键字支持本机和特定于平台的代码中; 也就是说，它可编译带有或不带`/ZW`或`/clr`编译器选项。

您可以在编译时检测类型是否为抽象与`__is_abstract(type)`类型特征。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。

**抽象**关键字是上下文相关的重写说明符。 有关上下文相关关键字的详细信息，请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。 有关重写说明符的详细信息，请参阅[如何： 在本机编译中声明重写说明符](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

## <a name="windows-runtime"></a>Windows 运行时

有关详细信息，请参阅[Ref 类和结构](../cppcx/ref-classes-and-structs-c-cx.md)。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的代码示例生成一个错误，因为类`X`砆**抽象**。

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

下面的代码示例生成一个错误，因为它实例化被标记为本机类**抽象**。 无论是否使用 `/clr` 编译器选项，都将出现此错误。

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

下面的代码示例生成一个错误，因为函数`f`包含了一个定义，但却标记**抽象**。 示例中的最后一条语句显示声明抽象虚拟函数等效于声明纯虚拟函数。

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

[适用于.NET 和 UWP 组件扩展](../windows/component-extensions-for-runtime-platforms.md)
