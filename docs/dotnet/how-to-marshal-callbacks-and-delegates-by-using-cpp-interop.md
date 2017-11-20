---
title: "如何： 封送回调和委托使用 c + + 互操作 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2a835dbdbce23f7f92f13fabd038d6e294345981
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>如何：使用 C++ 互操作封送回调和委托
本主题演示了回调的封送处理和使用 Visual c + + 的托管和非托管代码之间委托 （回调的托管的版本）。  
  
 下面的代码示例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指令来实现托管和非托管函数中同一文件中，但也可以在单独的文件定义函数。 仅包含非托管的函数的文件不需要使用编译[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何配置一个非托管的 API，用于触发的托管的委托。 创建的托管的委托和互操作的方法，之一<xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>，用于检索对委托的基础的入口点。 此地址然后传递给非托管函数，这样不必了解作为托管函数实现的事实将调用它。  
  
 请注意，就完成了可行的但不是必要的为 pin 使用的委托[pin_ptr (C + + /cli CLI)](../windows/pin-ptr-cpp-cli.md)来防止其被重新定位或释放垃圾回收器。 需要从过早垃圾回收的保护，但固定提供多是必需的因为它可以防止集合，但还可以防止重定位的保护。  
  
 如果通过垃圾回收重新位于委托，则它将不会影响其中托管回调，因此<xref:System.Runtime.InteropServices.GCHandle.Alloc%2A>用于添加对委托，允许重定位的委托，但阻止处置的引用。 而不 pin_ptr 使用 GCHandle 减少托管堆的碎片可能性。  
  
```  
// MarshalDelegate1.cpp  
// compile with: /clr  
#include <iostream>  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
// Declare an unmanaged function type that takes two int arguments  
// Note the use of __stdcall for compatibility with managed code  
typedef int (__stdcall *ANSWERCB)(int, int);  
  
int TakesCallback(ANSWERCB fp, int n, int m) {  
   printf_s("[unmanaged] got callback address, calling it...\n");  
   return fp(n, m);  
}  
  
#pragma managed  
  
public delegate int GetTheAnswerDelegate(int, int);  
  
int GetNumber(int n, int m) {  
   Console::WriteLine("[managed] callback!");  
   return n + m;  
}  
  
int main() {  
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);  
   GCHandle gch = GCHandle::Alloc(fp);  
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);  
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());  
   Console::WriteLine("[managed] sending delegate as callback...");  
  
// force garbage collection cycle to prove  
// that the delegate doesn't get disposed  
   GC::Collect();  
  
   int answer = TakesCallback(cb, 243, 257);  
  
// release reference to delegate  
   gch.Free();  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例是类似于前面的示例中，但在这种情况下提供的函数指针存储由非托管 API，因此它可以调用任何时候，需要任意长的时间内，禁止垃圾回收。 因此，下面的示例使用的全局实例<xref:System.Runtime.InteropServices.GCHandle>以防止对委托进行重定位，独立于函数范围。 第一个示例中所述，使用 pin_ptr 是不必要的这些示例中，但在这种情况下不会起作用，因为 pin_ptr 的作用域仅限于单个函数。  
  
```  
// MarshalDelegate2.cpp  
// compile with: /clr   
#include <iostream>  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
// Declare an unmanaged function type that takes two int arguments  
// Note the use of __stdcall for compatibility with managed code  
typedef int (__stdcall *ANSWERCB)(int, int);  
static ANSWERCB cb;  
  
int TakesCallback(ANSWERCB fp, int n, int m) {  
   cb = fp;  
   if (cb) {  
      printf_s("[unmanaged] got callback address (%d), calling it...\n", cb);  
      return cb(n, m);  
   }  
   printf_s("[unmanaged] unregistering callback");  
   return 0;  
}  
  
#pragma managed  
  
public delegate int GetTheAnswerDelegate(int, int);  
  
int GetNumber(int n, int m) {  
   Console::WriteLine("[managed] callback!");  
   static int x = 0;  
   ++x;  
  
   return n + m + x;  
}  
  
static GCHandle gch;  
  
int main() {  
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);  
  
   gch = GCHandle::Alloc(fp);  
  
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);  
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());  
   Console::WriteLine("[managed] sending delegate as callback...");  
  
   int answer = TakesCallback(cb, 243, 257);  
  
   // possibly much later (in another function)...  
  
   Console::WriteLine("[managed] releasing callback mechanisms...");  
   TakesCallback(0, 243, 257);  
   gch.Free();  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)