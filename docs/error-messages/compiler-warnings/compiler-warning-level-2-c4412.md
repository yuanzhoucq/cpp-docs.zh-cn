---
title: 编译器警告 （等级 2） C4412 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4412
dev_langs:
- C++
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47659a9ba0469b8ee719dbc686ba611e876d32c1
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704008"
---
# <a name="compiler-warning-level-2-c4412"></a>编译器警告（等级 2）C4412

> *函数*： 函数签名包含类型*类型*';C + + 对象是不安全的时间间隔纯代码和混合或本机。

## <a name="remarks"></a>备注

**/Clr: pure**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。 如果你有必须是纯代码，我们建议你对 C# 移植它。

编译器检测到的可能不安全的情况下，可能会导致运行时错误： 正在进行从调用 **/clr： 纯**对已导入通过 dllimport 和函数签名的函数编译单位包含不安全类型. 一种类型是不安全的如果它包含的成员函数，或者包含不安全类型或间接寻址上的不同、 不安全类型的数据成员。

这是不安全由于中的默认调用约定纯代码和本机代码之间的差异 （或混合本机和托管）。 导入时 (通过`dllimport`) 函数导入到 **/clr: pure**编译单位，确保签名中的每种类型的声明中导出的函数 （要特别小心编译单位相同中的差异隐式调用约定）。

虚拟成员函数是特别容易产生意外的结果。  但是，应测试甚至非虚拟函数，以确保获得正确的结果。 如果您确信您处于正确的结果，你可以忽略此警告。

默认情况下，C4412 处于关闭状态。 请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)和[dllexport、 dllimport](../../cpp/dllexport-dllimport.md)有关详细信息。

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

下面的示例是声明了两种类型的标头文件。 `Unsafe`类型是不安全的因为它有一个成员函数。

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

此示例使用头文件中定义的类型中导出函数。

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

默认调用约定 **/clr: pure**编译是不同的本机编译。  包括 C4412.h 时，`Test`默认为`__clrcall`。 如果编译和运行此程序 (不使用 **/c**)，该程序将引发异常。

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