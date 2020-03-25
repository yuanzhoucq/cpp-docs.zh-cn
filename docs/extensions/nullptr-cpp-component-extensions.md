---
title: nullptr（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 02da716959deb7fcffa7a63a8308279a765c4569
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172109"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr（C++/CLI 和 C++/CX）

nullptr 关键字表示空指针值。 空指针值可用于指明对象句柄、内部指针或本机指针类型不指向对象。

结合使用 nullptr 与托管代码或本机代码。 编译器为托管空指针值和本机空指针值发出相应但不同的指令。 若要了解如何使用此关键字的 ISO 标准 C++ 版本，请参阅 [nullptr](../cpp/nullptr.md)。

__nullptr 是 Microsoft 专用关键字，虽然与 nullptr 的含义相同，但仅适用于本机代码。 如果你将 nullptr 与本机 C/C++ 代码结合使用，然后使用 [/clr](../build/reference/clr-common-language-runtime-compilation.md) 编译器选项进行编译，那么编译器便无法确定 nullptr 指明的是本机空指针值，还是托管空指针值。 若要向编译器明确表达你的意图，请使用 nullptr 来指定托管值，或使用 __nullptr 来指定本机值。

nullptr 关键字相当于 Visual Basic 中的“无”和 C# 中的“null”。

## <a name="usage"></a>使用情况

nullptr 关键字可用于任何能使用句柄、本机指针或函数参数的位置。

nullptr 关键字不是一种类型，也不支持用于：

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr`（尽管 `throw (Object^)nullptr;` 可以正常发挥作用）

nullptr 关键字可用于初始化以下指针类型：

- 本机指针

- Windows 运行时句柄

- 托管句柄

- 托管内部指针

nullptr 关键字可用于在使用指针或句柄引用之前，先测试引用是否为空。

应正确解释使用空指针值进行错误检查的语言之间的函数调用。

无法将句柄初始化为 0；只能使用 nullptr。 将常数 0 赋给对象句柄会生成装箱的 `Int32`，并强制转换为 `Object^`。

## <a name="example"></a>示例

下面的代码示例展示了 nullptr 关键字可用于任何能使用句柄、本机指针或函数参数的位置。 此示例还展示了 nullptr 关键字可用于在使用引用之前先检查引用。

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

下面的代码示例展示了可以对本机指针交换使用 nullptr 和 0。

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

下面的代码示例展示了 nullptr 被解释为指向任何类型的一个句柄，或指向任何类型的一个本机指针。 如果函数重载了多个指向不同类型的句柄，便会生成多义性错误。 必须将 nullptr 显式强制转换为一种类型。

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

下面的代码示例展示了可以强制转换 nullptr，并返回指向强制转换类型的指针或句柄，其中包含 nullptr 值。

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

下面的代码示例展示了 nullptr 可用作函数参数。

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

下面的代码示例展示了已声明但未显式初始化的句柄默认初始化为 nullptr。

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

下面的代码示例展示了在使用  **编译时，可以将 nullptr**`/clr` 赋给本机指针。

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>要求

编译器选项：（不是必需的; 由所有代码生成选项支持，包括 `/ZW` 和 `/clr`）

## <a name="see-also"></a>另请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)
