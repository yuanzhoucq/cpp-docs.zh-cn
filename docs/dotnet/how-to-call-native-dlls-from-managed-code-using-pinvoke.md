---
title: "如何：使用 PInvoke 从托管代码调用本机 DLL | Microsoft Docs"
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
  - "数据封送处理 [C++], 调用本机 DLL"
  - "互操作 [C++], 调用本机 DLL"
  - "封送处理 [C++], 调用本机 DLL"
  - "平台调用 [C++], 调用本机 DLL"
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# 如何：使用 PInvoke 从托管代码调用本机 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用平台调用 \(P\/Invoke\) 功能，可以从托管代码调用在非托管 DLL 中实现的函数。  如果 DLL 的源代码不可用，P\/Invoke 就是进行交互操作的唯一选择。  但是，与其他 .NET 语言不同，Visual C\+\+ 提供了一种替代 P\/Invoke 的方法。  有关详细信息，请参阅[使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
## 示例  
 下面的代码示例使用 Win32 [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385) 函数检索屏幕的当前分辨率（以像素为单位）。  
  
 对于仅将内部类型用作参数和返回值的函数而言，并不需要其他操作。  其他数据类型（如函数指针、数组和结构）需要一些附加特性以确保进行正确的数据封送处理。  
  
 对值类的静态成员进行 P\/Invoke 声明使其不存在于全局命名空间中是个好做法（尽管并不要求），如此示例所示。  
  
```  
// pinvoke_basic.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value class Win32 {  
public:  
   [DllImport("User32.dll")]  
   static int GetSystemMetrics(int);  
  
   enum class SystemMetricIndex {  
      // Same values as those defined in winuser.h.  
      SM_CXSCREEN = 0,  
      SM_CYSCREEN = 1  
   };  
};  
  
int main() {  
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );  
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );  
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);  
}  
```  
  
## 请参阅  
 [在 C\+\+ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)