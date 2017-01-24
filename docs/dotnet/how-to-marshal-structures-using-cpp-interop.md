---
title: "如何：使用 C++ 互操作封送结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 互操作, 结构"
  - "数据封送处理 [C++], 结构"
  - "互操作 [C++], 结构"
  - "封送处理 [C++], 结构"
  - "结构 [C++], 封送处理"
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C++ 互操作封送结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题演示 Visual C\+\+ 互操作性的一个方面。  有关详细信息，请参阅[使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 下面的代码示例使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) \#pragma 指令在同一个文件中实现托管函数和非托管函数，但如果在不同的文件中定义这些函数，则它们将以同样的方式进行交互操作。  不需要使用 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md) 对仅包含非托管函数的文件进行编译。  
  
## 示例  
 下面的示例演示如何按值以及按引用从托管函数向非托管函数传递结构。  由于本示例中的结构只包含简单内部数据类型（请参见 [可直接复制到本机结构中的类型和非直接复制到本机结构中的类型](../Topic/Blittable%20and%20Non-Blittable%20Types.md)），因此不需要进行特殊的封送处理。  若要封送非直接复制到本机结构中的结构（例如包含指针的结构），请参见 [如何：使用 C\+\+ 互操作封送嵌入式指针](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。  
  
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
  
## 示例  
 下面的示例演示如何按值以及按引用从非托管函数向托管函数传递结构。  由于本示例中的结构只包含简单内部数据类型（请参见 [可直接复制到本机结构中的类型和非直接复制到本机结构中的类型](../Topic/Blittable%20and%20Non-Blittable%20Types.md)），因此不需要进行特殊的封送处理。  若要封送非直接复制到本机结构中的结构（例如包含指针的结构），请参见 [如何：使用 C\+\+ 互操作封送嵌入式指针](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。  
  
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
  
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)