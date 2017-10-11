---
title: "编译器错误 C3899 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3899
dev_langs:
- C++
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c7d9d32b3063dbecde375159ad90eec5bf128d56
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3899"></a>编译器错误 C3899
var： 左值使用 initonly 数据成员不允许直接在类 class 中的并行区域内  
  
 [Initonly (C + + /cli CLI)](../../dotnet/initonly-cpp-cli.md)数据成员不能初始化该部分中的构造函数内[并行](../../parallel/openmp/reference/parallel.md)区域。  这是由于编译器执行该代码，内部重定位，以便它不再有效地构造函数的一部分。  
  
 若要解决，初始化在构造函数中，但在并行区域外的 initonly 数据成员。  
  
## <a name="example"></a>示例  
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
