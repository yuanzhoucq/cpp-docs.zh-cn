---
title: "如何：使用 PInvoke 封送嵌入式指针 | Microsoft Docs"
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
  - "数据封送处理 [C++], 嵌入式指针"
  - "嵌入式指针 [C++]"
  - "互操作 [C++], 嵌入式指针"
  - "封送处理 [C++], 嵌入式指针"
  - "平台调用 [C++], 嵌入式指针"
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：使用 PInvoke 封送嵌入式指针
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用平台调用 \(P\/Invoke\) 功能，可以从托管代码调用在非托管 DLL 中实现的函数。  如果 DLL 的源代码不可用，P\/Invoke 就是进行交互操作的唯一选择。  但是，与其他 .NET 语言不同，Visual C\+\+ 提供了一种替代 P\/Invoke 的方法。  有关更多信息，请参见[使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)和[如何：使用 C\+\+ 互操作封送嵌入式指针](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。  
  
## 示例  
 向本机代码传递结构时要求创建一个数据布局与本机结构等效的托管结构。  但是，包含指针的结构需要进行特殊处理。  对于本机结构中的每个嵌入的指针，结构的托管版本应包含 <xref:System.IntPtr> 类型的一个实例。  而且，用于这些实例的内存必须使用 <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>、<xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A> 和 <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> 方法来显式分配、初始化和释放。  
  
 下面的代码由一个非托管模块和一个托管模块组成。  非托管模块是一个 DLL，它定义一个接受包含指针且名为 ListString 的结构的函数，以及一个名为 TakesListStruct 的函数。  托管模块是一个命令行应用程序，它导入 TakesListStruct 函数并定义名为 MListStruct 的结构，该结构与本机 ListStruct 等效，区别在于 double\* 由 <xref:System.IntPtr> 实例来表示。  调用 TakesListStruct 之前，主函数将分配并初始化此字段引用的内存。  
  
 该托管模块使用 \/clr 进行编译，但 \/clr:pure 也适用。  
  
```  
// TraditionalDll6.cpp  
// compile with: /EHsc /LD  
#include <stdio.h>  
#include <iostream>  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
#pragma pack(push, 8)  
struct ListStruct {  
   int count;  
   double* item;  
};  
#pragma pack(pop)  
  
extern "C" {  
   TRADITIONALDLL_API void TakesListStruct(ListStruct);  
}  
  
void TakesListStruct(ListStruct list) {  
   printf_s("[unmanaged] count = %d\n", list.count);  
   for (int i=0; i<list.count; i++)  
      printf_s("array[%d] = %f\n", i, list.item[i]);  
}  
```  
  
```  
// EmbeddedPointerMarshalling.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[StructLayout(LayoutKind::Sequential, Pack=8)]  
value struct MListStruct {  
   int count;  
   IntPtr item;  
};  
  
value struct TraditionalDLL {  
    [DllImport("TraditionalDLL6.dll")]  
   static public void TakesListStruct(MListStruct);  
};  
  
int main() {  
   array<double>^ parray = gcnew array<double>(10);  
   Console::WriteLine("[managed] count = {0}", parray->Length);  
  
   Random^ r = gcnew Random();  
   for (int i=0; i<parray->Length; i++) {  
      parray[i] = r->NextDouble() * 100.0;  
      Console::WriteLine("array[{0}] = {1}", i, parray[i]);  
   }  
  
   int size = Marshal::SizeOf(double::typeid);  
   MListStruct list;  
   list.count = parray->Length;  
   list.item = Marshal::AllocCoTaskMem(size * parray->Length);  
  
   for (int i=0; i<parray->Length; i++) {  
      IntPtr t = IntPtr(list.item.ToInt32() + i * size);  
      Marshal::StructureToPtr(parray[i], t, false);  
   }  
  
   TraditionalDLL::TakesListStruct( list );  
   Marshal::FreeCoTaskMem(list.item);  
}  
```  
  
 请注意，使用传统的 \#include 指令不会向托管代码公开 DLL 的任何部分。  实际上，仅在运行时访问 DLL，所以在编译时将检测不到使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 导入的函数所存在的问题。  
  
## 请参阅  
 [在 C\+\+ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)