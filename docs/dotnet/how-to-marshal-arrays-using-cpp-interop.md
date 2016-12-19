---
title: "如何：使用 C++ 互操作封送数组 | Microsoft Docs"
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
  - "数组 [C++], 封送处理"
  - "C++ 互操作, 数组"
  - "数据封送处理 [C++], 数组"
  - "互操作 [C++], 数组"
  - "封送处理 [C++], 数组"
ms.assetid: c2b37ab1-8acf-4855-ad3c-7d2864826b14
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C++ 互操作封送数组
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题演示 Visual C\+\+ 互操作性的一个方面。  有关详细信息，请参阅[使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 下面的代码示例使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) \#pragma 指令在同一个文件中实现托管函数和非托管函数，但如果在不同的文件中定义这些函数，则它们将以同样的方式进行交互操作。  不需要使用 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md) 对仅包含非托管函数的文件进行编译。  
  
## 示例  
 下面的示例演示如何向非托管函数传递托管数组。  在调用非托管函数之前，托管函数使用 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md) 来取消数组的垃圾回收。  通过向非托管函数提供 GC 堆中的固定指针，可避免制作数组副本的开销。  为了演示非托管函数正在访问 GC 堆内存，该示例修改了数组的内容，而且所做的更改将在托管函数继续控制时得到反映。  
  
```  
// PassArray1.cpp  
// compile with: /clr  
#ifndef _CRT_RAND_S  
#define _CRT_RAND_S  
#endif  
  
#include <iostream>  
#include <stdlib.h>  
using namespace std;  
  
using namespace System;  
  
#pragma unmanaged  
  
void TakesAnArray(int* a, int c) {  
   cout << "(unmanaged) array received:\n";  
   for (int i=0; i<c; i++)  
      cout << "a[" << i << "] = " << a[i] << "\n";  
  
   unsigned int number;  
   errno_t err;  
  
   cout << "(unmanaged) modifying array contents...\n";  
   for (int i=0; i<c; i++) {  
      err = rand_s( &number );  
      if ( err == 0 )  
         a[i] = number % 100;  
   }  
}  
  
#pragma managed  
  
int main() {  
   array<int>^ nums = gcnew array<int>(5);  
  
   nums[0] = 0;  
   nums[1] = 1;  
   nums[2] = 2;  
   nums[3] = 3;  
   nums[4] = 4;  
  
   Console::WriteLine("(managed) array created:");  
   for (int i=0; i<5; i++)  
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);  
  
   pin_ptr<int> pp = &nums[0];  
   TakesAnArray(pp, 5);  
  
   Console::WriteLine("(managed) contents:");  
   for (int i=0; i<5; i++)  
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);  
}  
```  
  
## 示例  
 下面的示例演示如何向托管函数传递非托管数组。  托管函数直接访问数组内存（而不是创建托管数组并复制数组内容），这样，在托管函数重新获得控制时，它所做的更改便可在非托管函数中得到反映。  
  
```  
// PassArray2.cpp  
// compile with: /clr   
#include <iostream>  
using namespace std;  
  
using namespace System;  
  
#pragma managed  
  
void ManagedTakesAnArray(int* a, int c) {  
   Console::WriteLine("(managed) array received:");  
   for (int i=0; i<c; i++)  
      Console::WriteLine("a[{0}] = {1}", i, a[i]);  
  
   cout << "(managed) modifying array contents...\n";  
   Random^ r = gcnew Random(DateTime::Now.Second);  
   for (int i=0; i<c; i++)  
      a[i] = r->Next(100);  
}  
  
#pragma unmanaged  
  
void NativeFunc() {  
   int nums[5] = { 0, 1, 2, 3, 4 };  
  
   printf_s("(unmanaged) array created:\n");  
   for (int i=0; i<5; i++)  
      printf_s("a[%d] = %d\n", i, nums[i]);  
  
   ManagedTakesAnArray(nums, 5);  
  
   printf_s("(ummanaged) contents:\n");  
   for (int i=0; i<5; i++)  
      printf_s("a[%d] = %d\n", i, nums[i]);  
}  
  
#pragma managed  
  
int main() {  
   NativeFunc();  
}  
```  
  
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)