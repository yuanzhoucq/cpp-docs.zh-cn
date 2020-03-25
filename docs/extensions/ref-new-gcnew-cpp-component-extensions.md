---
title: ref new、gcnew（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
ms.openlocfilehash: f7269a62d7899df4eb89f6dd9487310c0fda0b4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181806"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>ref new、gcnew（C++/CLI 和 C++/CX）

ref new 聚合关键字分配在对象不可访问时垃圾回收的类型实例，并返回指向已分配对象的句柄 ([^](handle-to-object-operator-hat-cpp-component-extensions.md)) 。

## <a name="all-runtimes"></a>所有运行时

ref new 分配的类型实例的内存会自动解除分配。

如果无法分配内存，ref new 操作抛出 `OutOfMemoryException`。

若要详细了解如何分配和解除分配本机 C++ 类型的内存，请参阅 [new 和 delete 运算符](../cpp/new-and-delete-operators.md)。

## <a name="windows-runtime"></a>Windows 运行时

ref new 可用于为要自动管理其生存期的 Windows 运行时对象分配内存。 对象会在其引用计数变为零（这会在引用的最后一个副本超出范围之后发生）时自动释放。 有关详细信息，请参阅 [ref class 和 ref struct](../cppcx/ref-classes-and-structs-c-cx.md)。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

托管类型（引用类型或值类型）的内存由 gcnew 分配，并使用垃圾回收来解除分配。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的示例使用 gcnew 分配 Message 对象。

```cpp
// mcppv2_gcnew_1.cpp
// compile with: /clr
ref struct Message {
   System::String^ sender;
   System::String^ receiver;
   System::String^ data;
};

int main() {
   Message^ h_Message  = gcnew Message;
  //...
}
```

下面的示例使用 gcnew 创建装箱值类型以供使用（如引用类型）。

```cpp
// example2.cpp : main project file.
// compile with /clr
using namespace System;
value class Boxed {
    public:
        int i;
};
int main()
{
    Boxed^ y = gcnew Boxed;
    y->i = 32;
    Console::WriteLine(y->i);
    return 0;
}
```

```Output
32
```

## <a name="see-also"></a>另请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
