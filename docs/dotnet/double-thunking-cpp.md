---
title: 双重 Thunk (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
ms.openlocfilehash: 89cca9ef42910d295cbae8bb677fb51927dbcdd2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545347"
---
# <a name="double-thunking-c"></a>双重 Thunk (C++)

Double thunk 是指当托管上下文中的函数调用调用视觉对象C++托管函数，并且程序执行调用该函数的本机入口点以调用托管函数时，您可能会遇到的性能损失。 本主题讨论双重 thunk 发生的位置以及如何避免它来提高性能。

## <a name="remarks"></a>备注

默认情况下，使用 **/clr**进行编译时，托管函数的定义将导致编译器生成托管入口点和本机入口点。 这允许从本机和托管调用站点调用托管函数。 但是，当存在本机入口点时，它可以是对函数的所有调用的入口点。 如果调用函数是托管的，则本机入口点将调用托管入口点。 实际上，调用函数需要两次调用（因此，需要双 thunk）。 例如，虚函数始终通过本机入口点调用。

一种解决方法是让编译器不生成托管函数的本机入口点，而只会使用[__clrcall](../cpp/clrcall.md)调用约定从托管上下文调用该函数。

同样，如果导出（[dllexport，dllimport](../cpp/dllexport-dllimport.md)）托管函数，则会生成一个本机入口点，并且任何导入和调用该函数的函数都将通过本机入口点调用。 若要避免在此情况下出现双重 thunk，请不要使用本机导出/导入语义;只需通过 `#using` 引用元数据（请参阅[#using 指令](../preprocessor/hash-using-directive-cpp.md)）。

已更新编译器以减少不必要的双 thunk。 例如，签名中具有托管类型的任何函数（包括返回类型）都将隐式标记为 `__clrcall`。

## <a name="example"></a>示例

### <a name="description"></a>说明

下面的示例演示 double thunk。 编译本机（不包含 **/clr**）时，对 `main` 中虚拟函数的调用将生成一个对 `T`的复制构造函数和一个对析构函数的调用。 当用 **/clr**和 `__clrcall`声明虚函数时，就会实现类似的行为。 但是，在使用 **/clr**进行编译时，函数调用会生成对复制构造函数的调用，但由于本机到托管的 thunk，将再次调用复制构造函数。

### <a name="code"></a>代码

```cpp
// double_thunking.cpp
// compile with: /clr
#include <stdio.h>
struct T {
   T() {
      puts(__FUNCSIG__);
   }

   T(const T&) {
      puts(__FUNCSIG__);
   }

   ~T() {
      puts(__FUNCSIG__);
   }

   T& operator=(const T&) {
      puts(__FUNCSIG__);
      return *this;
   }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;

   printf("calling struct S\n");
   pS->f(t);
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>示例输出

```
__thiscall T::T(void)
calling struct S
__thiscall T::T(const struct T &)
__thiscall T::T(const struct T &)
__thiscall T::~T(void)
__thiscall T::~T(void)
after calling struct S
__thiscall T::~T(void)
```

## <a name="example"></a>示例

### <a name="description"></a>说明

前面的示例演示了双 thunk 的存在。 此示例显示了其效果。 `for` 循环调用虚函数，程序报告执行时间。 用 **/clr**编译程序时，会报告最慢的时间。 如果在没有 **/clr**的情况下进行编译，或在 `__clrcall`中声明了虚函数，则会报告最快的时间。

### <a name="code"></a>代码

```cpp
// double_thunking_2.cpp
// compile with: /clr
#include <time.h>
#include <stdio.h>

#pragma unmanaged
struct T {
   T() {}
   T(const T&) {}
   ~T() {}
   T& operator=(const T&) { return *this; }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;
   clock_t start, finish;
   double  duration;
   start = clock();

   for ( int i = 0 ; i < 1000000 ; i++ )
      pS->f(t);

   finish = clock();
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);
   printf( "%2.1f seconds\n", duration );
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>示例输出

```
4.2 seconds
after calling struct S
```

## <a name="see-also"></a>另请参阅

[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)
