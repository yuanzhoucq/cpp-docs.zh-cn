---
title: "编译器错误 C3020 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3020"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3020"
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C3020
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”: OpenMP“for”循环的索引变量不能在循环体中修改  
  
 OpenMP `for` 循环不能修改 `for` 循环体中的索引（循环计数器）。  
  
 下面的示例生成 C3020：  
  
```  
// C3020.cpp  
// compile with: /openmp  
int main() {  
   int i = 0, n = 3;  
  
   #pragma omp parallel  
   {  
      #pragma omp for  
      for (i = 0; i < 10; i += n)  
         i *= 2;   // C3020  
         // try the following line instead  
         // n++;  
   }  
}  
```  
  
 使用 [lastprivate](../../parallel/openmp/reference/lastprivate.md) 声明的变量不能用作并行化循环中的索引。  
  
 对于第二个 lastprivate，下面的示例将给出 C3020，原因是该 lastprivate 将触发在最外层 for 循环内写入 idx\_a。  第一个 lastprivate 不会给出错误，原因是该 lastprivate 将触发在最外层 for 循环外写入 idx\_a（从技术角度来说，是在上一次迭代将近结束的位置）。  下面的示例生成 C3020。  
  
```  
// C3020b.cpp  
// compile with: /openmp /c  
float a[100][100];  
int idx_a, idx_b;  
void test(int first, int last)  
{  
   #pragma omp parallel for lastprivate(idx_a)  
   for (idx_a = first; idx_a <= last; ++idx_a) {  
      #pragma omp parallel for lastprivate(idx_a)   // C3020  
      for (idx_b = first; idx_b <= last; ++idx_b) {  
         a[idx_a][idx_b] += 1.0f;  
      }  
   }  
}  
```  
  
 下面的示例演示一个可能的解决方法：  
  
```  
// C3020c.cpp  
// compile with: /openmp /c  
float a[100][100];  
int idx_a, idx_b;  
void test(int first, int last)  
{  
   #pragma omp parallel for lastprivate(idx_a)  
   for (idx_a = first; idx_a <= last; ++idx_a) {  
      #pragma omp parallel for lastprivate(idx_b)  
      for (idx_b = first; idx_b <= last; ++idx_b) {  
         a[idx_a][idx_b] += 1.0f;  
      }  
   }  
}  
```