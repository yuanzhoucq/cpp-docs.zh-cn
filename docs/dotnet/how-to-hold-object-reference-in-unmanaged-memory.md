---
title: "如何：在非托管内存中保存对象引用 | Microsoft Docs"
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
  - "gcroot 关键字 [C++], 本机函数中的对象引用"
  - "对象引用, 本机函数中"
  - "对象 [C++], 本机函数中的引用"
  - "引用, 本机函数中的对象"
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在非托管内存中保存对象引用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用 gcroot.h（该文件包装了 <xref:System.Runtime.InteropServices.GCHandle>）在非托管内存中保存 CLR 对象引用。  也可以直接使用 `GCHandle`。  
  
## 示例  
  
```  
// hold_object_reference.cpp  
// compile with: /clr  
#include "gcroot.h"  
using namespace System;  
  
#pragma managed  
class StringWrapper {  
  
private:  
   gcroot<String ^ > x;  
  
public:  
   StringWrapper() {  
      String ^ str = gcnew String("ManagedString");  
      x = str;  
   }  
  
   void PrintString() {  
      String ^ targetStr = x;  
      Console::WriteLine("StringWrapper::x == {0}", targetStr);  
   }  
};  
#pragma unmanaged  
int main() {  
   StringWrapper s;  
   s.PrintString();  
}  
```  
  
  **StringWrapper::x \=\= ManagedString**   
## 示例  
 `GCHandle` 为您提供在非托管内存中保存托管对象引用的方式。可以使用 <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> 方法创建托管对象的不透明句柄，并使用 <xref:System.Runtime.InteropServices.GCHandle.Free%2A> 方法释放该句柄。  另外，<xref:System.Runtime.InteropServices.GCHandle.Target%2A> 方法允许您从托管代码的句柄中取回对象引用。  
  
```  
// hold_object_reference_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma managed  
class StringWrapper {  
   IntPtr m_handle;  
public:  
   StringWrapper() {  
      String ^ str = gcnew String("ManagedString");  
      m_handle = static_cast<IntPtr>(GCHandle::Alloc(str));  
   }  
   ~StringWrapper() {  
      static_cast<GCHandle>(m_handle).Free();  
   }  
  
   void PrintString() {  
      String ^ targetStr = safe_cast< String ^ >(static_cast<GCHandle>(m_handle).Target);  
      Console::WriteLine("StringWrapper::m_handle == {0}", targetStr);  
   }  
};  
  
#pragma unmanaged  
int main() {  
   StringWrapper s;   
   s.PrintString();  
}  
```  
  
  **StringWrapper::m\_handle \=\= ManagedString**   
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)