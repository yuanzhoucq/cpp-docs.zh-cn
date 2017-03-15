---
title: "如何：使用 C++ 互操作封送回调和委托 | Microsoft Docs"
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
  - "C++ 互操作, 回调和委托"
  - "回调 [C++], 封送处理"
  - "数据封送处理 [C++], 回调和委托"
  - "委托 [C++], 封送处理"
  - "互操作 [C++], 回调和委托"
  - "封送处理 [C++], 回调和委托"
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C++ 互操作封送回调和委托
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此主题演示如何使用 Visual C\+\+ 在托管和非托管代码之间进行回调和委托（回调的托管版本）封送处理。  
  
 下面的代码示例使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) \#pragma 指令在同一个文件中实现托管函数和非托管函数，但也可以在单独的文件中定义这些函数。  不需要使用 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md) 对仅包含非托管函数的文件进行编译。  
  
## 示例  
 下面的示例演示如何对非托管 API 进行配置以触发托管委托。  将创建一个托管委托，并使用其中一个互操作方法 <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A> 检索该委托的基础入口点。  然后将此地址传递给非托管函数，而此非托管函数将调用该地址，而不会意识到其已被实现为托管函数。  
  
 请注意，可以（但不是必须）使用 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md) 固定委托来防止其被重新定位或由垃圾回收器释放。  需要进行保护，防止过早进行垃圾回收，但固定提供了过多的保护，它不仅防止垃圾回收，而且还防止重定位。  
  
 如果由垃圾回收对委托进行重定位，则不会影响基础托管回调，因此使用 <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> 添加对该委托的引用，允许对委托进行重定位，但防止将其释放。  使用 GCHandle 而非 pin\_ptr 可减少生成托管堆碎片的潜在可能。  
  
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
  
## 示例  
 下面的示例与前面的示例类似，但在此示例中，提供的函数指针由非托管 API 存储，因此可随时调用，这要求在任意长的时间内禁止垃圾回收。  因此，下面的示例使用 <xref:System.Runtime.InteropServices.GCHandle> 的全局实例以防止对委托进行重定位，而不受函数范围的限制。  如第一个示例所述，这些示例都没必要使用 pin\_ptr，但在此示例中不再是这样，因为 pin\_ptr 的范围被限制为单个函数。  
  
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
  
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)