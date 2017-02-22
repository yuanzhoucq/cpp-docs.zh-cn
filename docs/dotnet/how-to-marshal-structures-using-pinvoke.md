---
title: "如何：使用 PInvoke 封送结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据封送处理 [C++], 结构"
  - "互操作 [C++], 结构"
  - "封送处理 [C++], 结构"
  - "平台调用 [C++], 结构"
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# 如何：使用 PInvoke 封送结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此文档说明如何通过使用 P\/Invoke 从提供 <xref:System.String> 实例的托管函数调用接受 C 样式字符串的本机函数。  虽然建议您使用 C\+\+ Interop 功能而不是 P\/Invoke（因为 P\/Invoke 几乎不提供编译时错误报告，它不是类型安全的，实现起来可能单调乏味），但是如果将非托管 API 打包为 DLL，而源代码又不可用，则 P\/Invoke 就成为唯一的选择。  另请参见下列文档：  
  
-   [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [How to: Marshal Structures Using PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
 默认情况下，本机结构和托管结构在内存中的布局有所不同，因此，若要跨托管\/非托管边界成功传递结构，需要执行一些额外步骤来保持数据的完整性。  
  
 此文档说明定义本机结构的托管等效项时需要执行的步骤，并说明如何将得到的结构传递给非托管函数。  此文档假定使用的是简单结构（不包含字符串或指针）。  有关非直接复制到本机结构中的互操作性的更多信息，请参见[使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  P\/Invoke 不能将非直接复制到本机结构中的类型作为返回值。  可直接复制到本机结构中的类型在托管和非托管代码中具有相同的表示形式。  有关详细信息，请参阅[可直接复制到本机结构中的类型和非直接复制到本机结构中的类型](../Topic/Blittable%20and%20Non-Blittable%20Types.md)。  
  
 跨托管\/非托管边界封送简单的、可直接复制到本机结构中的结构首先要求定义每个本机结构的托管版本。  这些结构可以具有任何合法名称；除了数据布局之外，两个结构的本机版本和托管版本之间没有任何关系。  因此，托管版本包含的字段必须与本机版本的大小和顺序相同，这一点很重要。（没有确保结构的托管版本和本机版本等效的机制，因此在运行之前不会出现不兼容现象。  由程序员负责确保两个结构具有相同的数据布局。）  
  
 有时，出于对性能的考虑，会对托管结构的成员进行重新排列，因此有必要使用 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 特性指示该结构为顺序布局。  将结构封装设置显式设置为与本机结构所使用的设置相同的设置也是一个好办法。（尽管在默认情况下 Visual C\+\+ 对托管代码都使用 8 字节结构封装。）  
  
1.  接着，使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 声明对应于任何接受该结构的非托管函数的入口点，而在函数签名中使用结构的托管版本（如果对结构的两个版本使用相同的名称，则这样做将没有任何意义）。  
  
2.  现在，尽管托管代码实际上是托管函数，但仍可将托管版本的结构传递给非托管函数。  可通过值或引用传递这些结构，如下面的示例所示。  
  
## 示例  
 下面的代码由一个非托管模块和一个托管模块组成。  非托管模块是一个 DLL，它定义了一个名为 Location 的结构和一个名为 GetDistance 的函数，该函数接受 Location 结构的两个实例。  第二个模块是一个托管命令行应用程序，它导入 GetDistance 函数，但在 Location 结构的托管等效项 \(MLocation\) 中是对其进行定义。  在实际应用中，结构的两种版本可能使用相同的名称；但是这里使用了不同的名称，以说明该 DllImport 原型是根据托管版本定义的。  
  
 该托管模块使用 \/clr 进行编译，但 \/clr:pure 也适用。  
  
 请注意，使用传统的 \#include 指令不会向托管代码公开 DLL 的任何部分。  实际上，仅在运行时访问 DLL，所以在编译时将检测不到使用 DllImport 导入的函数所存在的问题。  
  
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
  
## 示例  
  
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
  
  **\[unmanaged\] loc1\(0,0\) loc2\(100,100\)**  
**\[managed\] distance \= 141.42135623731**  
**\[unmanaged\] Initializing location...**  
**\[managed\] x\=50 y\=50**   
## 请参阅  
 [在 C\+\+ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)