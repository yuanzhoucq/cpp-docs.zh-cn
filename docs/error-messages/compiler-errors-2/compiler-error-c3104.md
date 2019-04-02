---
title: 编译器错误 C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: 3b2737bd67798fd467649be175d581ca551e1331
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770624"
---
# <a name="compiler-error-c3104"></a>编译器错误 C3104

特性参数非法

指定属性的无效参数。

请参阅[特性参数类型](../../extensions/attribute-parameter-types-cpp-component-extensions.md)有关详细信息。

为 Visual c + + 2005年执行的编译器一致性工作可以生成此错误： 时将托管的数组传递给自定义特性，数组的类型不能再从聚合初始化列表推导。 编译器现在要求您指定的数组初始值设定项列表的类型。

## <a name="example"></a>示例

下面的示例生成 C3104。

```
// C3104a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104
// try the following line instead
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="example"></a>示例

下面的示例生成 C3104。

```
// C3104b.cpp
// compile with: /clr /c
// C3104 expected
using namespace System;

int func() {
   return 0;
}

[attribute(All)]
ref class A {
public:
   A(int) {}
};

// Delete the following 2 lines to resolve.
[A(func())]
ref class B {};

// OK
[A(0)]
ref class B {};
```
