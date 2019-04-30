---
title: 编译器警告（等级 2）C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 2c9d50fc3433321c0ca92366a512892212545754
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402432"
---
# <a name="compiler-warning-level-2-c4412"></a>编译器警告（等级 2）C4412

> '*函数*： 函数签名包含类型*类型*';C++对象是不安全纯代码之间传递与混合或本机。

## <a name="remarks"></a>备注

**/Clr: pure**编译器选项在 Visual Studio 2015 中弃用并在 Visual Studio 2017 中不受支持。 如果你有必须是纯的代码，我们建议你移植到C#。

编译器检测到潜在的不安全的情况下，可能会导致运行时错误： 从正在进行调用 **/clr: pure**通过 dllimport 和函数签名已导入的函数编译单位包含不安全类型. 一种类型是不安全的如果它包含的成员函数或有一个数据成员，是不安全的类型或为不安全类型间接寻址。

这是不安全的由于中的默认调用约定纯代码和本机代码之间的差异 （或混合本机和托管）。 导入时 (通过`dllimport`) 到函数 **/clr: pure**编译单位，确保在签名中的每种类型的声明与导出 （要特别注意该函数将编译单位中的相同差异隐式调用约定）。

虚拟成员函数是特别容易产生意外的结果。  但是，应测试甚至非虚拟函数，以确保获得正确的结果。 如果确定你将获得正确结果，可以忽略此警告。

默认情况下，C4412 处于关闭状态。 请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)并[dllexport、 dllimport](../../cpp/dllexport-dllimport.md)有关详细信息。

若要解决此警告，请从类型中移除所有函数。

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

下面的示例是声明了两种类型的标头文件。 `Unsafe`类型是不安全，因为它具有成员函数。

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

此示例使用标头文件中定义的类型导出函数。

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

默认调用约定 **/clr: pure**编译与本机编译的区别。  如果包括，则包括 C4412.h`Test`默认为`__clrcall`。 如果编译并运行此程序 (不使用 **/c**)，该程序将引发异常。

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