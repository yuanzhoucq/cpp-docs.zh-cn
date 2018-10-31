---
title: nullptr (C + + /cli 和 C + + /cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 25ecf09d4794500bbc53f7f555380b050d394c71
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056602"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C + + /cli 和 C + + /cli CX)

**Nullptr**关键字表示*为 null 指针值*。 使用 null 指针值指示，对象句柄、 内部指针或本机指针类型不指向对象。

使用**nullptr** ，托管或本机代码。 编译器会发出相应但不同的托管和本机 null 指针值的说明。 有关使用此关键字的 ISO 标准 c + + 版本的信息，请参阅[nullptr](../cpp/nullptr.md)。

**__Nullptr**关键字是具有相同含义的 Microsoft 专用关键字**nullptr**，但适用于仅本机代码。 如果您使用**nullptr**带有本机 C/c + + 代码和使用然后编译[/clr](../build/reference/clr-common-language-runtime-compilation.md)编译器选项，编译器无法确定是否**nullptr**指示本机或管理 null 指针值。 若要使编译器清楚地您的意图，使用**nullptr**以指定托管的值或 **__nullptr**指定本机值。

**Nullptr**关键字等效于**Nothing**在 Visual Basic 中并**null** C# 中。

## <a name="usage"></a>用法

**Nullptr**关键字可用于任何可以使用句柄、 本机指针或函数自变量的地方。

**Nullptr**关键字不是类型和不支持用于：

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr` (尽管`throw (Object^)nullptr;`起)

**Nullptr**关键字可用于以下指针类型的初始化：

- 本机指针

- Windows 运行时句柄

- 托管的句柄

- 托管的内部指针

**Nullptr**关键字可用于测试如果之前使用引用 null 指针或句柄的引用。

在使用 null 指针值来进行错误检查的语言之间的函数调用应正确解释。

无法初始化为零; 的句柄仅**nullptr**可用。 分配到的对象的句柄的常量 0 会生成一个装箱`Int32`和强制转换为`Object^`。

## <a name="example"></a>示例

下面的代码示例演示**nullptr**关键字可用于任何句柄，本机指针，或可以使用函数参数。 和的示例演示**nullptr**关键字可用于检查一个引用，然后使用它。

```cpp
// mcpp_nullptr.cpp
// compile with: /clr
value class V {};
ref class G {};
void f(System::Object ^) {}

int main() {
// Native pointer.
   int *pN = nullptr;
// Managed handle.
   G ^pG = nullptr;
   V ^pV1 = nullptr;
// Managed interior pointer.
   interior_ptr<V> pV2 = nullptr;
// Reference checking before using a pointer.
   if (pN == nullptr) {}
   if (pG == nullptr) {}
   if (pV1 == nullptr) {}
   if (pV2 == nullptr) {}
// nullptr can be used as a function argument.
   f(nullptr);   // calls f(System::Object ^)
}
```

## <a name="example"></a>示例

下面的代码示例演示**nullptr**和本机指针互换使用零。

```cpp
// mcpp_nullptr_1.cpp
// compile with: /clr
class MyClass {
public:
   int i;
};

int main() {
   MyClass * pMyClass = nullptr;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");

   pMyClass = 0;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");
}
```

```Output
pMyClass == nullptr

pMyClass == 0

pMyClass == nullptr

pMyClass == 0
```

## <a name="example"></a>示例

下面的代码示例演示**nullptr**被解释为任何类型的句柄或指向任何类型的本机指针。 如果函数重载具有不同类型的句柄，将生成多义性错误。 **Nullptr**必须显式强制转换为一种类型。

```cpp
// mcpp_nullptr_2.cpp
// compile with: /clr /LD
void f(int *){}
void f(int ^){}

void f_null() {
   f(nullptr);   // C2668
   // try one of the following lines instead
   f((int *) nullptr);
   f((int ^) nullptr);
}
```

## <a name="example"></a>示例

下面的代码示例显示了该强制转换**nullptr**允许并返回到包含的强制转换类型的指针或句柄**nullptr**值。

```cpp
// mcpp_nullptr_3.cpp
// compile with: /clr /LD
using namespace System;
template <typename T>
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type

int main() {
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)

   // Delete the following line to resolve.
   f(nullptr);

   f(0);   // T = int, call f(int)
}
```

## <a name="example"></a>示例

下面的代码示例演示**nullptr**可用作函数参数。

```cpp
// mcpp_nullptr_4.cpp
// compile with: /clr
using namespace System;
void f(Object ^ x) {
   Console::WriteLine("test");
}

int main() {
   f(nullptr);
}
```

```Output
test
```

## <a name="example"></a>示例

下面的代码示例显示了声明和未显式初始化句柄，它们都将初始化为默认**nullptr**。

```cpp
// mcpp_nullptr_5.cpp
// compile with: /clr
using namespace System;
ref class MyClass {
public:
   void Test() {
      MyClass ^pMyClass;   // gc type
      if (pMyClass == nullptr)
         Console::WriteLine("NULL");
   }
};

int main() {
   MyClass ^ x = gcnew MyClass();
   x -> Test();
}
```

```Output
NULL
```

## <a name="example"></a>示例

下面的代码示例演示**nullptr**使用编译时可以分配给本机指针`/clr`。

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>要求

编译器选项: (不需要; 支持的所有代码生成选项，包括`/ZW`和`/clr`)

## <a name="see-also"></a>请参阅

[ .NET 和 UWP 的组件扩展](../windows/component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)