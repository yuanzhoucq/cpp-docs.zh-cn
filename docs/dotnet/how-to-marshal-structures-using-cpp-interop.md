---
title: 如何： 使用 c + + 互操作封送结构 |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ Interop, structures
- structures [C++], marshaling
- data marshaling [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bbf85f8da0477de2483ee2ce4b981d832421da95
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680897"
---
# <a name="how-to-marshal-structures-using-c-interop"></a>如何：使用 C++ 互操作封送结构
本主题演示 Visual c + + 互操作性的一个方面。 有关详细信息，请参阅[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 下面的代码示例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指令以实现托管和非托管函数中同一文件中，但如果在单独的文件中定义，这些函数互操作方式相同。 文件仅包含非托管的函数无需使用编译[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示按值和按引用从托管到非托管函数传递一个结构。 因为在此示例结构包含仅简单内部数据类型 (请参阅[Blittable 和非 Blittable 类型](/dotnet/framework/interop/blittable-and-non-blittable-types))，没有特殊封送处理是必需。 若要封送非 blittable 结构，例如包含的指针，请参阅[如何： 封送嵌入式指针使用 c + + 互操作](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。  
  
```  
// PassStruct1.cpp  
// compile with: /clr  
  
#include <stdio.h>  
#include <math.h>  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
struct Location {  
   int x;  
   int y;  
};  
  
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
  
#pragma managed  
  
int main() {  
   Location loc1;  
   loc1.x = 0;  
   loc1.y = 0;  
  
   Location loc2;  
   loc2.x = 100;  
   loc2.y = 100;  
  
   double dist = GetDistance(loc1, loc2);  
   Console::WriteLine("[managed] distance = {0}", dist);  
  
   Location loc3;  
   InitLocation(&loc3);  
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例演示按值和按引用从非托管到托管的函数，传递结构。 因为在此示例结构包含仅简单内部数据类型 (请参阅[Blittable 和非 Blittable 类型](/dotnet/framework/interop/blittable-and-non-blittable-types))，是必需的任何特殊的封送。 若要封送非 blittable 结构，例如包含的指针，请参阅[如何： 封送嵌入式指针使用 c + + 互操作](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。  
  
```  
// PassStruct2.cpp  
// compile with: /clr  
#include <stdio.h>  
#include <math.h>  
using namespace System;  
  
// native structure definition  
struct Location {  
   int x;  
   int y;  
};  
  
#pragma managed  
  
double GetDistance(Location loc1, Location loc2) {  
   Console::Write("[managed] got loc1({0},{1})", loc1.x, loc1.y);  
   Console::WriteLine(" loc2({0},{1})", loc2.x, loc2.y);  
  
   double h = loc1.x - loc2.x;  
   double v = loc1.y = loc2.y;  
   double dist = sqrt( pow(h,2) + pow(v,2) );  
  
   return dist;  
}  
  
void InitLocation(Location* lp) {  
   Console::WriteLine("[managed] Initializing location...");  
   lp->x = 50;  
   lp->y = 50;  
}  
  
#pragma unmanaged  
  
int UnmanagedFunc() {  
   Location loc1;  
   loc1.x = 0;  
   loc1.y = 0;  
  
   Location loc2;  
   loc2.x = 100;  
   loc2.y = 100;  
  
   printf_s("(unmanaged) loc1=(%d,%d)", loc1.x, loc1.y);  
   printf_s(" loc2=(%d,%d)\n", loc2.x, loc2.y);  
  
   double dist = GetDistance(loc1, loc2);  
   printf_s("[unmanaged] distance = %f\n", dist);  
  
   Location loc3;  
   InitLocation(&loc3);  
   printf_s("[unmanaged] got x=%d y=%d\n", loc3.x, loc3.y);  
  
    return 0;  
}  
  
#pragma managed  
  
int main() {  
   UnmanagedFunc();  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)