---
title: "如何： 使用 PInvoke 从托管代码调用本机 Dll |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5d22f493a582b6ef09615f94c7b321a7cc535e5b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>如何：使用 PInvoke 从托管代码调用本机 DLL
可以使用平台调用 (P/Invoke) 的功能的托管代码中调用在非托管 Dll 中实现的函数。 如果该 DLL 的源代码不可用，P/Invoke 是唯一的选项来进行互操作。 但是，不同于其他.NET 语言，Visual c + + 提供 P/Invoke 的替代方法。 有关详细信息，请参阅[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
## <a name="example"></a>示例  
 下面的代码示例使用 Win32 [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385)函数以检索屏幕以像素为单位的当前分辨率。  
  
 对于只使用内部类型作为自变量和返回值的函数，任何额外工作不是必需的。 其他数据类型，如函数指针、 数组和结构，需要确保正确地执行数据封送处理的其他属性。  
  
 尽管这不是必需的但是很好的做法，若要使 P/Invoke 声明的值类的静态成员，以便它们不存在于全局命名空间，在此示例中所示。  
  
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
  
## <a name="see-also"></a>请参阅  
 [在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)