---
title: "编译器错误 C3899 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3899"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3899"
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器错误 C3899
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”: 不允许在类“class”的并行区域内直接使用 initonly 数据成员的左值  
  
 [initonly](../../dotnet/initonly-cpp-cli.md) 数据成员无法在 [parallel](../../parallel/openmp/reference/parallel.md) 区域中构造函数的该部分内初始化。这是因为编译器执行了该代码的内部重定位，因此，它不再是构造函数的一部分。  
  
 要解决此问题，请初始化构造函数中的 initonly 数据成员，但是要在并行区域外进行。  
  
## 示例  
 下面的示例生成 C3899。  
  
```  
// C3899.cpp  
// compile with: /clr /openmp  
#include <omp.h>   
  
public ref struct R {  
   initonly int x;  
   R() {  
      x = omp_get_thread_num() + 1000;   // OK  
      #pragma omp parallel num_threads(5)  
      {  
         // cannot assign to 'x' here  
         x = omp_get_thread_num() + 1000;   // C3899  
         System::Console::WriteLine("thread {0}", omp_get_thread_num());  
      }  
      x = omp_get_thread_num() + 1000;   // OK  
   }  
};  
  
int main() {  
   R^ r = gcnew R;  
   System::Console::WriteLine(r->x);  
}  
```