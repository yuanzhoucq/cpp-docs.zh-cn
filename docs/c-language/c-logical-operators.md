---
title: "C 逻辑运算符 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "&& 运算符"
  - "|| 运算符"
  - "逻辑 AND 运算符"
  - "逻辑运算符, C"
  - "逻辑运算符, 表达式序列点"
  - "逻辑 OR 运算符"
  - "运算符 [C], 逻辑"
  - "短路计算"
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 逻辑运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

逻辑运算符执行逻辑与 （**&&**）和逻辑或\( `||` \)操作。  
  
 **语法**  
  
 *logical\-AND\-expression*：  
 *独占的”或“表达式*  
  
 *逻辑与表达式*  **&&** *逻辑或表达式*  
  
 *logical\-OR\-expression*：  
 *逻辑与表达式*  
  
 *逻辑或表达式*  **&#124;&#124;**  *逻辑与表达式*  
  
 逻辑运算符不执行常见的算术转换。  相反，根据其等效性为 0 计算每个操作数。  逻辑运算符的结果不是 0 就是 1。  结果的类型为 `int`。  
  
 C 逻辑运算符如下所述:  
  
|运算符|描述|  
|---------|--------|  
|**&&**|逻辑与运算符生产值 1 （如果两个操作数具有非零值）。  如果其中一个操作数等于 0，则结果是 0。  如果逻辑与运算的第一个操作数等于 0，则第二个操作数不会计算。|  
|`&#124;&#124;`|逻辑或运算符对其操作数执行“与或”运算。  如果操作时都有 0 值，结果将会 0。  如果其中一个操作数具有非零值，则结果是 1。  如果逻辑 OR 运算的第一个操作数非零值，则第二个操作数不会计算。|  
  
 逻辑与和逻辑或表达式的操作数从左到右进行计算。  如果第一个操作数的值足以确定操作的结果，第二个操作数不计算。  这被称作为“短路计算”。第一个操作数后有一个序列点。  有关更多信息，请参见[序列点](../c-language/c-sequence-points.md)。  
  
## 示例  
 下面的示例演示了本地运算符：  
  
```  
int w, x, y, z;  
  
if ( x < y && y < z )  
    printf( "x is less than z\n" );  
```  
  
 在此示例中，如果 `x` 比 `y` 小于，并 `y` 比 `z`更少，`printf` 函数调用打印消息。  如果 `x` 大于 `y`，则不会计算第二个操作数 \(`y < z`\) 且不会输出任何数据。  请注意这会导致出现问题，在第二个操作数依赖某些其他原因有副作用的情况下。  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 在此示例中，如果 `x` 与 `w`、`y` 或 `z` 相等，则为 `printf` 函数的第二个参数的计算为 true，值 1 打印。  否则，它计算结果为 false，打印数值 0。  只要其中的一个条件的计算结果为 true，计算停止。  
  
## 请参阅  
 [逻辑与运算符：&&](../cpp/logical-and-operator-amp-amp.md)   
 [逻辑或运算符：&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)