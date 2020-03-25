---
title: 编译器警告（等级 2）C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 601b99eec4625e9b598ece4cbb74d0039ad04bf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161784"
---
# <a name="compiler-warning-level-2-c4412"></a>编译器警告（等级 2）C4412

> "*function*"：函数签名包含类型 "*type*";C++对象在纯代码与混合或本机之间传递是不安全的。

## <a name="remarks"></a>备注

**/Clr： pure**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。 如果你的代码需要纯代码，我们建议你将其移植到C#。

编译器检测到可能会导致运行时错误的可能不安全的情况：从 **/clr： pure**编译单位到通过 dllimport 导入的函数进行调用，并且函数签名包含不安全的类型。 如果某个类型包含成员函数，或者该类型的数据成员是不安全类型或为不安全类型的间接寻址，则该类型是不安全的。

这是不安全的，因为在纯代码和本机代码（或混合本机代码和托管的）之间存在不同的默认调用约定。 在将函数 `dllimport`导入到 **/clr： pure**编译单位中时，请确保签名中每个类型的声明与导出函数的编译单位中的声明相同（特别小心地了解隐式调用约定中的差异）。

虚拟成员函数特别容易产生意外的结果。  但是，甚至应该对非虚拟函数进行测试，以确保获得正确的结果。 如果确实要获得正确的结果，可以忽略此警告。

默认情况下，C4412 处于关闭状态。 有关详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)和[dllimport](../../cpp/dllexport-dllimport.md) 。

若要解决此警告，请从类型中删除所有函数。

## <a name="example"></a>示例

下面的示例生成 C4412。

```cpp
// C4412.cpp
// compile with: /c /W2 /clr:pure
#pragma warning (default : 4412)

struct Unsafe {
   virtual void __cdecl Test();
};

struct Safe {
   int i;
};

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   Unsafe *pUnsafe = func();   // C4412
   // pUnsafe->Test();

   Safe *pSafe = func2();   // OK
}
```

## <a name="example"></a>示例

下面的示例是一个声明两个类型的标头文件。 `Unsafe` 类型是不安全的，因为它具有成员函数。

```cpp
// C4412.h
struct Unsafe {
   // will be __clrcall if #included in pure compilation
   // defaults to __cdecl in native or mixed mode compilation
   virtual void Test(int * pi);

   // try the following line instead
   // virtual void __cdecl Test(int * pi);
};

struct Safe {
   int i;
};
```

## <a name="example"></a>示例

此示例将函数导出到头文件中定义的类型。

```cpp
// C4412_2.cpp
// compile with: /LD
#include "C4412.h"

void Unsafe::Test(int * pi) {
   *pi++;
}

__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }
```

## <a name="example"></a>示例

**/Clr： pure**编译中的默认调用约定不同于本机编译。  当包含 C4412 时，`Test` 默认为 `__clrcall`。 如果编译并运行此程序（不使用 **/c**），程序将引发异常。

下面的示例生成 C4412。

```cpp
// C4412_3.cpp
// compile with: /W2 /clr:pure /c /link C4412_2.lib
#pragma warning (default : 4412)
#include "C4412.h"

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   int n = 7;
   Unsafe *pUnsafe = func();   // C4412
   pUnsafe->Test(&n);

   Safe *pSafe = func2();   // OK
}
```
