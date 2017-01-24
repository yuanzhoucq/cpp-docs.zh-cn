---
title: "2.7.2.6 reduction | Microsoft Docs"
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
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.6 reduction
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

该子句对显示 *变量列表*，与操作的运算符的标量变量降低。  `reduction` 子句的语法如下所示:  
  
```  
  
reduction(  
op  
:  
variable-list  
)  
  
```  
  
 减少为具有以下形式之一的语句通常指定:  
  
```  
  
        x     =  x     op     expr  
x     binop=  expr  
x     =  expr     op     x            (except for subtraction)  
x++  
++x  
x--  
--x  
```  
  
 其中：  
  
 *x*  
 在 `list`指定的某个缩减变量。  
  
 *变量列表*  
 逗号分隔的列表标量缩减变量。  
  
 *expr*  
 与不引用 *x.*的标量类型的表达式 *。*  
  
 `op`  
 不是重载运算符，还一 \+， \*， \)，  ， ^，&#124;，  或者&#124;&#124;.  
  
 `binop`  
 不是重载运算符，还一 \+， \*， \)，  或者， ^&#124;.  
  
 下面是 `reduction` 子句的示例:  
  
```  
#pragma omp parallel for reduction(+: a, y) reduction(||: am)  
for (i=0; i<n; i++) {  
   a += b[i];  
   y = sum(y, c[i]);  
   am = am || b[i] == c[i];  
}  
```  
  
 如示例中所示，运算符可能会隐藏函数调用。  运算符在 `reduction` 子句与指定减少操作的用户应谨慎。  
  
 虽然正确的操作数 &#124;&#124;运算符没有副作用在此示例中，它们允许，但是，应谨慎使用。  在此上下文中，确保不在循环的顺序执行期间发生的副作用可能在并行执行时发生。  ，因为迭代的执行顺序是不确定的，则此差别会发生此错误。  
  
 运算符用于减少用于确定编译器使用的所有私有变量的初始值并确定终止运算符。  指定运算符显式授予减少语句在构造之外的词法范围。  任意数量的子句 `reduction` 在指令可以指定，但是，变量可以出现在最指令的这一 `reduction` 子句。  
  
 每个变量的私有副本 *变量列表* 后，每个线程的，因此，就象使用了 `private` 子句。  该私有复制根据运算符初始化 \(请参见下表。\)  
  
 在 `reduction` 子句中指定的区域末端，更新原始对象反映合并其原始值的结果与每个的最终值专用副本使用运算符指定。  缩减运算符是任何关联的减号 \(除外\)，因此，编译器能随便重新关联曾最终值的计算。  \(减号减少的部分结果添加窗体最终值。\)  
  
 原始对象的值变为不确定，当第一个线程到达包含的子句并做时保持，直到减少计算完成。  通常，计算将完成时在构造结束时;但是，因此，如果 `reduction` 子句。 `nowait` 也适用的构造使用，原始对象的值保持不确定，直到障碍同步执行确保所有线程均已完成 `reduction` 子句。  
  
 下表列出了有效的运算符及其规范初始化值。  实际初始化值与降低变量的数据类型将是一致的。  
  
|运算符|初始化|  
|---------|---------|  
|\+|0|  
|\*|1|  
|\-|0|  
|&|~0|  
|&#124;|0|  
|^|0|  
|&&|1|  
|&#124;&#124;|0|  
  
 为 `reduction` 子句的限制如下所示:  
  
-   变量的类型。 `reduction` 子句中必须是有效的用于减少运算符，除指针类型和引用类型不允许的。  
  
-   在 `reduction` 子句中指定的变量不能为 \- 限定 **const**。  
  
-   在并行区域内是专用或显示 **并行** 指令的 `reduction` 子句的变量。 `reduction` 子句不能指定在绑定到并行构造的工作划分指令。  
  
    ```  
    #pragma omp parallel private(y)  
    { /* ERROR - private variable y cannot be specified  
                 in a reduction clause */  
       #pragma omp for reduction(+: y)  
       for (i=0; i<n; i++)  
          y += b[i];  
    }  
  
    /* ERROR - variable x cannot be specified in both  
               a shared and a reduction clause */  
    #pragma omp parallel for shared(x) reduction(+: x)  
    ```