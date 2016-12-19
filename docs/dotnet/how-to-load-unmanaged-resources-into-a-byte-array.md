---
title: "如何：将非托管资源加载到一个字节数组 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "本机资源"
  - "本机资源, 加载到 Byte 数组中"
  - "非托管资源, 加载到 Byte 数组中"
ms.assetid: cdada6cd-6d42-437a-a90f-44a0b18d6a93
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将非托管资源加载到一个字节数组
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题讨论了向 <xref:System.Byte> 数组中加载非托管资源的几种方法。  
  
## 示例  
 如果知道非托管资源的大小，则可以预分配一个 CLR 数组，然后使用指向 CLR 数组的数组块的指针将资源加载到该数组中。  
  
```  
// load_unmanaged_resources_into_Byte_array.cpp  
// compile with: /clr  
using namespace System;  
void unmanaged_func( unsigned char * p ) {  
   for ( int i = 0; i < 10; i++ )  
      p[ i ] = i;  
}  
  
public ref class A {  
public:  
   void func() {  
      array<Byte> ^b = gcnew array<Byte>(10);  
      pin_ptr<Byte> p =  &b[ 0 ];  
      Byte * np = p;  
      unmanaged_func( np );   // pass pointer to the block of CLR array.  
      for ( int i = 0; i < 10; i++ )  
         Console::Write( b[ i ] );  
      Console::WriteLine();  
   }  
};  
  
int main() {  
   A^ g = gcnew A;  
   g->func();  
}  
```  
  
  **0123456789**   
## 示例  
 此示例演示如何从非托管内存块向托管数组中复制数据。  
  
```  
// load_unmanaged_resources_into_Byte_array_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#include <string.h>  
int main() {  
   char buf[] = "Native String";  
   int len = strlen(buf);  
   array<Byte> ^byteArray = gcnew array<Byte>(len + 2);  
  
   // convert any native pointer to IntPtr by doing C-Style cast  
   Marshal::Copy( (IntPtr)buf, byteArray, 0, len );  
}  
```  
  
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)