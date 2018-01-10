---
title: "如何： 使用 PInvoke 封送结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5bfca720a97ac8462afa970e54f13e0bd74a7808
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>如何：使用 PInvoke 封送结构
本文档介绍如何本机接受 C 样式字符串可以从提供的一个实例的托管函数调用的函数<xref:System.String>通过使用 P/Invoke。 尽管我们建议你使用 c + + 互操作功能而不是 P/Invoke P/Invoke 提供很少的编译时错误报告，因为不是类型安全和可单调乏味，若要实现，如果非托管的 API 打包为的 DLL，并且源代码不是可用，P/Invoke 是唯一的选项。 否则，请参阅以下文档：  
  
-   [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送结构](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
 默认情况下，本机和托管结构的布局以不同方式在内存中，成功跨托管/非托管边界传递结构要求额外的步骤来保持数据的完整性。  
  
 本文档说明定义本机结构和如何将得到的结构传递到非托管函数的托管等效项所需的步骤。 本文档假定简单结构-那些不包含字符串或指针-使用。 有关非本机互操作性的信息，请参阅[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。 P/Invoke 不能将作为返回值的非通用类型。 通用类型在托管和非托管代码中有相同的表示形式。 有关详细信息，请参阅[本机结构中和非 Blittable 类型](http://msdn.microsoft.com/Library/d03b050e-2916-49a0-99ba-f19316e5c1b3)。  
  
 封送处理简单，本机结构中的结构跨托管/非托管边界首先需要定义的每个本机结构的托管的版本。 这些结构可以具有任何合法的名称;其数据布局以外的两个结构的本机和托管版本之间没有任何关系。 因此，很重要的托管的版本包含相同的大小和本机版本的顺序相同的字段。 （没有任何机制可确保结构的托管和本机版本等效，因此不兼容问题会在运行时之前出现。 它位于程序员有责任确保两个结构具有相同的数据布局）。  
  
 由于托管结构的成员有时排列以提高性能，因此有必要使用<xref:System.Runtime.InteropServices.StructLayoutAttribute>特性以指示结构布局按顺序。 它也是一个好办法显式设置封装设置要使用的本机结构相同的结构。 （尽管默认情况下，Visual c + + 使用这两个托管代码的装箱的 8 字节结构。）  
  
1.  接下来，使用<xref:System.Runtime.InteropServices.DllImportAttribute>来声明对应接受该结构中，任何非托管函数的入口点，但使用这些函数的签名，这是没有任何意义点，如果你使用这两个版本的相同名称的结构的托管的版本结构。  
  
2.  现在托管的代码可以通过结构的托管的版本到非托管函数就像它们是实际托管的函数。 这些结构可以通过值或通过引用传递以下示例所示。  
  
## <a name="example"></a>示例  
 下面的代码由非托管和的托管的模块组成。 非托管的模块是一个 DLL，它定义结构称为位置和 GetDistance 接受位置结构的两个实例时调用的函数。 第二个模块是托管的命令行应用程序将导入 GetDistance 函数，但在位置结构，MLocation 的托管等效项方面对其进行定义。 在实践中相同的名称将可能用于结构; 这两个版本但是，不同的名称用于此处演示 DllImport 原型定义根据托管版本。  
  
 托管的模块编译 /clr，但 /clr: pure 工作原理以及。 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
 请注意，对使用传统的托管代码公开的 DLL 没有一部分 #include 指令。 实际上，会在运行时仅，访问 DLL，以便与使用 DllImport 导入的函数的问题将不会在编译时检测多。  
  
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