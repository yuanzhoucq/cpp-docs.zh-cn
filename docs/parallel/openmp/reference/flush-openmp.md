---
title: "flush (OpenMP) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Flush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "flush OpenMP directive"
ms.assetid: 150ca46e-d4f7-4423-b0a4-838df40aeb67
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# flush (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定所有线程的内存同一视图所有共享对象的。  
  
## 语法  
  
```  
#pragma omp flush [(var)]  
```  
  
## 备注  
 其中，  
  
 `var`（可选）  
 逗号分隔的对象表示要同步的列表变量。  如果 `var` 未指定，刷新所有内存。  
  
## 备注  
 **刷新** 指令不支持 OpenMP 子句。  
  
 有关更多信息，请参见 [2.6.5 flush Directive](../../../parallel/openmp/2-6-5-flush-directive.md)。  
  
## 示例  
  
```  
// omp_flush.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
void read(int *data) {  
   printf_s("read data\n");  
   *data = 1;  
}  
  
void process(int *data) {  
   printf_s("process data\n");  
   (*data)++;  
}  
  
int main() {  
   int data;  
   int flag;  
  
   flag = 0;  
  
   #pragma omp parallel sections num_threads(2)  
   {  
      #pragma omp section  
      {  
         printf_s("Thread %d: ", omp_get_thread_num( ));  
         read(&data);  
         #pragma omp flush(data)  
         flag = 1;  
         #pragma omp flush(flag)  
         // Do more work.  
      }  
  
      #pragma omp section   
      {  
         while (!flag) {  
            #pragma omp flush(flag)  
         }  
         #pragma omp flush(data)  
  
         printf_s("Thread %d: ", omp_get_thread_num( ));  
         process(&data);  
         printf_s("data = %d\n", data);  
      }  
   }  
}  
```  
  
  **线程 0:读取数据**  
**线程 1:处理数据**  
**数据 \= 2**   
## 请参阅  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)