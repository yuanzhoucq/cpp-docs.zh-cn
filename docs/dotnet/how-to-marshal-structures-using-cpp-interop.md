---
title: "如何： 使用 c + + 互操作封送结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- C++ Interop, structures
- structures [C++], marshaling
- data marshaling [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 85c0b4301b0fb55acdc74344d1ca3fc1b6b393d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-structures-using-c-interop"></a>如何：使用 C++ 互操作封送结构
本主题演示 Visual c + + 互操作性的一个的方面。 有关详细信息，请参阅[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 下面的代码示例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指令来实现托管和非托管函数中同一文件中，但如果在单独的文件中定义，这些函数互操作方式相同。 仅包含非托管的函数的文件不需要使用编译[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示的值和按引用从托管到非托管函数传递结构。 因为在此示例中的结构包含仅简单的内部数据类型 (请参阅[本机结构中和非 Blittable 类型](http://msdn.microsoft.com/Library/d03b050e-2916-49a0-99ba-f19316e5c1b3))，是必需的没有特殊封送处理。 若要封送非本机结构中的结构，例如包含的指针，请参阅[How to： 封送嵌入式指针使用 c + + 互操作](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。  
  
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
 下面的示例演示将结构从非托管传递到托管函数的值和引用。 因为在此示例中的结构包含仅简单的内部数据类型 (请参阅[本机结构中和非 Blittable 类型](http://msdn.microsoft.com/Library/d03b050e-2916-49a0-99ba-f19316e5c1b3))，是必需的任何特殊的封送处理。 若要封送非本机结构中的结构，例如包含的指针，请参阅[How to： 封送嵌入式指针使用 c + + 互操作](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。  
  
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