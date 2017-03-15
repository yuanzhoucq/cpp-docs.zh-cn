---
title: "2.7.1 threadprivate Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.1 threadprivate Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`threadprivate` 指令在 *变量中* 指定的命名文件大小、命名空间范围或静态块范围变量私有传递给线程。  *变量列表* 是逗号分隔的不包含不完整类型的列表变量。  `threadprivate` 指令的语法如下所示:  
  
```  
#pragma omp threadprivate(variable-list) new-line  
```  
  
 `threadprivate` 变量的每个副本初始化一次，在未指定点在程序在第一之前对该副本并以常规方式 \(即，，因为该主复制到过程中序列化的执行过程中初始化\)。  请注意，如果对象引用按 `threadprivate` 变量的显式初始值设定项和对象的值在第一之前修改引用要复制的变量，则该行为是未指定的。  
  
 与任何私有变量，线程无法引用 `threadprivate` 对象的另一个线程的副本。  在序列化区域以及程序执行期间的主区域，引用是对对象的主线程的副本。  
  
 在第一个并行区域执行后，在 `threadprivate` 对象的数据确保仍然存在，仅当动态线程结构已被禁用，并且，如果线程数。所有并行区域不变。  
  
 为 `threadprivate` 指令的限制如下所示:  
  
-   文件的大小或命名空间范围变量的一个 `threadprivate` 指令必须在所有定义或声明外部出现，并且必须在词法上排在所有对任何在其变量列表。  
  
-   每个变量在 `threadprivate` 指令的 *变量列表* 在文件或命名空间范围必须是指一个变量声明在词法指令前面的文件或命名空间范围。  
  
-   静态块范围变量的一个 `threadprivate` 指令必须出现在变量的范围内和不适用于嵌套的大小。  指令必须在词法上排在所有对任何在其变量列表。  
  
-   每个变量在 `threadprivate` 指令的 *变量列表* 块范围必须引用在词法指令前面的同一范围的变量声明。  变量声明必须使用这种静态的存储类说明符。  
  
-   如果变量在一个翻译单元的一个 `threadprivate` 指令指定，在声明它的每个翻译单元的一个 `threadprivate` 指令必须指定。  
  
-   `threadprivate` 变量不能出现除 `copyin`、 `copyprivate`、 `schedule`、 `num_threads`或 **如果** 子句的任何子句。  
  
-   `threadprivate` 变量的地址不是地址常数。  
  
-   `threadprivate` 变量不能包含不完整类型或引用类型。  
  
-   ，则声明使用显式初始值设定项，与非 POD 类类型的一个 `threadprivate` 变量必须有一个可访问，明确的复制构造函数。  
  
 下面的示例演示修改出现在本过程中的变量如何产生未指定的行为，使用一个从属对象和复制构造函数，以及如何避免此问题。  
  
```  
int x = 1;  
T a(x);  
const T b_aux(x); /* Capture value of x = 1 */  
T b(b_aux);  
#pragma omp threadprivate(a, b)  
  
void f(int n) {  
   x++;  
   #pragma omp parallel for  
   /* In each thread:  
   * Object a is constructed from x (with value 1 or 2?)  
   * Object b is copy-constructed from b_aux  
   */  
   for (int i=0; i<n; i++) {  
      g(a, b); /* Value of a is unspecified. */  
   }  
}  
```  
  
## 交叉引用:  
  
-   动态线程，请参见中的第 39 页的 [第3.1.7部分](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 。  
  
-   `OMP_DYNAMIC` 环境变量，请参见中的第 49 页的 [第4.3部分](../../parallel/openmp/4-3-omp-dynamic.md) 。