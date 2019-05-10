---
title: 如何：使用 PInvoke 封送结构
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
ms.openlocfilehash: d5c64a3e93cd85d7e38bac7c0ea3fa3c3301abc9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387235"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>如何：使用 PInvoke 封送结构

本文档介绍如何将纯函数接受 C 样式结构可以从托管函数调用通过使用 P/Invoke。 不过，我们建议你使用C++互操作功能，而不是 P/Invoke 因为 P/Invoke 提供小的编译时错误报告，不类型安全的并可能会很麻烦，若要实现，如果非托管的 API 打包为 DLL 并不是源代码可用，P/Invoke 是唯一的选项。 否则，请参阅以下文档：

- [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [如何：使用 PInvoke 封送字符串](../dotnet/how-to-marshal-strings-using-pinvoke.md)

默认情况下，本机和托管结构的布局方式以不同的方式在内存中，成功跨托管/非托管边界传递结构需要额外的步骤来保持数据的完整性。

本文档介绍了定义的本机结构，以及如何将得到的结构传递到非托管函数的托管等效项所需的步骤。 本文档假定的简单结构，不包含字符串或指针的那些 — 使用。 有关非 blittable 互操作性的信息，请参阅[使用C++互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。 P/Invoke 不能将非 blittable 类型作为返回值。 可直接复制类型在托管和非托管代码中具有相同的表示形式。 有关详细信息，请参阅[Blittable 和非 Blittable 类型](/dotnet/framework/interop/blittable-and-non-blittable-types)。

封送处理简单，可直接复制结构跨托管/非托管边界首先需要定义的每个本机结构的托管的版本。 这些结构可以具有任何合法的名称;其数据的布局以外的两个结构的本机和托管版本之间没有任何关系。 因此，非常重要的托管的版本包含相同的大小和本机版本的相同顺序中的字段。 （没有任何机制，用于确保结构的托管和本机版本等效的因此不兼容性会运行之前出现。 它是程序员的责任，以确保两个结构具有相同的数据布局）。

由于有时出于性能考虑排列的托管结构的成员，因此有必要使用<xref:System.Runtime.InteropServices.StructLayoutAttribute>特性以指示该结构顺序依次布局。 它也是最好显式设置打包设置要使用的本机结构相同的结构。 (尽管默认情况下，视觉对象C++使用装箱这两个托管代码的 8 字节的结构。)

1. 接下来，使用<xref:System.Runtime.InteropServices.DllImportAttribute>声明对应于接受结构，任何非托管函数的入口点，但使用的函数签名，这是毫无意义，如果使用这两个版本的相同名称的结构的托管的版本结构。

1. 现在托管的代码可传递结构的托管的的版本的非托管函数就好像它们是实际托管的函数。 这些结构可以传递值或引用，如以下示例所示。

## <a name="example"></a>示例

下面的代码由非托管和托管的模块组成。 非托管的模块是一个 DLL，它定义了称为位置和一个名为接受两个位置结构实例的 GetDistance 函数的结构。 第二个模块是托管的命令行应用程序将导入 GetDistance 函数，但其定义的托管等效项的位置结构 MLocation 方面。 在实践中相同的名称可能用于结构; 这两个版本但是，不同的名称用于此处演示的 DllImport 原型定义根据托管版本。

请注意该 DLL 的任何部分公开给托管代码使用的传统 #include 指令。 事实上，DLL 访问在运行时仅，因此不会在编译时检测问题的函数与 DllImport 导入。

```
// TraditionalDll3.cpp
// compile with: /LD /EHsc
#include <iostream>
#include <stdio.h>
#include <math.h>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
   #define TRADITIONALDLL_API __declspec(dllexport)
#else
   #define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct Location {
   int x;
   int y;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API double GetDistance(Location, Location);
   TRADITIONALDLL_API void InitLocation(Location*);
}

double GetDistance(Location loc1, Location loc2) {
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   printf_s("[unmanaged] Initializing location...\n");
   lp->x = 50;
   lp->y = 50;
}
```

## <a name="example"></a>示例

```
// MarshalStruct_pi.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MLocation {
   int x;
   int y;
};

value struct TraditionalDLL {
   [DllImport("TraditionalDLL3.dll")]
   static public double GetDistance(MLocation, MLocation);
   [DllImport("TraditionalDLL3.dll")]
   static public double InitLocation(MLocation*);
};

int main() {
   MLocation loc1;
   loc1.x = 0;
   loc1.y = 0;

   MLocation loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = TraditionalDLL::GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   MLocation loc3;
   TraditionalDLL::InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

```Output
[unmanaged] loc1(0,0) loc2(100,100)
[managed] distance = 141.42135623731
[unmanaged] Initializing location...
[managed] x=50 y=50
```

## <a name="see-also"></a>请参阅

[在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
